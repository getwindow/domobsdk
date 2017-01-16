### SDK集成

注：关于工程里如何使用SDK部分 ，以例子工程为准，文档只做参考。

#### 1.1 将dynamic-4.3.0.jar拷贝到libs下，加入到您的Build Path。

注：积分墙 SDK 依赖 android-support-v4.jar，并且指定target-sdk 21 以上编译.

否则会影响积分墙的正常运行。

#### 1.2 修改AndroidManifest.xml 添加权限：

&lt;uses-permissionandroid:name="android.permission.MOUNT\_UNMOUNT\_FILESYSTEMS" /&gt;

&lt;uses-permissionandroid:name="android.permission.INTERNET" /&gt;

&lt;uses-permissionandroid:name="android.permission.ACCESS\_NETWORK\_STATE" /&gt;

&lt;uses-permissionandroid:name="android.permission.READ\_PHONE\_STATE" /&gt;

&lt;uses-permissionandroid:name="android.permission.WRITE\_EXTERNAL\_STORAGE" /&gt;

&lt;uses-permissionandroid:name="android.permission.ACCESS\_WIFI\_STATE" /&gt;

&lt;uses-permissionandroid:name="android.permission.GET\_TASKS" /&gt;

&lt;uses-permissionandroid:name="android.permission.PACKAGE\_USAGE\_STATS"

tools:ignore="ProtectedPermissions" /&gt;

**Service与APPID注册：**

**&lt;activity**

android:name="cn.dow.android.DActivity"

 android:screenOrientation="portrait"&gt;

&lt;intent-filter&gt;

&lt;categoryandroid:name="android.intent.category.DEFAULT"/&gt;

&lt;actionandroid:name="aa.bb.cc.dd"/&gt;

&lt;/intent-filter&gt;

**&lt;/activity&gt;**

**&lt;serviceandroid:name="cn.dow.android.DService" /&gt;**

&lt;meta-data **android:name="D\_PPID"**

android:value="此处填写APP的PPID,即开发者在多盟申请的媒体ID" /&gt;



#### 1.3 初始化

在应用的入口处\(即:

第一个启动的Activity\)初始化多盟SDK，在Activity的onCreate的加入下面的代码:

DOW.getInstance\(this\).init\(\);

#### 1.4 代码混淆

如果是需要混淆代码的，需要在proguard.cfg文件中加上：

-dontwarn cn.dow.\*\*

-keep class cn. dow.\*\* { \*; }

-dontwarn android.support.v4.\*\*

-keep class android.support.v4.\*\* { \*; }

