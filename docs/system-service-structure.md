# System service structure

#### version 4.1.4.28

System Service si single .NET project `SystemServiceApp.csproj`. Layers are implementes at folders level:

- Domain
- Infrasrtucture
- Application


## Domain

### 

### Repositories



```
public interface IAnalyticsCheckRepository
{
    string Name { get; set; }
    Task<Result<IEnumerable<AnalyticsRecord>>> GetAnalyticsRecordHistory(int last);
    Task<Result> SaveAnalyticsRecord(AnalyticsRecord record);
}
```

```
public interface ILicenseRepository
{
    Task<Result> SaveLicenseKey(string sourceKey,string licenseKey);
    Task<IEnumerable<ServiceLicenseDao?>> GetAll();
    Task GenerateTable();
}
```

```
public interface IServiceAnalyticsRepository
{
	Result<IEnumerable<ServiceAnalytics>> GetAll();
	Result<ServiceAnalytics> GetById(ServiceAddressEndPoint id);
	Result CreateOrUpdateServiceAnalytics(ServiceAnalytics serviceAnalytics);
}
```

```
public interface IServiceRegistryRepository : IReadOnlyServiceRegistryRepository
{
    Task<Result<IEnumerable<ServiceRegistryCollection>>> GetAllFromDatabase(CancellationToken token = default);
    Task<Result<ServiceRegistryCollection>> GetByServiceName(string id, CancellationToken token = default);
    Task<Result> Update(ServiceRegistryCollection service, CancellationToken token = default);
    Task<Result> Save(ServiceRegistryCollection service, CancellationToken ct = default);
    Task<Result> DeleteByUri(string uri, CancellationToken ct = default);
    Task<Result> DeleteById(string id, CancellationToken ct = default);
}
```

```
public interface ISettingsRepository
{
    IReadOnlyList<SettingsDao> GetAll();
    Result<SettingsDao> GetByKey(string key);
    Task<Result<SettingsDao>> UpsertAsync(string key, string? value, CancellationToken token);
    Task<Result> DeleteAsync(string key, CancellationToken token);
    Task<Result> Initialize(IConfiguration configuration);
}
```


## Infrastructure




## Application