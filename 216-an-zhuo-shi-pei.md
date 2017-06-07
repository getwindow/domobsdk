如果的targetSdkVersion为23或者以上版本（安卓6.0及以上系统）需要动态申请READ_PHONE_STATE和WRITE_EXTERNAL_STORAGE两个权限，通过多盟SDK申请过程如下：
(1)设置申请权限的监听，监听用户授予权限的状态			
```java
DOW.getPermissonHelper(this).setOnApplyPermissionListener(new OnGainPermissionListener() {
				//所有权限都成功申请
				@Override
				public void onAllPermissionGained() {
					
				}
				 //用户拒绝了某一个权限，pair.first:权限名称 ；pair.second:权限描述
				@Override
				public void onRefuse(Pair<String, String> permission_msg) {

				}
				//用户勾选了不再显示
				@Override
				public void onRefuseForever() {
					
				}
				//最终授权失败
				@Override
				public void onGainedFail() {
					
				}
			}); 
```
(2)申请权限

```java	
DOW.getPermissonHelper(this).applyPermissions();
```


(3)在activity中重新onRequestPermissionsResult方法，在此方法中调用多盟权限帮助类相关方法
```java	
@Override
public void onRequestPermissionsResult(int requestCode, String[] permissions, int[] grantResults) {			super.onRequestPermissionsResult(requestCode, permissions, grantResults);
			//调用多盟权限帮助类相关方法
				DOW.getPermissonHelper(this).onRequestPermissionsResult(requestCode,permissions,grantResults);
}
			```

如果的targetSdkVersion为24或者以上版本（安卓7.0及以上系统），需要做如下适配：
在AndroidManifest中注册provider
```xml
<provider           
android:name="android.support.v4.content.FileProvider"
android:authorities="包名.fileProvider"
android:exported="false"
android:grantUriPermissions="true">
<!--我们提供 file_paths，也可以在demo中 res/xml下找到-->
<meta-data
android:name="android.support.FILE_PROVIDER_PATHS"
android:resource="@xml/file_paths" />
</provider>
```



在项目的res/xml下添加 file_paths.xml
<?xml version="1.0" encoding="utf-8"?>
<paths>
    <external-path
        name="apkFiles"
        path="DMDownload" />
    <files-path
        name="apkFiles2"
        path="DMDownload" />
</paths>




