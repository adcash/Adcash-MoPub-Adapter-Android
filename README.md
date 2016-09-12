# AdMob Mediation Android

This SDK is designed for integrating Adcash with AdMob Mediation on Android to maximize fill rate and revenue.  

It’s a simple 2-step integration process.

## Integration Guide

> Assuming integration is already done with AdMob SDK, if not please follow AdMob Integration guideline 

**Prerequisite:** Android Studio 1.0 or higher 

### Configure Adcash SDK
#### Download SDK
  Download the Adcash SDK [here](http://developer.adca.sh/wp-content/uploads/2016/09/admob-adapter.zip).
#### Update build.gradle
Add Adcash SDK into project by putting it in **'libs'** module.  If you don't have 'libs' folder in your project module then create one (Example: ... MyNewProject/app/libs/)

Open the build.gradle of your app and add the following code lines:

```xml
repositories {
    flatDir {
       dirs 'libs'
    }
}

dependencies {
    // Integrate Adcash SDK:
    compile(name: 'adcash-sdk-lib', ext: 'aar')

    // Required by Adcash SDK:
    compile 'com.android.support:support-v4:24.2.+'
    compile 'com.google.android.gms:play-services-ads:9.2.+'
}
```
![alt tag](http://developer.adca.sh/wp-content/uploads/2016/09/gradle_sync.png)
#### Update AndroidManifest.xml
```xml

    <!-- Include required permissions for Adcash SDK to run -->
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
    
    <application ...>
    ...

        <!-- Include the AdcashActivity -->
        <activity
            android:name="com.adcash.mobileads.ui.AdcashActivity"
            android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize" 
            android:theme="@android:style/Theme.Translucent"
            android:hardwareAccelerated="true" />
            
   <application>
```
### Configure Adcash Custom Event on AdMob Mediation Portal

##### ?	Select App & Add New Network
On AdMob Mediation Portal, click on **Monetize tab** then select one of your app from left panel that you want to monetize. 

On Application page, select one of your **ad unit** (Adcash AdMob Android Adaptor currently supports Banner and Interstitial ad format) and click on **Mediation** for adding new ad network.
![alt tag](http://developer.adca.sh/wp-content/uploads/2016/08/ScreenShot2.png)
On Mediation page, click on **new ad network** and it open new window for configuring it.
![alt tag](http://developer.adca.sh/wp-content/uploads/2016/08/ScreenShot3.png)
##### ?	Add Adcash Custom Ad Network
Click on **Custom Event** and it will open window for filling out information. 
![alt tag](http://developer.adca.sh/wp-content/uploads/2016/08/ScreenShot4.png)
Custom Event Information from:  
>	**Class Name**  
   	_For Banner:_ com.adcash.mobileads.admobadapter.AdcashAdmobBanner  
	_For Interstitial:_ com.adcash.mobileads.admobadapter.AdcashAdmobInterstitial  
>	**Label:** Adcash  
>	**Parameter:** Enter Zone ID from Adcash Publisher Panel

![alt tag](http://developer.adca.sh/wp-content/uploads/2016/08/ScreenShot5.png)

## Release App
Now Adcash is successfully has integrated with AdMob Mediation platform and you can release out the app in PlayStore. Please note changes made in AdMob Portal take couple of hours to reflect.