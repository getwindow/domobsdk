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
			public void onRequestPermissionsResult(int requestCode, String[] permissions, int[] grantResults) {
				super.onRequestPermissionsResult(requestCode, permissions, grantResults);
				//调用多盟权限帮助类相关方法
				DOW.getPermissonHelper(this).onRequestPermissionsResult(requestCode,permissions,grantResults);
			}
			```


