# Integrate AdFly by ironSource custom Networks

## Language
* ch [中文](chinese.md)

### Support ads
1. Reward
2. Interstitial

### Support platforms
1. Android

### ironSource version
7.2.1.1 or latest

## Add Network configurations in ironSource Dashboard

### 1. Add SDK Network
In the ironSource dashboard, select [MONETIZE > Setup -> SDK Networks](https://platform.ironsrc.com/partners/monetize/mediation/setup). then click **“Manage Networks”** and select **“Custom Adapter”**。

![](1.png)

Enter **“15bac1a39”** for the **Network Key**, Click **Enter Key**, Once the network key is recognized, you’ll be able to see the network’s name and save it。

![](2.png)

### 2. Configure Custom Adapter
In the SDK Networks, Select which app you want to configure，Select AdFly in the Networks list and click Setup。

![](3.png)

- **App Secret**: secret of AdFly
- **App Key**: key of AdFly
- **Unit ID**: Unit ID of AdFly
- **Rate**：eCMP of AdFly。Reference：[Instance rate](https://developers.is.com/ironsource-mobile/general/instance-rate-2/#step-1)

## Integrate in Android

### 1. Integrate ironSource in Android
Reference [ironSource Integration](https://developers.is.com/ironsource-mobile/android/android-sdk/)

### 2. Add dependency libraries
Open your project and update the project’s `build.gradle` to include the following repositories.

```
allprojects {
    repositories {
       // ... other repositories

        mavenCentral()
    }
}
```

Open your app module's `build.gradle` to include the following dependencies.

```
dependencies {
    // ... other project dependencies

    implementation 'pub.adfly:adapter-ironsource:0.14.+'
}
```

## Integrate in Unity

### 1. Integrate ironSource in Unity
Reference: [ironSource Integration](https://developers.is.com/ironsource-mobile/unity/unity-plugin/)

### 2. Add dependencies
Add `IronSourceSDKDependencies.xml` in folder `Assets/IronSource/Editor`：

```xml
<dependencies>
    <unityversion>4.3.37.2</unityversion>
  <androidPackages>
    <androidPackage spec="pub.adfly:adapter-ironsource:0.14.3.0">
      <repositories>
        <repository>https://repo1.maven.org/maven2/</repository>
      </repositories>
    </androidPackage>
  </androidPackages>
</dependencies>
```

![](4.png)

## Check integrate successful

After integrate is successful，If request Reward ads, filter  `AdFly` in logcat will have logs like these:

```
D/AdFlyIronSourceAdapter: initialize, configuration: {instanceName=Default, revByRate=true, customNetworkAdapterName=AdFlyCustomRewardedVideo, instanceType=1, customNetworkPackage=com.ironsource.adapters.custom.adfly, rateReporting=1, userId=null, isDefault=true, deleted=0, isCustomNetwork=true, maxAdsPerSession=99, customNetwork=AdFly, unitId=1867, appKey=xx, appSecret=xx}
I/AdFly: AdFly SDK
    ======Build Info======
    Version: 0.11.5
    Time: 2022-03-25 11:14:16
    Commit: 80d9df8
    ======Device Info======
    GAID: xx
    ======User Info======
    UserId: xx
D/AdFlyIronSourceAdapter: onInitializationFinished
D/AdFlyRewardedVideo: loadAd: 1867
D/AdFlyRewardedVideo: onRewardedAdLoadSuccess
```