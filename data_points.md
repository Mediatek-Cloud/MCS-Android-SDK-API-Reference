# Data Points


上傳: DataPointsUploadEntity

下載 (response): DataPointEntity

## Values



- `Values(String value)`
- `Values(String value, String period)`
- `Values(McsGeoPoint geoPoint)`


原生: DataPointsUploadEntity

這邊已經封裝起來了，並且會使用 DataPointFormatter (預設) 做一些 default formatting (e.g. 數字開頭去0, GeoPoint 會取至小數點下第 6 位)



### Value

+ `String`
+ `Hex`
+ `Integer`
+ `Float`

### Value and Period

+ `Pwm`
+ `PwmSlider`


### McsGeoPoint

`float latitude, float longitude, float altitude`

public McsGeoPoint(String latitudeString, String longitudeString, String altitude) {


You could simply provide `String` to let us validate the value and do the transformation. `InvalidDataPointException` would be thrown if there is error in the value you provide.