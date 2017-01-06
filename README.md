Adcash MoPub Mediation Adapter is designed to integrate Adcash SDK with MoPub Mediation to maximize your App fill rate and revenue.  

It's a simple 2-step integration process.

## Integration Guide

> Assuming integration is already done with MoPub SDK, if not please follow [MoPub Integration guideline](https://github.com/mopub/mopub-android-sdk/wiki/Getting-Started).  

### 1. Integrate Adcash SDK

* **ZONE ID(s)**. You create at [Adcash website](https://www.adcash.com/console/scripts.php).
* Android Studio 1.0 or higher. Instructions to [install Android Studio](https://developer.android.com/studio/install.html).
* Android API level 9 or higher

#### 1. Add Dependencies

##### JCenter repository

Add **JCenter** repository if you havn't added it yet. Adcash SDK also requires **Google Play Services** and **Android Support Library v4** 
In your project base `build.gradle` file add:

```groovy
repositories {
    jcenter()
}

dependencies {
    // Integrate Adcash SDK:
    compile 'com.adcash:adcash-mopub-adapter:2.2.2'

    // Required by Adcash SDK:
    compile 'com.android.support:support-v4:24.2.0'
    compile 'com.google.android.gms:play-services:9.4.0'
}
```
![alt tag](http://developer.adca.sh/wp-content/uploads/2016/09/AndroidSDK-MoPub-Adapter-Gradle-Script.png)
##### Local library file
If you prefer to use local file instead of Jcenter repository, you can also do it.  

First, download the [MoPub adapter](https://github.com/adcash/Adcash-MoPub-Adapter-Android/archive/master.zip). Then create a `libs` folder (if you do not already have one) in your project (Example: ... MyApplication/app/libs/) then add the previously downloaded .AAR file
Open the build.gradle of your app and add the following code lines:

```groovy
repositories {
    flatDir {
       dirs 'libs'
    }
}

dependencies {
    // Integrate Adcash SDK:
    compile(name: 'adcash-mopub-adapter', ext: 'aar')

    // Required by Adcash SDK:
    compile 'com.android.support:support-v4:24.2.0'
    compile 'com.google.android.gms:play-services-ads:9.2.0'
}
```
![alt tag](http://developer.adca.sh/wp-content/uploads/2016/09/AndroidSDK-MoPub-Adapter-Gradle-Script-local.png)

  
Click **Sync Now** or request Gradle sync yourself if you have not been promoted automatically. Wait till Gradle finishes.

##### (Optional) Proguard settings

If you want to enable **Proguard** in your project, add following line to your  `proguard.cfg` file:

> -keep class com.adcash.mobileads.** { *; }

#### 2. Update Manifest

At this point you have added all necessary dependencies to your project and need small modifications to your module `AndroidManifest.xml` file to finish with the integration.

1. Add the following `<uses-permission>` tags: 
    * `INTERNET` - required to allow the Adcash SDK to make ad requests.
    * `ACCESS_NETWORK_STATE` - used to check the Network connection availability.  

```xml
    <uses-permission android:name="android.permission.INTERNET"/>
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
```


2. Add **AdcashActivity** for full screen ads to work (interstitial and rewarded video)  

```xml
    <activity
        android:name="com.adcash.mobileads.ui.AdcashActivity"
        android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize"
        android:hardwareAccelerated="true"
        android:theme="@android:style/Theme.Translucent" />
```
![alt tag](http://developer.adca.sh/wp-content/uploads/2016/09/AndroidSDK-MoPub-Adapter-Manifest-File.png)

### 2. Configure MoPub Custom Event on Mediation Portal

##### 2.1. Add a Network

On MoPub Dashboard, click on **Networks tab** then click on **Add a Network** button.
![alt tag](http://developer.adca.sh/wp-content/uploads/2016/09/ScreenShot2.png)

On the **Add a Network** page select **Custom Native Network** under **Additional Networks** section.
![alt tag](http://developer.adca.sh/wp-content/uploads/2016/09/ScreenShot3.png)

##### 2.2. Configure Custom Native Ad Network

Give it a title **Adcash**, then scroll down for ad units (Adcash MoPub Android Adapter currently supports Banner and Interstitial ad format)   

Custom Event Information:  
>	**Custom Event Class:**  
   	_For Banner:_ com.adcash.mobileads.mopubadapter.AdcashMoPubBanner  
	_For Interstitial:_ com.adcash.mobileads.mopubadapter.AdcashMoPubInterstitial 
        _For Rewarded Video:_ com.adcash.mobileads.mopubadapter.AdcashMoPubRewarded
>	**Custom Event Class Data:**  
>	Enter your Zone ID from Adcash Publisher Panel. It has to be in JSON format with parametr name "adZoneID"
>	Example: {"adZoneID": "your_zone_id"}   

![alt tag](http://developer.adca.sh/wp-content/uploads/2016/09/ScreenShot4.png)

## Release App
Now Adcash MoPub Mediation Adapter is successfully integrated with MoPub Mediation platform and you can release out the app in PlayStore. Please note changes made in MoPub Mediation Portal might take couple of hours to reflect.

## Support
If you need any help or assistance you can contact us by sending email to **mobile@adcash.com**