# Entities

Entities, or entity classes, are pre-defined data models which could represent response of [MCS API][mcs-api], or part of it. We use these entities to communicate with MCS API server, either to upload data or to receive response.

We use [Gson][gson] to serialize / deserialize these objects, so you don't have to worry about using `object.getString("key")` and other trivial things. It's a handy library providing simple `toJson()` and `fromJson()` methods to convert Java objects to JSON and vice-versa

These entity classes are put under the `entity/` folder, and the class name are ended with `-Entity`.

### API Response

Note that classes under `api/` folder have a different format. They extended `ApiResults<T>`, and should be used in the following format:

```java
// use .getResults() to get the parsed api response as an Array
DeviceSummaryEntity[] summary = new Gson().fromJson(
    response.toString(), DeviceSummaryEntity.class)
    .getResults();
```

These classes are:

+ `DeviceSummaryEntity`
+ `DeviceInfoEntity`

Check [RequestApi - MCS SDK Android Guide](requestapi.md) for the mapping.


### Common Use Case

Also, an entity class may contain another entity classes, though it's not the direct format of API response.

They are used like this: 

```java
DataChannelEntity channelEntity = deviceInfo.getDataChannels().get(0);
```
Some use cases are listed below: 

+ `DataChannelEntity`
+ `DataPointEntity`



[mcs-api]: https://mcs.mediatek.com/resources/latest/api_references/
[gson]: https://github.com/google/gson