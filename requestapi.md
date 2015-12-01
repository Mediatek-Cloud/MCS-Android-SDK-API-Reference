## `RequestApi`

`RequestApi` class integrates some of the APIs of [API references][mcs-api]. 

* API Server domain prefix: `https://api.mediatek.com/mcs/v2`


| Constant Name | URL | Response Entity | Description |
| -- | -- | -- | -- |
| URL_QUERY_PAGING | `?page={page}&limit={limit}` |    | Postfix for url that has an array of data. E.g.: `"/devices" + URL_QUERY_PAGING`  |
| DEVICES | `/devices` | `DeviceSummaryEntity` | get device list with limit and paging |
| DEVICE | `/devices/{deviceId}` | `DeviceInfoEntity` | get device by deviceId |
| DATA_POINTS | `/devices/{deviceId}/datachannels/{datachannelId}/datapoints` | `List<DataPointEntity>` | get data points of certain data channel |
| UPLOAD_DATA_POINT | `/devices/{deviceId}/datapoints` | `DataPointsUploadEntity` |   Upload data point |



[mcs-api]: https://mcs.mediatek.com/resources/latest/api_references/