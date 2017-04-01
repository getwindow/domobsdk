```
<b>开发者朋友，您好！</b>
```

```
为了便于您顺利使用多盟积分墙广告服务，请您首先仔细阅读本文档。
###  1 积分墙广告产品介绍
#### 1.1什么是积分墙     
   积分墙广告是一种新型的移动广告形式，以列表墙的形式展现丰富多样的广告任务。开发者在APP中使用积分墙服务，用户通过完成积分墙上的任务，免费获得APP内的虚拟货币。
####  1.2 积分墙的优势     
   对开发者而言，用户每完成一个积分墙任务，开发者能够获得一次分成收益。因此积分墙是帮助开发者最快实现流量变现的激励广告形式。积分墙支持开发者高度自定义，能够在不损害用户体验的前提下，提高用户APP内活跃度及用户黏性。对用户而言，积分墙是一种获得APP内虚拟货币的新途径，具有新鲜感与强吸引力。积分墙是深受开发者和用户欢迎的广告形式。
#### 1.3积分墙的用法  
   积分墙是用户获得APP内虚拟货币的来源，开发者需要向用户提供虚拟货币的消费场景。
   消费场景包括但不限于以下几种： 
   • 购买APP内虚拟道具或周边物品：如游戏道具、主题皮肤等
   • 解锁APP内关卡： 如小说章节、游戏关卡等    
   • 兑换APP内功能服务：如参与抽奖、获得额外的活动机会、享受会员特权等
   • 兑换实物商品或充值类商品：如兑换流量、话费充值等
   • 换算成人民币提现
 ####  1.4 积分墙的任务
  ##### 1.4.1任务类型
  1）基础任务     
  一般是下载类任务，需要用户按照任务要求完成基础任务后，会激发其它的任务
  2）额外奖励任务     
  完成基础任务后，会激发对应的特定时间的特殊任务，如激发在完成基础任务后的第1天、第3天、第5天可以完成的任务等。按照任务要求，用户在特定时间完成相应任务，可以获得得额外的积分奖励
#####   1.4.2任务流程
  1）基础任务     
  第一步：进入详情页（从“任务列表”中，点击任务，进入详情页）           第二步：按照任务要求完成任务（每个应用的任务要求都不一样，请仔细阅读任务规则）    
  【举例】任务要求为“首次下载安装并注册即可获3000积分”      
  步骤一：点击详情页中的按钮，下载并安装应用（确保应用从未下载过，更新/卸载后再安装的都不可获得奖励）      
  步骤二：在下载的应用中完成注册     
  步骤三：领取奖励（完成任务后，务必返回积分墙，刷新列表，获得相应的积分奖励）
  2）额外奖励任务     
  在完成下载类任务后，会激发额外奖励任务，额外奖励任务会显示在“额外奖励”列表中     
  <b>第一步</b>：按照任务要求完成任务（每个应用的任务要求都不一样，请仔细阅读任务规则）    
  【举例】任务要求为“第3天浏览3件商品即可获1000积分”，可做时间：9月28日      
  步骤一：只有在9月28日可以完成本任务      
  步骤二：点击“额外奖励”列表页中的任务      
  步骤三：打开应用，在应用中浏览3件商品     
  <b>第二步</b>：领取奖励（完成任务后，务必返回积分墙，刷新列表，获得相应的积分奖励）
### 2 积分墙广告加载方法
#### 2.1注册账号 
  您首先需要去多盟官网注册一个开发者账号，注册地址：
  http：// www.domob.cn/passport/user/register       
  注册后，需要填写一些必要的身份认证资料、财务信息，等待多盟审核人员审核。 
#### 2.2创建积分墙应用      
   当您的开发者账号审核通过之后，您就可以创建积分墙应用了。在“积分墙”菜单下可以看到您的“积分墙应用列表”，点击“创建积分墙应用”，如图：       
   ![](/assets/5EFF61C4-3493-44E2-90BF-36917A226F71.png)
   您需要填写应用的相关信息：      
   • 应用平台：是指应用的操作系统     
  • 应用名称：不超过20个字符      
  • 应用类型：应用的内容分类      
  • 货币名称：应用内部的货币名称，不超过3个字      
  • 兑换比例：开发者获得1元分成时，返给用户的货币数（不能填写小于1的数）        
  【举例】假设在您的应用中1元等价于100积分，且您与用户三七分成，即您获得1元时返给用户0.7元，也就是70积分。那么此处应填写“70”
#### 2.3 获取Publisher ID      
  创建应用之后，系统将会为您的应用创建一个唯一标识Publisher ID，在嵌入SDK时需要使用到。如图： 
  ![](/assets/696D4855-6B04-41E5-8F1B-B3098632D385.png)
   此Publisher ID只能这个应用中使用，请不要在您的其他应用中使用，否则会被判定为作弊应用， 作弊应用中广告不产生收入。 
#### 2.4 嵌入积分墙SDK      
  获取到Publisher ID后，下载并在您的应用中嵌入积分墙SDK。嵌入时必须使用该应用的Publisher ID，嵌入方法详见SDK安装包。嵌入完成后您可以自行测试。
#### 2.5 上传应用      
  在您的应用成功嵌入积分墙SDK之后，点击上传应用。上传的apk文件大小限制为30M，当您的应用超过这个限制时请联系多盟客服，并将应用包名和apk文件发给客服，客服将转给审核人员。您的应用将会在2个工作日内审核完，在积分墙应用列表中可以直接看到应用审核状态。如果审核拒绝，您可以根据拒绝的理由修改后重新提交。 
### 3 积分墙广告收入查看方式        
  当您的应用在商店成功上架后，您就会逐渐获得积分墙广告收入，在多盟官网应用统计报表里可以查看相应的收入。      
  报表中包含以下数据项：      
  • 入口点击量：积分墙入口的点击量，等价于用户进入积分墙的次数 
  • 关联展现量：积分墙上的广告展示量      
  • 关联点击量：积分墙上的广告点击量      
  • 广告激活数量：积分墙上广告的激活数
  • 广告激活收入：积分墙上广告激活带来的收入
  ### 4. 常见问题
 ####  4.1 积分墙显示异常(没有广告)
  <b> 1）问题现象：</b>显示异常空白或一直loading     
  <b>问题原因：</b>1、手机没有网络 2、手机网络设置代理 3、Publisher ID设置错误     
  <b>解决办法：</b>首先检查Publisher ID是否是应用对应的。如Publisher ID没有问题，建议产看网络是否正常，如果设置了代理，代理去掉后重试
  <b>2）问题现象：</b>提示“任务没有了请过一会再来”     
  <b>问题原因：</b>1、做任务的设备异常 2、当天广告任务已经做完  
  3、Publisher ID
  <b>错误解决办法：</b>
  1、需要使用有SIM卡的非root设备，否则看不到任务         
  2、确认一天内是否已经做完10个任务(只包含激活任务，深度任务不算)	          
  3、检查是否提供正确的Publisher ID                    
  4、检查应用是否已通过审核，未通过审核的应用无法看到任务 
  #### 4.2激活回调失败(开发者没有收到激活回调)     
  <b>问题现象：</b>开发者已经完成任务，并提示已获取奖励，但是未收到激活回调     
  <b>问题原因：</b>1、回调地址配置错误   2、服务器延迟     
  <b>解决办法：</b>请确认激活回调配置是否正确。若正确无误，请耐心等待3-5分钟，可能存在服务器延迟。若仍无法解决，请联系我们
 ####  4.3 积分墙广告无法下载     
  <b>问题现象：</b>用户无法下载广告而且积分墙列表无法显示图片     
  <b>问题原因：</b>移动宽带限制导致     
 <b> 解决办法：</b>确定用户是否是在移动宽带下进行测试
#### 4.4 嵌入积分墙后可以直接打开，但是打包后运行崩溃     
 <b> 问题原因：</b>打包时SDK被二次混淆了     
 <b> 解决办法：</b>按文档要求进行混淆配置
```



