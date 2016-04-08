/*
Title: 友盟统计平台接入指南
Description: 友盟统计平台接入指南
*/

#概述
开发者在使用 umengAnalytics 模块接入友盟统计平台时，需要开发者自行到友盟官网申请相应的统计应用AppKey，并将该AppKey以feature的形式配置到您项目的 config.xml 文件中。

umengAnalytics 模块的具体使用步骤如下：

##申请AppKey

使用本模块之前需先到友盟注册账号。注册地址为：[http://www.umeng.com/users/sign_up](http://www.umeng.com/users/sign_up)

![注册](http://community.apicloud.com/bbs/data/attachment/forum/201603/28/151323kzvqfv9m30fqihhi.png "注册")

注册帐号后登录网站，分别创建 Android 和 iOS 两个平台的应用，创建时请选择 **标准统计分析**，创建地址为：[http://www.umeng.com/apps/new](http://www.umeng.com/apps/new)

![创建应用](http://community.apicloud.com/bbs/data/attachment/forum/201603/28/152447zi3d4kdaissj6stc.png "创建应用")

创建后分别获取 Android 和 iOS 两个平台的 AppKey

![获取AppKey](http://community.apicloud.com/bbs/data/attachment/forum/201603/28/152447lpwly0ww2pzwm0kq.png "获取AppKey")

用得到的AppKey配置 APICloud 项目的 config.xml 文件
- 名称：umengAnalytics
- 参数：

     **ios_app_key：**iOS应用的 appkey

    **ios_app_channel：**（可选项）iOS应用的渠道名称。名称可自定义，去掉这一项的话将使用平台默认渠道名称

    **android_app_key：**Android应用的 appkey

    **android_app_channel：**（可选项）Android应用的渠道名称。名称可自定义，去掉这一项的话将使用平台默认渠道名称
- 备注：若要移除本模块，需要先删除 config.xml 中的配置项，提交代码到云端后方可在APICloud控制台的模块栏目移除。
- 配置示例:
```
<feature name="umengAnalytics">
    <param name="ios_app_key" value="56f8dbd5e0f55a467d001cb6"/>
    <param name="ios_app_channel" value="APICloud_iOS"/>
    <param name="android_app_key" value="56f8dc2567e58ee2cb002616"/>
    <param name="android_app_channel" value="APICloud_Android"/>
</feature>
```

提交代码到APICloud云端后，umengAnalytics 模块将自动添加到你的项目。此时，只需 **云编译** 或者 **编译自定义Loader** 项目即可使用 umengAnalytics 模块。
![提交代码](http://community.apicloud.com/bbs/data/attachment/forum/201603/28/153507j6fpprqpt61pnhlq.png "提交代码")

##自定义页面统计的使用
自定义页面统计功能可以统计用户使用APP过程中，各个不同页面的访问次数、平均访问时长、跳出率等数据。

首先必须在 index.html 或应用入口文件里调用 ```init``` 接口初始化模块（模块使用前必须初始化，在下面几项功能介绍时不再重复描述了）。

然后在页面打开时，调用 ```onPageStart``` 接口，在页面关闭时调用 ```onPageEnd``` 接口，如此，便完成的一次页面的统计。

建议：如果你的页面使用的是 APICloud 的 win+frame 的结构，只需在 win 里调用即可。由于 iOS 可以手势关闭页面，Android 可以按返回键关闭页面，为了不照成统计遗漏，在这里给出一个自定义页面统计的参考代码以解决这两种关闭模式带来的问题：
```js
	var umengAnalytics = null;
	
	// 点击界面中的返回按钮(图标)时结束自定义页面统计
    function closeWin(){
        onPageEnd();
        api.closeWin();
    }
	// 结束统计
	function onPageEnd(){
		umengAnalytics.onPageEnd({
			pageName:'列表页',
		},function(ret,err){
             if(ret.status){
                   //api.alert({msg: '结束统计自定义页面'});
             }else{
                   api.alert({msg: err.code+' '+err.msg});
             }
		});
	}
	
    apiready = function(){
        umengAnalytics = api.require('umengAnalytics');
        // 开始统计
        umengAnalytics.onPageStart({
            pageName:'列表页',
        },function(ret,err){
             if(ret.status){
                   //api.alert({msg: '开始统计自定义页面'});
             }else{
                   api.alert({msg: err.code+' '+err.msg});
             }
        });
		
        // iOS手势关闭页面时结束自定义页面统计
        api.addEventListener({
            name:'viewdisappear'
        },function(ret,err){
            onPageEnd()
        });
        
        // Android按返回键关闭页面时结束自定义页面统计
        api.addEventListener({
            name:'keyback'
        },function(ret,err){
        	closeWin();
        });
	};
```

## 查看自定义页面的统计报表

打开友盟控制台进入应用

![进入应用](http://community.apicloud.com/bbs/data/attachment/forum/201603/28/162153beoor5xe5e9aoyer.png "进入应用")

打开 **页面访问路径** 点击 **管理版本** 

![页面访问路径](http://community.apicloud.com/bbs/data/attachment/forum/201603/28/162200n1pghh1sfl7lzslv.png "页面访问路径")

把需要统计的 APP 版本从右侧点到左侧去

![版本管理](http://community.apicloud.com/bbs/data/attachment/forum/201603/28/162201w2kkt775et4bymbd.png "版本管理")

最后在页面的左上角和右上角选择要查看的版本和日期

![选择版本](http://community.apicloud.com/bbs/data/attachment/forum/201603/28/163029ujv30vwef1t97dfe.png "版本管理")
![选择日期](http://community.apicloud.com/bbs/data/attachment/forum/201603/28/162201vfy3crvpvp13faau.png "选择要查看统计数据的日期")

即可查看数据

![数据](http://community.apicloud.com/bbs/data/attachment/forum/201603/28/162202s58155rexsrqgoam.png "数据")

**注意：** 自定义页面统计不是实时的，需第二天才能查看。且会把测试设备的数据隔离开，以免数据污染，详细介绍请 [点击这里](http://bbs.umeng.com/thread-9166-1-1.html)


##自定义事件统计的使用

自定义事件统计，自定义事件可以实现在应用程序中埋点来统计用户的点击行为。自定义事件目前包括“计数事件”和“计算事件”，二者的区别以及详细说明请[点击这里](http://dev.umeng.com/analytics/functions/numekv)

首先进入友盟应用的控制台，打开事件管理页面

![打开事件管理页面](http://community.apicloud.com/bbs/data/attachment/forum/201603/28/164432p9qb44lxqkbfajdk.png "打开事件管理页面")

根据自己需要添加事件

![添加事件](http://community.apicloud.com/bbs/data/attachment/forum/201603/28/164432ngjogflspjfqjggb.png "添加事件")

然后回到 APICLoud 的项目中，在需要做事件统计的地方调用 ```onEvent``` 接口来做统计工作，此接口的具体使用方法请看模块接口文档。


## 查看自定义事件的统计报表

打开友盟控制台进入应用

![进入应用](http://community.apicloud.com/bbs/data/attachment/forum/201603/28/162153beoor5xe5e9aoyer.png "进入应用")


打开 **自定义事件页面** 即可查看各个事件的统计数据

![查看各个事件的统计数据](http://community.apicloud.com/bbs/data/attachment/forum/201603/28/165900vt3ddd0b2idk33i3.png "查看各个事件的统计数据")

## 账号统计的启用

友盟在统计时以设备为标准，如果需要统计应用自身的账号，需使用 ```profileSignIn``` 和 ```profileSignOff``` 接口，并在友盟应用控制台中开启。

首先进入应用控制台，打开 **应用信息** 页
![应用信息](http://community.apicloud.com/bbs/data/attachment/forum/201603/28/170831g5fzgpjxjr4opgp6.png "应用信息")

然后启动账号统计，并保存确定
![启动账号统计](http://community.apicloud.com/bbs/data/attachment/forum/201603/28/170831qk6lcggkwgkdll9b.png "启动账号统计")

## 集成测试的使用

集成测试是通过收集和展示已注册测试设备发送的日志，来检验SDK集成有效性和完整性的一个服务。 所有由注册设备发送的应用日志将实时地进行展示，您可以方便地查看包括应用版本、渠道名称、自定义事件、页面访问情况等数据，提升集成与调试的工作效率。所有测试数据将不会进入应用的正常数据处理流程，您不必再担心因为测试而导致的数据污染问题，让数据更加真实有效地反应用户使用情况。

打开测试设备列表页，点击右上角添加测试设备，页面地址：[http://www.umeng.com/test_devices](http://www.umeng.com/test_devices)

![测试设备列表页](http://community.apicloud.com/bbs/data/attachment/forum/201603/28/171817iqh0kdlk88enf8tl.png "测试设备列表页")

此时要求填写一个叫 **设备识别信息** 的东西，这个东西可以在项目代码中，调用模块的 ```testDeviceID``` 接口获取，然后再用 ```console.log``` 打印出来复制到里面去。

![填写测试设备信息](http://community.apicloud.com/bbs/data/attachment/forum/201603/28/171817ubfc95868vbpb994.png "填写测试设备信息")

**注意：**
 1. 使用集成测试时，在模块初始化（init）的时候，参数 ```debugMode``` 需设置为 ```true```；
 2. ```testDeviceID``` 接口返回的是JSON格式字的 **字符串**，而非JSON **对象**，所以返回的数据可以直接拿来使用；


## 查看集成测试数据


在集成测试页面，可以选择实时日志和历史日志查看测试数据


![查看集成测试数据](http://community.apicloud.com/bbs/data/attachment/forum/201603/28/173059lou2iz60z7nso0fg.png "查看集成测试数据")

**注意：** 测试数据会在完成一次完整的APP启动与关闭后，再次启动APP时才会发送统计数据到友盟后台中去。

Android平台一次完整的启动包括如下三种情况：

 1. 从启动应用到关闭应用；
 2. 从启动应用到应用退至后台，且在后台运行时间超过30s；
 3. 启动应用后设备黑屏，黑屏时间超过30s；

iOS平台一次完整的启动包括如下两种情况：

 1. 从启动应用到关闭应用；
 2. 从启动应用到应用退至后台，此种情况iOS与Android不同，iOS只要退至后台就算本次启动的结束；
