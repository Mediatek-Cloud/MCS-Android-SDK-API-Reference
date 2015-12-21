# Push Notifications

`McsPushInstallation` wraps [Google Cloud Messaging][gcm] to enable you to send push notifications to users' mobile devices.

If you have not installed the SDK, or you just want to make sure whether the setup is correct, check [Get Push Notification - MCS Android Tutorial][sdk-tutorial-notif].

## Requirement

The android device should have [google-play-services][google-play-services].

## Mechanism

```java
McsPushInstallation.getInstance().registerInBackground(
    "YOUR_GCM_SENDER_ID", "YOUR_GCM_API_KEY"
);
```

Inside `registerInBackground()`, we use your `GcmSenderId` and `GcmApiKey` to get a `registrationId` from GCM server. With this `registrationId`, we then register this mobile device to MCS Server. You should be able to see `Register mobile succeeded.` or `Update mobile succeeded.` in logcat.

The parameters of `registerInBackground()` are listed below:

| Parameter | Usage | Description |
| -- | -- | -- | -- |
| gcmSenderId | Required, `String` | The sender id of your GCM project. |
| gcmApiKey | Required, `String` | The api key of your GCM project. |
| successListener | Optional, `McsResponse.SuccessListener` | The handler to define what to do after registered mobile. |
| errorListener | Optional, `McsResponse.ErrorListener` | The handler to define what to do after register mobile failed. Default error message shows in log. |


## Customization


### Push Callback

In your `Application` class, after you have initialize MCS Android SDK, you could setup the activity to be open when user click on the notification.

```
public class YourApplication extends Application {
  @Override public void onCreate() {
    // Add these lines in your extended Application class
    Mcs.initialize(this, "YOUR_APP_KEY", "YOUR_APP_SECRET");
    
    // install push service
    McsPushInstallation.getInstance().registerInBackground(
        "YOUR_GCM_SENDER_ID", "YOUR_GCM_API_KEY"
    );

    /**
     * Optional: Specify an Activity to handle all pushes by default.
     * default is null
     */
    PushService.setDefaultPushCallback(MainActivity.class);
  }
}
```

#### Icon

In your `AndroidManifest.xml`, put the code below inside the `<application>` tag and replace `@mipmap/ic_launcher` with your own icon resource.

```java
<!-- in your AndroidManifest.xml -->

<application>

    // ...

    <meta-data
        android:name="com.mediatek.mcs.push.notification_icon"
        android:resource="@mipmap/ic_launcher"
        />
```

## Proguard

To remove the compile warning caused by gcm, add the following lines to your project’s `proguard.cfg` file:

```
-dontwarn com.google.android.gms.internal.**
```


[gcm]: https://developers.google.com/cloud-messaging/
[sdk-tutorial-notif]: https://mtk-mcs.gitbooks.io/mcs-android-sdk-tutorial/content/get_push_notification.html
[google-play-services]: https://developers.google.com/android/guides/overview