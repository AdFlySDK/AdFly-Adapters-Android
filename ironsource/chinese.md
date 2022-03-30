# ironSource 通过聚合方式集成 AdFly

### 支持的广告
1. 激励视频
2. 插屏广告

### 支持的平台
1. Android

### ironSource版本
7.2.1.1以上版本

## 在 ironSource 后台添加聚合配置

### 1. 添加 SDK Network
在 ironSource 控制后台, 选择 [MONETIZE > Setup -> SDK Networks](https://platform.ironsrc.com/partners/monetize/mediation/setup). 然后点击 **“Manage Networks”** 并选择 **“Custom Adapter”**。

![](1.png)

输入 **Network Key** 为 **“15bac1a39”**，点击 **Enter Key** ，当 Network Key 识别到后就可以看到 Adapter 的名称，然后点击 **Save** 保存。

![](2.png)

### 2. 配置 Custom Adapter
在 SDK Networks 中，点击选择需要配置的应用后，在 Networks 列表中选择 AdFly 并点击 Setup。

![](3.png)

- **App Secret**：填写为 AdFly 的 secret
- **App Key**：填写为 AdFly 的 key
- **Unit ID**：填写为 AdFly 的 Unit ID
- **Rate**：填写为 AdFly 该广告位的 eCMP 价格。官方参考：[Instance rate](https://developers.is.com/ironsource-mobile/general/instance-rate-2/#step-1)

## Android集成配置

### 1. 在Android中集成ironSource
参考 [ironSource官方文档](https://developers.is.com/ironsource-mobile/android/android-sdk/)

### 2. 添加依赖库
在 project 根目录下的 `build.gradle` 文件中添加 `mavenCentral()` 作为依赖库的源

```
allprojects {
    repositories {
       // ... other repositories

        mavenCentral()
    }
}
```

在 app 模块的 `build.gradle` 中添加 adfly 依赖

```
dependencies {
    // ... other project dependencies

    implementation 'pub.adfly:adapter-ironsource:0.11.+'
}
```

