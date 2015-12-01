# Push Notifications

`McsPushInstallation` wraps [Google Cloud Messaging][gcm] to enable you to send push notifications to users' mobile devices.

If you have not installed the SDK, or you just want to make sure whether the setup is correct, check [MCS Android Tutorial Doc - Get Push Notification][sdk-tutorial-notif].




## Customization


### Push Callback

In your `Application` class, after you have initialize MCS Android SDK, you could setup the activity to be open when user click on the notificaion.

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
[sdk-tutorial-notif]: https://mtk-mcs.gitbooks.io/mcs-sdk-android-tutorial-doc/content/get_push_notification.html