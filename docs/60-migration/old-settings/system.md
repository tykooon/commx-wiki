# System

## Global Settings

| Setting | OldDbKey | CurrentDbKey | Type | Default | Status | Description | Comments |
|---|---|---|---|---|---|---|---|
| AXL IP | CUCMIP | CUCMIP | string |  | active | Ip address of CUCM AXL interface | ... |
| Max Request Timeout | AXLMaxRequestTimeout | AXLMaxRequestTimeout | int | 100 | active | ... | ... |
| Server URL | ServerURL | ServerURL | string |  | active | ... | ... |
| ECCP | ECCPName | ECCPName | string |  | active | ... | ... |
| Primary Server URL | PrimaryServerURL | PrimaryServerURL | string |  | active | ... | ... |
| Backup Server URL | BackupServerURL | BackupServerURL | string |  | active | ... | ... |
| Backup Server IP | BackupServerIP | BackupServerIP | string |  | active | ... | ... |
| VoiceMail Number | VoiceMailNumber | VoiceMailNumber | string |  | active | ... | ... |
| Clear Upload Folder (min) | ClearUploadFolderTimer | ClearUploadFolderTimer | int | 2880 | active | ... | ... |
| Language | Language | Language | string | English | active | ... | Type changed to int (Enums) |
| Enable RIS | RISEnable | RISEnable | bool | false; | active | ... | ... |
| Disable JTAPI | JtapiDisableMode | JtapiDisableMode | bool | False | active | ... | ... |
| Disable XMPP | XmppDisableMode | XmppDisableMode | bool | True | active | ... | ... |
| Dev Mode | DevMode | DevMode | bool | False | active | ... | ... |
| DB Data | DBData | DBData | bool | False | active | ... | ... |
| User | DBUser | DBUser | string |  | active | ... | ... |
| Password | EncDBPass | EncDBPass | string |  | active | ... | Password stored as encrypted |
| Customer Name | CustomerName | CustomerName | string |  | active | ... | ... |
| Use User Principal | UseUserPrincipal | UseUserPrincipal | bool | False | active | ... | ... |

## CTI Managers

| Setting | OldDbKey | CurrentDbKey | Type | Default | Status | Description | Comments |
|---|---|---|---|---|---|---|---|
| First Cti Manager | CtiManagerIP | CtiManagerIP | string |  | active | ... | ... |
| Second Cti Manager | SecondCtiManagerIP | SecondCtiManagerIP | string |  | active | ... | ... |
| Third Cti Manager | ThirdCtiManagerIP | ThirdCtiManagerIP | string |  | active | ... | ... |
| Fourth Cti Manager | FourthCtiManagerIP | FourthCtiManagerIP | string |  | active | ... | ... |

## CTI/AXL User

| Setting | OldDbKey | CurrentDbKey | Type | Default | Status | Description | Comments |
|---|---|---|---|---|---|---|---|
| User | CUCMUser | CUCMUser | string |  | active | ... | ... |
| Backup CTI User | BackupCUCMUser | BackupCUCMUser | string |  | active | ... | ... |
| Password | CUCMEncPass | CUCMEncPass | string |  | active | ... | Encrypted. |

## Provisioning

| Setting | OldDbKey | CurrentDbKey | Type | Default | Status | Description | Comments |
|---|---|---|---|---|---|---|---|
| ECCP Profiles | ProfilesProv | ProfilesProv | bool | False | active | ... | ... |
| ECCP Phones | ProfilesProv | ProfilesProv | bool | False | active | ... | ... |
| ECCP Whitelist | WhiteLineProv | WhiteLineProv | bool | False | active | ... | ... |
| App User | AppProvisioning | AppProvisioning | bool | False | active | ... | ... |
| ECCP License | LicenseLineProv | LicenseLineProv | bool | False | active | ... | ... |
| Backup Server | BackupServer | BackupServer | bool | False | active | ... | ... |

## Stop Services Settings

| Setting | OldDbKey | CurrentDbKey | Type | Default | Status | Description | Comments |
|---|---|---|---|---|---|---|---|
| Stop UQS | StopUQSService | StopUQSService | bool | False | active | ... | ... |
| Stop UCW | StopUCWService | StopUCWService | bool | False | active | ... | ... |
| Stop UMS | StopUMSService | StopUMSService | bool | False | active | ... | ... |
| Stop URS | StopURSService | StopURSService | bool | False | active | ... | ... |

## CTI Ports

