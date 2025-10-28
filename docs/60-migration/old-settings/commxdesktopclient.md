# CommXDesktopClient

## SignalR Settings

| Setting | OldDbKey | CurrentDbKey | Type | Default | Status | Description | Comments |
|---|---|---|---|---|---|---|---|
| Start Server | startSignalRServer | StartSignalRServer | bool | False | active | ... | ... |
| Server Web Protocol | signalRWebProtocol | SignalRWebProtocol | string |  | active | ... | ... |
| Server Port on UAS | signalRServerPortOnUas | SignalRServerPortOnUas | int | 0 | active | ... | ... |
| Server Port on Client | signalRServerPortOnClient | SignalRServerPortOnClient | int | 0 | active | ... | ... |

## Client Configuration

| Setting | OldDbKey | CurrentDbKey | Type | Default | Status | Description | Comments |
|---|---|---|---|---|---|---|---|
| Authentication Method | commXClientDesktopRegistrationMethod | ClientAuthenticationMethod | int | 0 | active | ... | ... |
| SRTP Use | srtpUse | SrtpUse | string |  | active | ... | ... |
| Allow Sounds | AllowSoundsFromClient | AllowSoundsFromClient | bool | False | active | ... | ... |
| Display Windows Notifications | DisplayWindowsNotifications | DisplayWindowsNotifications | bool | False | active | ... | ... |
| Global Certificate Password | CommXClientCertificatePassword | CommXClientCertificatePassword | string |  | active | ... | Password stored as encrypted |
| SignalR Retries | signalRHaRetries | SignalRHaRetries | int | 0 | active | ... | ... |
| SignalR Timeouts | signalRHaTimeouts | SignalRHaTimeouts | int | 0 | active | ... | ... |
| CUCM Retries | CUCMHaRetries | CUCMHaRetries | int | 0 | active | ... | ... |
| CUCM Timeouts | CUCMHaTimeouts | CUCMHaTimeouts | int | 0 | active | ... | ... |
| Use H.264 for WebRTC | UseH264ForWebRTC | UseH264ForWebRTC | bool | False | active | ... | ... |
| SIP Dynamic Ports | SIPDynamicPorts | SIPDynamicPorts | bool | False | active | ... | ... |
| RTP Max Payload | RTPMaxPayload | RTPMaxPayload | int | 0 | active | ... | ... |
| Video CRF (1-51) | VideoConstanRateFactor | VideoCRF | int | 0 | active | ... | ... |
| Screen Share CRF (1-51) | ShareScreenConstanRateFactor | ShareScreenCRF | int | 0 | active | ... | ... |
| Use Rejected Event | UseRejectedEvent | UseRejectedEvent | bool | False | active | ... | ... |

## Manual Switch Servers

| Setting | OldDbKey | CurrentDbKey | Type | Default | Status | Description | Comments |
|---|---|---|---|---|---|---|---|
| Switch to Manual Servers | switchToManualCUCMServers | SwitchToManualCUCMServers | bool | False | active | ... | ... |
| Primary CUCM | manualPrimaryCUCMIP | ManualPrimaryCUCMIP | string |  | active | ... | ... |
| Backup CUCM | manualBackupCUCMIP | ManualBackupCUCMIP | string |  | active | ... | ... |
| Switch to Backup UAS | switchToBackupUAS | SwitchToBackupUAS | bool | False | active | ... | ... |
| Switch to Backup CUCM | switchToBackupCUCM | SwitchToBackupCUCM | bool | False | active | ... | ... |

## Chat Server Settings

| Setting | OldDbKey | CurrentDbKey | Type | Default | Status | Description | Comments |
|---|---|---|---|---|---|---|---|
| Zip Chat XMLs | zipChatXmls | ZipChatXmls | bool | False | active | ... | ... |

