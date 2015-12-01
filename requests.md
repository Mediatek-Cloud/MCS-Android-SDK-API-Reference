# Requests

This session demonstrate how to interact with MCS API Server.

## Send a Request

If you are familiar with [Volley][volley], the open source network request library created by Google, hooray! It's almost the same to manipulate MCS SDK. 

```java
// Default method is GET 
int method = McsJsonRequest.Method.GET;
String url = RequestApi.GET_DEVICE_LIST;
McsResponse.SuccessListener<JSONObject> successListener =
    new McsResponse.SuccessListener<JSONObject>() {
      @Override public void onSuccess(JSONObject response) {
        DeviceSummaryEntity[] summary = new Gson().fromJson(
            response.toString(), DeviceSummaryEntity.class).getResults();
            
        // ...
      }
};

/**
 * Optional.
 * Default error message shows in log.
 */
McsResponse.ErrorListener errorListener = new McsResponse.ErrorListener() {
  @Override public void onError(Exception e) {
    // network request failed
  }
};

McsJsonRequest request = new McsJsonRequest(method, url, successListener, errorListener);
RequestManager.sendInBackground(request);
```

### `RequestManager` and `McsJsonRequest`

We use `RequestManager` singleton to send `McsJsonRequest` to MCS API server. To create any `McsJsonRequest`, provide the following as parameters:

| Name | Usage | Description |
| -- | -- | -- |
| method | Optional, `int` | The method of request. Default is `GET`. |
| url | Required, `String` | The url of request |
| headers | Optional, `HashMap<String, String>` | The headers of request. Always default with key `Content-Type: application/json`, `AppId: YOUR_APP_ID` and `AppSecret: YOUR_APP_SECRET`. |
| body | Optional, `String` | The body of request. |
| successListener | Required, `McsResponse.SuccessListener` | The handler to define what to do after request succeed. |
| errorListener | Optional, `McsResponse.ErrorListener` | The handler to define what to do after request failed. Default error message shows in log. |


#### Method of Request

Use `McsJsonRequest.Method` to specify the method of your HTTP request:

- `McsJsonReqeust.Method.GET`
- `McsJsonReqeust.Method.POST`
- `McsJsonReqeust.Method.PUT`
- `McsJsonReqeust.Method.DELETE`


## `McsResponse`

The response of `McsRequest` is separated into 2 parts: success and error.

Inside the code block of `onSuccess()` and `onError()`, it runs on main thread.


### `SuccessListener` - Required

The handler to define what to do after request succeeded.

```
new McsResponse.SuccessListener<JSONObject>() {
    @Override public void onSuccess(JSONObject response) {
        // Request Succeeded, back to UI thread
    }
}
```

### `ErrorListener` - Optional

The handler to define what to do after request failed. Default error message shows in log. Check [Handling Errors](handling_errors.md) for detailed exception type.

```
new McsResponse.ErrorListener() {
    @Override public void onError(Exception e) {
        // Request failed, back to UI thread
    }
}
```

### Response and Entities 

Every success response of `McsJsonRequest` is of type `JSONObject`. We have provided a set of entities to simplify the serialization and deserialization of these network requests.

With [Gson][gson], you can get the object by specifing the correct class: 

```java
DeviceSummaryEntity[] summary = new Gson().fromJson(
    response.toString(), DeviceSummaryEntity.class).getResults();
```

Check [Entities - Mcs Android Guide](entities.md) for detailed explaination.



[volley]: https://android.googlesource.com/platform/frameworks/volley/
[gson]: https://github.com/google/gson