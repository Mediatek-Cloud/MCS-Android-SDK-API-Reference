# Data Points

Data channels contain their own data points. There two kinds of model to interact with MCS API:

+ Download: `DataPointEntity`
+ Upload: `DataPointsUploadEntity`

They are a little bit different, but we have wrapped it so you only need to provide the `Values` like this

```
mDataChannel.submitDataPoint(new DataPointEntity.Values(data));

```

whenever you want to upload data points, and the SDK will take care of the format.

## `Values`

Currently, there are 3 kinds of `Values` 

- `Values(String value)`
- `Values(String value, String period)`
- `Values(McsGeoPoint geoPoint)`

According to [Data Channel Format - API References][mcs-api], every data channel has its own type of data point. It's necessary to put `Values` in the right format to submit data points successfully.


### Value

Provide `Values(String value)` for the following data channel type:

+ `String`
+ `Hex`: hexadecimal value of A-D and 0-9
+ `Integer`
+ `Float`
+ `Switch`: 0 stands for OFF, and 1 stands for ON.
+ `Gpio`: 0 stands for Low, and 1 stands for High.
+ `Category`: key value

### Value and Period

Provide `Values(String value, String period)` for the following data channel type:

+ `Pwm`: The range of Period and Value is from 0 to 1000.


### McsGeoPoint

Provide `Values(McsGeoPoint geoPoint)` for the following data channel type:

+ `Gps`: check the range limitation at [API References][mcs-api]

To create an `McsGeoPoint`, use

```
new McsGeoPoint(String latitude, String longitude, String altitude);
```


## Data Point Validation

### `DataPointFormatter`

We use `DataPointFormatter` to format the `Values` you provide. This is automatically done when you call `McsDataChannel.submitDataPoint(values)`. Only the valid data point would trigger the request to upload your data point. Some rules to format value are like

+ Remove the leading zeroes of `Integer` and `Float`
+ Trim each dimension of `McsGeoPoint` to 6 decimal places (`"#.######"`) if present with `RoundingMode.HALF_EVEN`.


### Exception

For the above parameters of `Values`, you could simply provide `String` to let us validate the value and do the transformation. `InvalidDataPointException` would be thrown if there is any error in the value you provide.



[mcs-api]: https://mcs.mediatek.com/resources/latest/api_references/