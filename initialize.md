# Initialize

To setup SDK, we asked you to initialize the MCS SDK like this:

```java
Mcs.initialize(this, "YOUR_APP_KEY", "YOUR_APP_SECRET");
```

Upon [API references of MCS API server](https://mcs.mediatek.com/resources/latest/api_references/), we need `appKey` and `appSecret` to request user's token. Without correct info, you will not be able to sign in.


## Debug Information

Also, you can choosed whether to have debug information to show in log console. It's recommended to turn off debug information in production release. For your convenience, the debug info is **ON as default**.

You could specify it when initialize

```java
// default is true, if not specified.
Mcs.initialize(this, "YOUR_APP_KEY", "YOUR_APP_SECRET", true);
```

or do it later:

```java
// It's recommended to turn off debug information in production release
// You could use build variants to make it simple
Mcs.setDebuggable(BuildConfig.DEBUG);
```



