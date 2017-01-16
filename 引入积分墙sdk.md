### 引入积分墙SDK

如果您单纯是想体积分墙功能的功能，建议直接跳过这一步。直接[下载Demo](http://baichuan.taobao.com/doc2/detail?spm=0.0.0.0.ct3Z2i&treeId=41&articleId=102828&docType=1#s0)。

#### Step1.1 Android Studio集成

##### Step1.1.1 配置maven仓库地址

repositories {

```
maven { url 'http://repo.baichuan-android.taobao.com/content/groups/BaichuanRepositories/' }
```

}

##### Step1.1.2 依赖积分墙SDK

dependencies {

```
//必选

compile 'com.alibaba.mobileim:IMCore:2.0.1@aar'

//可选，如果使用SDK的UI必须添加该依赖，如果不使用SDK的UI，完全自己开发UI则无需添加该依赖

compile 'com.alibaba.mobileim:IMKit:2.0.1@aar'

//可选，如果使用小视频功能必须添加该依赖，如果不使用小视频功能则无需添加该依赖

compile 'com.alibaba.mobileim:RecorderSDK:1.0.0@aar'
```

}

#### Step1.2 aar集成

##### Step1.2.1 配置build.gradle

repositories {

```
flatDir {

    dirs 'libs'
```

}

}

##### Step1.2.2 添加依赖

dependencies {

compile fileTree\(dir: ‘libs’, include: \[’\*.jar’\]\)

compile\(name: ‘IMCore-2.0.2’, ext: ‘aar’\)

compile\(name: ‘IMKit-2.0.2’, ext: ‘aar’\)

}

#### Step1.3 Eclipse集成

##### Step1.3.1 下载SDK

如果您已经有了多盟APPID，请先下载SDK。SDK下载后解压，得到以下内容：

![](/assets/import.png)

**目录说明：**

1、doc是API说明文档

2、libs目录包含SDK。（libs中的libinet.so放到lib/armeabi目录）

3、AndroidManifest.xml包含了集成SDK所需的权限和Android组件的声明。

4、proguard.cfg代码混淆配置，开发者需要将这些配置复制到自己APP的混淆配置文件中去。

5、其它文件夹（文件）用户不用去关注。

##### Step1.3.2 Eclipse环境配置

1、将下载的SDK导入到Eclipse，具体操作方法为：File-&gt;Import，然后Android，选择Existing Android Code Into Workspace，

点击下一步，在RootDirectory中填入SDK的具体路径，点击完成。

2、主工程（开发者自己的APP工程）依赖SDK，打开主工程属性（Properties），定位到Android，然后在Libray中选择Add，选择刚才导入的工程Library工程。

3、编辑主工程的属性文件，project.properties，添加manifestmerger.enabled=true

4、proguard.cfg是混淆配置，开发者需要将这些配置复制到自己APP的混淆配置文件中去（注意：是内容上合并，请勿直接文件替换，这一步在打Release包时会用到）。

5、如果自己创建的工程未包含android-support-v4.jar，请从我们的Demo工程中复制，[下载Demo](https://www.baidu.com/)

注意：

详细的集成方式，可以参考我们视频中描述的方法。

我们不建议直接将SDK内容复制到主工程的方式，这样后续SDK升级会比较麻烦，也容易遗漏到一些文件的升级（比如res目录）。

