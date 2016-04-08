/*
Title: 百度移动统计平台接入
Description: 百度移动统计配置指南
Sort: 
*/

开发者在使用百度移动统计模块前需要到百度移动统计平台申请appkey，在config.xml文件中配置appkey，或者在应用初始化模块中传入你申请的appkey，来统计你的app信息。

该appkey的申请与您应用的创建过程有关，具体流程请参考如下介绍。

##申请步骤

- 登录百度账号

访问移动统计首页面，使用你已经注册的账号登录，未注册的用户需要注册一个新的账号。
登录地址：http://mtj.baidu.com/web/welcome/login
如下图：

![图片说明](/img/baiduMTJ/login.png) 
 
- 登陆控制台

登录会跳转到APP统计看板，显示当前你的app名称及关键数据，
具体如下图：

![图片说明](/img/baiduMTJ/main.png) 

- 创建应用

点击"新增应用"，系统将为您弹出app创建页面，输入应用名称，选择对应的平台和应用类型：
 
![图片说明](/img/baiduMTJ/add.png)

- 获取AppKey

![图片说明](/img/baiduMTJ/appkey.png)
百度移动统计平台的appkey获取需要区分移动平台，意味着如果你的同一个应用需要同时支持IOS和Android平台，那么，您必须为这两个平台单独申请appkey，即同一个应用申请两个appkey，并将这两个appkey同时在初始化模块中配置。 

##统计数据：
进入单个app统计页面后会出现相关统计数据，用户只要根据数据输出报表就可以了。
![图片说明](/img/baiduMTJ/mtj.png)

##appkey的初始化：
- 1、在程序中带入appkey的方法，双平台需要先判断操作系统，如是单平台的app则无需判断过程。
 
          var path = "";
          var appkey = "";
				if(sType == "android"){
			  	appkey="你申请的android的appkey";
				path ="apicloud";
					}else{
				appkey="你申请的ios的appkey";
				path = "AppStore";
				}
		  var analysis = api.require('MTJ_Analysis');
			  analysis.init({
			     appid:appkey,
			     path:path
			    });

初始化需要放在首页面的apiready = function()函数中，app启动后过10分钟，你就可以看到你的统计数据了。

- 2.在config.xml文件中配置的方法

          
          <feature name="baiduMTJ">
              <param name="android_appkey" value="你申请的android key"/>
              <param name="ios_appkey" value="你申请的ios key"/>
              <param name="android_channel" value="自定义的安卓渠道号"/>
              <param name="ios_channel" value="自定义的苹果渠道号"/>
          </feature>
          