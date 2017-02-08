### 引入积分墙SDK

如果您单纯是想体积分墙功能的功能，建议直接跳过这一步。直接[下载Demo](https://pro-app-mt.fir.im/e9b91721f339e6e419a3b59d97f2681e5c3cf343.apk?AWSAccessKeyId=e0cada7f00f2465b929656d799937873&Expires=1486458075&Signature=WTQpDxFMtC3MmC6WT%2Bis1cnh3Mc%3D&filename=domobwall.apk_1.0.apk)。

#### Step1.1 Android Studio集成

##### Step1.1.1 配置maven仓库地址

repositories {

```
maven { url "https://raw.githubusercontent.com/jia635/domobwallsdk/master" }
```

}

即整个Project 中的build.gradle中配置

##### Step1.1.2 依赖积分墙SDK

dependencies {

```
  compile 'cn.dow.android:aowsdk:4.6.0'
```

}

在需要配置的Model 的build.gradle 中 添加依赖SDK地址

#### Step1.3 Eclipse集成

##### Step1.3.1 下载SDK

如果您已经有了多盟APPID，请先[下载SDK](http://s.domob.cn/sdk/domob_android_offerwall_sdk-4.3.0.zip)。SDK下载后解压，得到以下内容：

![](/assets/sdk.png)

**目录说明：**

1、libs目录包含SDK。

2、AOWDataSDKSample是Eclipse环境下的Demo

3、\_6\_0\_demo是Android Studio环境下的Model形式的Demo

4、AndroidManifest.xml包含了集成SDK所需的权限和Android组件的声明。

##### 



