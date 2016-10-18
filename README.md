# MoPub Mediation Android

This SDK is designed for integrating Adcash with MoPub Mediation on Android to maximize fill rate and revenue.  

It's a simple 3-step integration process.

## Integration Guide

> Assuming integration is already done with MoPub SDK, if not please follow MoPub Integration guideline. (https://dev.twitter.com/mopub/android/getting-started) 

**Prerequisite:** Android Studio 1.0 or higher 

### 1. Download the Adcash SDK

The Adcash SDK is available via:

#### 1. Integration with JCenter repository (Recommended)

The Adcash SDK is uploaded to **JCenter** for your convenience. So you should setup your project to sync to the JCenter repository to allow it to download the Adcash SDK from there.  
In your project base `build.gradle` file add:

```xml
repositories {
    jcenter()
}
```
<a href="http://developer.adca.sh/wp-content/uploads/2015/12/integration_with_gradle_start.png"><img src="http://developer.adca.sh/wp-content/uploads/2015/12/integration_with_gradle_start-300x188.png" alt="integration_with_gradle_start" width="300" height="188" class="aligncenter size-medium wp-image-835" /></a>

When you sync you should now have successfully prepared your project to download from JCenter.  


Then simply include the **Adcash SDK** to your project dependencies. Make sure to also include the two library dependencies used and needed by the Adcash SDK - **Google Play Services** and **Android Support Library v4**.  
Add the following lines to your module based `build.gradle` file:

```xml
dependencies {
    // Integrate Adcash SDK:
    compile 'com.adcash:adcash-mopub-adapter:2.2.1'

    // Required by Adcash SDK:
    compile 'com.android.support:support-v4:24.2.0'
    compile 'com.google.android.gms:play-services:9.4.0'
}
```

<a href="http://developer.adca.sh/wp-content/uploads/2015/12/integration_with_gradle.png"><img src="http://developer.adca.sh/wp-content/uploads/2015/12/integration_with_gradle-300x188.png" alt="integration_with_gradle" width="300" height="188" class="aligncenter size-medium wp-image-833" /></a>

You may see a warning message across the top of the Android Studio window indicating that Gradle needs to perform a Gradle sync.    
If that is the case, click **Sync Now** and Gradle will refresh your project libraries to include the dependencies you just added. You should now have successfully integrated the Adcash SDK into your project.  
At last, go to **Finalize Integration** to make your newly integrated Adcash SDK ready to work with.
#### 2. Integration with local file

Download the Adcash SDK [here](http://developer.adca.sh/wp-content/uploads/2016/09/adcash-mopub-adapter.zip).
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
    compile(name: 'adcash-mopub-adapter', ext: 'aar')

    // Required by Adcash SDK:
    compile 'com.android.support:support-v4:24.2.+'
    compile 'com.google.android.gms:play-services-ads:9.2.+'
}
```
<a href="http://developer.adca.sh/wp-content/uploads/2016/09/gradle_sync.png"><img src="http://developer.adca.sh/wp-content/uploads/2016/09/gradle_sync-300x207.png" alt="gradle_sync" width="300" height="207" class="aligncenter size-medium wp-image-1102" /></a>
### 2. Update AndroidManifest.xml
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
### 3. Configure Adcash Custom Event on MoPub Mediation Portal

##### 3.1. Add a Network
On MoPub Dashboard, click on **Networks tab** then click on **Add a Network** button. 

<a href="http://developer.adca.sh/wp-content/uploads/2016/09/ScreenShot2.png"><img src="http://developer.adca.sh/wp-content/uploads/2016/09/ScreenShot2-300x26.png" alt="ScreenShot2" width="300" height="26" class="aligncenter size-medium wp-image-1131" /></a>

On the **Add a Network** page select **Custom Native Network** under **Additional Networks** section.

<a href="http://developer.adca.sh/wp-content/uploads/2016/09/ScreenShot3.png"><img src="http://developer.adca.sh/wp-content/uploads/2016/09/ScreenShot3-273x300.png" alt="ScreenShot3" width="273" height="300" class="aligncenter size-medium wp-image-1127" /></a>

##### 3.2. Configure Custom Native Ad Network

Give it a title **Adcash**, then scroll down for ad units (Adcash MoPub Android Adapter currently supports Banner and Interstitial ad format)
Custom Event Information from:  
>	**Custom Event Class:**  
   	_For Banner:_ com.adcash.mobileads.mopubadapter.AdcashMoPubBanner  
	_For Interstitial:_ com.adcash.mobileads.mopubadapter.AdcashMoPubInterstitial   
>	**Custom Event Class Data:**  
>	Enter your Zone ID from Adcash Publisher Panel. It has to be in JSON format with parametr name "adZoneID"
>	Example: {"adZoneID": "your_zone_id"}  

<a href="http://developer.adca.sh/wp-content/uploads/2016/09/ScreenShot4.png"><img src="http://developer.adca.sh/wp-content/uploads/2016/09/ScreenShot4-300x106.png" alt="ScreenShot4" width="300" height="106" class="aligncenter size-medium wp-image-1128" /></a>

## Release App
Now Adcash is successfully has integrated with MoPub Mediation platform and you can release out the app in PlayStore. Please note changes made in MoPub Portal might take couple of hours to reflect.

## Support
If you need any help or assistance you can contact us by sending email to <strong>mobile@adcash.com</strong>
