# Entities

Entities are pre-defined data models which could represent response of [MCS API](https://mcs.mediatek.com/resources/latest/api_references/).



McsEntity 是一系列定義了 MCS Server API 上傳/回傳格式的 class，並且可以透過 gson 來 serialize / deserialize ，從 McsRequest 的 successListener 回來的是 JSONObject, 您可以透過這些 Entity 來輕鬆地 parse 成可用的 class, 並且有對應的 function, 而不需要處理 object.getString("")的問題


Provide simple toJson() and fromJson() methods to convert Java objects to JSON and vice-versa


* Api Response

DeviceSummaryEntity
DeviceDetailEntity
DataChannelEntity
DataPointEntity (Values)



### RequestApi <-> Entities



### Others

有使用到，但已封裝起來的
- AuthEntity
- McsUserEntity
- McsUserInfoEntity
- McsMobileEntity
- RegisterMobileEntity
- DataPointsUploadEntity (只有需要完全客製 upload body 的人需要, e.g. HistoricalMap)


Extended: ApiResults<T>





`entity/`

`api/`


```java
DeviceSummaryEntity[] summary = new Gson().fromJson(
    response.toString(), DeviceSummaryEntity.class).getResults();
```

