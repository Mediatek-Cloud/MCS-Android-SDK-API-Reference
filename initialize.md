# Initialize

To setup SDK, we asked you to initialize the MCS SDK like this:

```java
Mcs.initialize(this, "YOUR_APP_ID", "YOUR_APP_SECRET");
```

Upon [API references of MCS API server][mcs-api], we need `AppId` and `AppSecret` be put in the HTTPS header to send authorized requests.


## Debug Information

Also, you can choosed whether to have debug information to show in log console. It's recommended to turn off debug information in production release. For your convenience, the debug info is **ON as default**.

You could specify it when initialize

```java
// default is true, if not specified.
Mcs.initialize(this, "YOUR_APP_ID", "YOUR_APP_SECRET", true);
```

or do it later:

```java
// It's recommended to turn off debug information in production release
// You could use build variants to make it simple
Mcs.setDebuggable(BuildConfig.DEBUG);
```

## Push Notification [Optional]

If you want to enable the feature to send push notification to the registered mobile, please check [Get Push Notification - MCS Android SDK Tutorial][sdk-tutorial-push] for detailed information.


[mcs-api]: https://mcs.mediatek.com/resources/latest/api_references/
[sdk-tutorial-push]: https://mtk-mcs.gitbooks.io/mcs-android-sdk-tutorial/content/get_push_notification.html