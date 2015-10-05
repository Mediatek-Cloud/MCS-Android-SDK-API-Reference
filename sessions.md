# Sessions

`McsSession` is a singleton that will keep alive during the life time of your program. `McsSession` provides everything you need about authentication. 

## Sign In

Use `McsSession.getInstance().requestSignIn()` to sign user in. 

```java
// call in main thread
McsSession.getInstance().requestSignIn(email, pwd, 
    new McsResponse.SuccessListener<JSONObject>() {
        @Override public void onSuccess(JSONObject response) {
            // Signed in, back to UI thread
        }
    },
    /**
     * Optional.
     * Default error message shows in log.
     */
    new McsResponse.ErrorListener() {
        @Override public void onError(Exception e) {
            // Sign in failed, back to UI thread
        }
    }
);
```

| Parameter | Usage | Description |
| -- | -- | -- | -- |
| email | Required, `String` | The email of the user. |
| password | Required, `String` | The password of the user. |
| successListener | Required, `McsResponse.SuccessListener` | The handler to define what to do after signed in. |
| errorListener | Optional, `McsResponse.ErrorListener` | The handler to define what to do after sign in failed. Default error message shows in log. |

Note that `requestSignIn()` will work in background network thread.

## Sign Out

It's even easier to sign out. 

```java
// call in main thread
McsSession.getInstance().requestSignOut(
    new McsResponse.SuccessListener<JSONObject>() {
      @Override public void onSuccess(JSONObject response) {
        // Signed out, back to UI thread
    }
);
```

| Parameter | Usage | Description |
| -- | -- | -- |
| successListener | Required, `McsResponse.SuccessListener` | The handler to define what to do after signed out. |

## Get Access Token

`McsRequest` automatically handles the trivial token issue for you, so you don't have to worry about access token and refresh token.

After signed in, you can use `McsUser.getInstance().getAccessToken()` to 
get access token to access the [MCS APIs][mcs-api] from your own third party service. Also, `McsSession.getInstance().getAccessToken()` could get the same access token for your ease of use to reduce the dependency of modules.


## Get User and Mobile Info

Once signed in, the following information would be prepared.

- `McsUser.getInstance()`
- `McsUserInfo.getInstance()`
- `McsMobile.getInstance()`

These information will be keep in the internal storage of Android application using `SharedPreferences`.

### McsUser

| Property | Type | Description |
| -- | -- | -- |
| email | `String` | The email account of user. |
| password | `String` | The password of user. |
| token | `String` | The token used to refresh again to get valid accesToken. |
| accessToken | `String` | The token used to make valid API calls. |
| isRememberMe | `boolean` | The value whether user choose to remember the information for sign in. |

### McsUserInfo

| Property | Type | Description |
| -- | -- | -- |
| userImageURL | `String` | The profile image url of user. |
| nickname | `String` | The nickname of user. |

### McsMobile


| Property | Type | Description |
| -- | -- | -- |
| mobileId | `String` | The mobileId of this mobile device, provided by MCS API server. This property exists only when you successfully register this mobile by `McsPushInstallation` |



[mcs-api]: https://mcs.mediatek.com/resources/latest/api_references/