# Background Jobs

## Description

Background jobs in services are implemented as infinite loops with ability to stop the cycle by switching `CancellationToken`. We are trying to get rid of previous implementqtion of this type of jobs via `Quartz` library - so, step-by-step refactoring them to more simple and direct approach.

## Basic Interfaces and Abstractions (in `SharedLibrary.Infrastructure.Services.PeriodicJobs`)

### Interface `ILoopJob`

```
public interface ILoopJob
{
    string Name { get; }
    Task JobExecuteAsync(CancellationToken ct);
}
```

### Interface `ILoopJobOptions`

```
public interface ILoopJobOptions
{
    int IntervalInSeconds { get; set; }           // how often to run
    int InitialDelayInSeconds { get; set; }       // first delay before starting
    bool SkipIfRunning { get; set; }              // true = skip overlapping executions

}
```

### Starting and managing the job with Hosted Service

Starting and managing everu single job is implemented with generic type service, implementing 'IHostedService'. Base class for this service also lives in `SharedLibrary.Infrastructure.Services.PeriodicJobs`:

```
public sealed class LoopHostedService<TJob, TOptions> : IHostedService, IDisposable
    where TJob : class, ILoopJob
    where TOptions : class, ILoopJobOptions, new()
```

This class already handle starting job, initial delay, execution with defined interval, guarding of job overlap (next tick will be skipped if current job is still in progress), cancelling job.

### Helper for regestring Job during building of application

```
public static IServiceCollection AddLoopJob<TJob, TOptions>(
    this IServiceCollection services,
    IConfiguration config,
    string? sectionName = null) where TJob : class, ILoopJob
                                where TOptions : class, ILoopJobOptions, new()
```

This method register Job as Singleton and add corresponding HostedService for Job Management.

## Example of implementation

#### Section in `appsettings.json`

```
 "PcKeepAliveJob": {
     "IntervalInSeconds": 10,
     "InitialDelayInSeconds": 600,
     "SkipIfRunning": true,
     "ChangeStateTimeInMinutes": 15
 },
```

#### Options Model class (supports DataAnnotations):

```
public sealed class PcKeepAliveJobOptions : ILoopJobOptions
{
    [Range(1, int.MaxValue)]
    public int IntervalInSeconds { get; set; } = 10;

    [Range(0, int.MaxValue)]
    public int InitialDelayInSeconds { get; set; } = 0;

    public bool SkipIfRunning { get; set; } = true;

// Here you can add additional options specific to certain job

    public int ChangeStateTimeInMinutes { get; set; } = 5;
}
```

#### Properties & Ctor

```
public sealed class PcKeepAliveJob : ILoopJob
{
    private readonly ILogger<PcKeepAliveJob> _logger;
    private readonly IKeepAliveRepository _keepAliveRepository;
    private readonly IComputerRepository _pcRepository;
    private readonly PcKeepAliveJobOptions _options;

    public string Name => nameof(PcKeepAliveJob);

    public PcKeepAliveJob(
        ILogger<PcKeepAliveJob> logger,
        IKeepAliveRepository keepAliveRepository,
        IComputerRepository pcRepository,
        IOptions<PcKeepAliveJobOptions> options)
    {
        _logger = logger;
        _keepAliveRepository = keepAliveRepository;
        _pcRepository = pcRepository;
        _options = options.Value;
    }
```

#### Main Job Method

```
public async Task JobExecuteAsync(CancellationToken token)
{
    try
    {
        var pcs = _pcRepository.GetAll();
        foreach (var pc in pcs)
        {
            var keepAliveDto = _keepAliveRepository.GetById(pc.ComputerMac);
            if (keepAliveDto.IsFailed)
            {
                _logger.LogDebug("Failed to get KeepAliveDto for PC with MAC={UserId}", pc.ComputerMac);
                if(pc.Online)
                {
                    await DeclarePcAsOffline(pc);
                }
                continue;
            }

            if ((DateTime.UtcNow - keepAliveDto.Value.LastKeepAlive).TotalMinutes < _options.ChangeStateTimeInMinutes)
            {
                continue;
            }

            if (pc.Online && (DateTime.UtcNow - keepAliveDto.Value.LastKeepAlive).TotalMinutes > _options.ChangeStateTimeInMinutes)
            {
                await DeclarePcAsOffline(pc);
            }
        }
        _logger.LogTrace("{job}: Lookup for KeepAlives from Pcs completed", Name);
    }
    catch (Exception ex)
    {
        _logger.LogError(ex, "{this} failed during PcKeepAlive Lookup. Errors: {message}", Name, ex.Message);
    }
}
```

#### Internal helper

```
    private async Task DeclarePcAsOffline(PcControlDao pc)
    {
        _logger.LogDebug("{this} Declaring PC with MAC={pcMac} as offline", Name, pc.ComputerMac);
        pc.Online = false;
        pc.OfflineStartTime = DateTime.UtcNow;
        var updatePC = await _pcRepository.UpsertObject(pc);
        if (updatePC.IsFailed)
        {
            _logger.LogError("{this} failed update PC with MAC={pcMac} to offline status. error(s) - '{errors}'", Name, pc.ComputerMac, updatePC.ErrorsToString());
        }
    }
}
```

#### Job Registration in `Program.cs` (includes adding HostedService)

```
services.AddLoopJob<PcKeepAliveJob, PcKeepAliveJobOptions>(configuration, sectionName: nameof(PcKeepAliveJob));
```

## List of Jobs implemented already with this pattern in different services

-   BulkJobCleanup (AdminProvisioning Service)
-   PcDeleteJob (Login Service)
-   PcKeepAliveJob (Login Service)
-   TokenCleanupJob (Login Service)
