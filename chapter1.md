#### SDK集成

<b style='color:red'>如果在Android Studio中通过Maven方式接入，可以不在AndroidManifest中注册Activity，Service以及权限</b>，如果通过Jar包形式，AndroidManifest.xml注册信息如下

#### 1.1 将dynamic-4.3.0.jar拷贝到libs下，加入到您的Build Path。


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

#### **Service与APPID注册：**

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

activity 是积分墙需要的，而数据模式

#### 1.3 代码混淆

如果是需要混淆代码的，需要在proguard.cfg文件中加上：

-dontwarn cn.dow.\*\*

-keep class cn. dow.\*\* { \*; }

-dontwarn android.support.v4.\*\*

-keep class android.support.v4.\*\* { \*; }