| Setting | OldDbKey | CurrentDbKey | Type | Default | Status | Description | Comments |
|---|---|---|---|---|---|---|---|
| UCW CTI Prefix Primary | Prefix_CTI_WC | Prefix_CTI_WC | string |  | active | ... | ... |
| UCW CTI Prefix Backup | Prefix_CTI_WC_Backup | Prefix_CTI_WC_Backup | string |  | active | ... | ... |
| Rec CTI Prefix Primary | Prefix_CTI_WC_Backup | Prefix_CTI_WC_Backup | string |  | active | ... | ... |
| Rec CTI Prefix Backup | Prefix_CTI_Rec_Backup | Prefix_CTI_Rec_Backup | string |  | active | ... | ... |
| UDS CTI Prefix | Prefix_CTI_UDS | Prefix_CTI_UDS | string |  | active | ... | ... |
| UDS CTI Prefix Backup | Prefix_CTI_UDS_Backup | Prefix_CTI_UDS_Backup | string |  | active | ... | ... |
| UQS CTI Prefix Primary | Prefix_CTI_UQS | Prefix_CTI_UQS | string |  | active | ... | ... |
| UQS CTI Prefix Backup | Prefix_CTI_UQS_Backup | Prefix_CTI_UQS_Backup | string |  | active | ... | ... |
| UMS Audio CTI Prefix Primary | Prefix_CTI_Audio_UMS | Prefix_CTI_Audio_UMS | string |  | active | ... | ... |
| UMS Audio CTI Prefix Backup | Prefix_CTI_Audio_UMS_Backup | Prefix_CTI_Audio_UMS_Backup | string |  | active | ... | ... |
| UMS Video CTI Prefix Primary | Prefix_CTI_Video_UMS | Prefix_CTI_Video_UMS | string |  | active | ... | ... |
| UMS Video CTI Prefix Backup | Prefix_CTI_Video_UMS_Backup | Prefix_CTI_Video_UMS_Backup | string |  | active | ... | ... |
| UMS Operator CTI Prefix Primary | Prefix_CTI_UMS_Operator | Prefix_CTI_UMS_Operator | string |  | active | ... | ... |
| UMS Operator CTI Prefix Backup | Prefix_CTI_UMS_Operator_Backup | Prefix_CTI_UMS_Operator_Backup | string |  | active | ... | ... |
| UCCX CTI Prefix | Prefix_CTI_UCCX | Prefix_CTI_UCCX | string |  | active | ... | ... |

## API Parameters

| Setting | OldDbKey | CurrentDbKey | Type | Default | Status | Description | Comments |
|---|---|---|---|---|---|---|---|
| API Username | APIUsername | APIUsername | string |  | active | ... | ... |
| API Password | APIPassword | APIPassword | string |  | active | ... | ... |

## SMTP Parameters

| Setting | OldDbKey | CurrentDbKey | Type | Default | Status | Description | Comments |
|---|---|---|---|---|---|---|---|
| SMTP Host | SMTPHost | SMTPHost | string |  | active | ... | ... |
| SMTP Port | SMTPPort | SMTPPort | int | 0 | active | ... | ... |
| Mail Sender | SMTPSender | SMTPSender | string |  | active | ... | ... |
| Mail Recipient | SMTPRecipient | SMTPRecipient | string |  | active | ... | ... |
| SMTP Username | SMTPUsername | SMTPUsername | string |  | active | ... | ... |
| SMTP Password | SMTPPassword | SMTPPassword | string |  | active | ... | Encrypted. |

## System Logs Parameters

| Setting | OldDbKey | CurrentDbKey | Type | Default | Status | Description | Comments |
|---|---|---|---|---|---|---|---|
| UAS CPU Usage > | UASCPU | UASCPU | int | 0 | active | ... | ... |
| UAS Memory Usage > | UASMemory | UASMemory | int | 0 | active | ... | ... |
| UAS Disk Usage > | UASDisk | UASDisk | int | 0 | active | ... | ... |
| Logger CPU Usage > | LoggerCPU | LoggerCPU | int | 0 | active | ... | ... |
| Logger Memory Usage > | LoggerMemory | LoggerMemory | int | 0 | active | ... | ... |
| Logger Disk Usage > | LoggerDisk | LoggerDisk | int | 0 | active | ... | ... |

## Translation Parameters

| Setting | OldDbKey | CurrentDbKey | Type | Default | Status | Description | Comments |
|---|---|---|---|---|---|---|---|
| Use Description Name | TRSNameEnable | TRSNameEnable | bool | False | active | ... | ... |

