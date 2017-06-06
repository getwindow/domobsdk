#### SDK集成

<b style='color:red'>如果在Android Studio中通过Maven方式接入，可以不在AndroidManifest中注册Activity，Service以及权限</b>，如果通过Jar包形式，AndroidManifest.xml注册信息如下

#### 1.1 将dynamic-4.3.0.jar拷贝到libs下，加入到您的Build Path。


#### 1.2 修改AndroidManifest.xml 添加权限：
```
    <uses-permission android:name="android.permission.MOUNT_UNMOUNT_FILESYSTEMS" />
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
    <uses-permission android:name="android.permission.READ_PHONE_STATE" />
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
    <uses-permission android:name="android.permission.GET_TASKS" />
      <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION"/>
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
    <uses-permission
        android:name="android.permission.PACKAGE_USAGE_STATS"
        tools:ignore="ProtectedPermissions" />
```
#### **Service与APPID注册：**
```
  <!--多盟配置-->
        <activity
            android:name="cn.dow.android.DActivity"
            android:screenOrientation="portrait" />
        <service android:name="cn.dow.android.DService" />

        <meta-data
            android:name="D_PPID"
            android:value="此处填写APP的PPID,即开发者在多盟申请的媒体ID" />
        <!--多盟配置-->
```
activity 是积分墙需要的，而数据模式

#### 1.3 代码混淆

如果是需要混淆代码的，需要在proguard.cfg文件中加上：

-dontwarn cn.dow.\*\*

-keep class cn. dow.\*\* { \*; }

-dontwarn android.support.v4.\*\*

-keep class android.support.v4.\*\* { \*; }

