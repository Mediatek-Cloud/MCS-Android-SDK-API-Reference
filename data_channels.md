# Data Channels

![[key concept][key-concept]][img-prototype]

**It's strongly recommended to read [Key Concept][mcs-key-concept] before you started.** Each device has at least 1 data channel, and data channels can vary from each other. Different data channel contains different type of data point. 
Because [data channel format][mcs-api] is complex, we provide `McsDataChannel` for your ease to use.

## `McsDataChannel`

| Property | Type | Description |
| -- | -- | -- |
| deviceId | `String` | DeviceId of this data channel. Use `getDeviceId()` to get it. |
| deviceKey | `String` | DeviceKey of this data channel. Use `getDeviceKey()` to get it. |
| dataChannelEntity | `DataChannelEntity` | The `DataChannelEntity` of this data channel. Use `getDataChannelEntity()` to get it. |
| socketListener | `McsSocketListener` | The `SocketListener` of this data channel. Default listener would show the message of socket update in log. |

Note that `McsDataChannel` contains `DataChannelEntity`. `DataChannelEntity` is only an entity / data model that describes the format of response. `McsDataChannel` is a wrapper of `DataChannelEntity` with extra funcitons: 

+ [Web Socket][sdk-tutorial-socket]
+ [Event Emit][sdk-tutorial-event]

### Instantiate

To create an `McsDataChannel`, use:

```java
new McsDataChannel(deviceInfo, channelEntity, socketListener);
```

| Parameter | Usage | Description |
| -- | -- | -- |
| deviceInfo | Required, `DeviceInfoEntity` | The `DeviceInfoEntity` of this data channel. |
| channelEntity | Required, `DataChannelEntity` | The `DataChannelEntity` of this data channel. |
| socketListener | Optional, `McsSocketListener` | The `SocketListener` of this data channel. Default listener would show the message of socket update in log. |

With `McsDataChannel`, you don't have to worry about the format of data channel when you want to parse or upload the data point.

Still, if you want to submit data point, you should know the `Values` that keep inside the data point.

```java
mDataChannel.submitDataPoint(new DataPointEntity.Values(data));
```

Check [Data Points - MCS SDK Android Guide](data_points.md) to know how to put correct `Values` into the data point.

[mcs-api]: https://mcs.mediatek.com/resources/latest/api_references/
[mcs-key-concept]: https://mcs.mediatek.com/resources/latest/key_concept/
[sdk-tutorial-socket]: https://mtk-mcs.gitbooks.io/mcs-sdk-android-tutorial-doc/content/web_socket.html
[sdk-tutorial-event]: https://mtk-mcs.gitbooks.io/mcs-sdk-android-tutorial-doc/content/event_emit.html

[img-prototype]: https://img.mediatek.com/1500/mtk.linkit/mcs-resources/en/2.8.5/Key_concept/img_keyconcept_01.png