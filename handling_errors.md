# Handling Errors

List different types of  `McsException` below alphabetically.

| Exception                 | Description               | 
| ------------------------- | ------------------------- |
| InvalidDataPointException | The data point submitted is in invalid format. | 
| InvalidSessionException   | Request sent to MCS API server is invalid. User not signed in, token expired, etc. | 
| McsNetworkException       | Any kind of network exception. Wifi not connected, server not responding, etc. | 
| SdkInstallationException | SDK configuration error. |
