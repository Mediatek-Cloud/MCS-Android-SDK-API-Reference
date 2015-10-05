# Handling Errors

List different types of  `McsException` below alphabetically.

| Exception | Description | Suggestion |
| -- | -- |
| InvalidDataPointException | The data point submitted is in invalid format. | Check if you provide correct `Values` for your data channel. |
| InvalidSessionException | Request sent to MCS API server is invalid. User not signed in, token expired, etc. | Check if your sign in info, like email or password, is correct.
| McsNetworkException | Any kind of network exception. Wifi not connected, server not responding, etc. | Check detailed desciprtion in log. |
| SdkInstallationException | SDK configuration error. | Check you initialize SDK with correct `appKey`, `appSecret`. Also, if you enable `McsPushInstallation`, check related setup. |
