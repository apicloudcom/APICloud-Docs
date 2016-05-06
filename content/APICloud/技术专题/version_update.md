/*
Title: 版本更新
Description: 版本更新
*/

#概述

您可以使用APICloud 的版本更新服务，来向用户推送您App的新版本。版本更新服务只针对正式版APP，测试版无效。只能由低版本更新到高版本。


##参考视频  

入门概念篇第七节（如何使用APICloud云端应用服务）：http://docs.apicloud.com/APICloud/videos-and-codes


#一、使用自动更新

1， config.xml 中配置

  ``` 
   <preference name="autoUpdate" value="true" />
  ```

2，登录APICloud官网，进入控制台，找到应用服务下的“版本”(图一)，点击进入版本管理界面（图二），如图：

   图一：
   ![版本](/img/version/version1.jpg)

   图二：
   ![版本](/img/version/version2.jpg)

3，点击“更新APP版本”，选择版本并填写更新地址，更新备注，最后点击“更新”按钮。

   ![版本](/img/version/version3.jpg)
  

   更新地址在云编译页面，点开编译记录，点击查看地址图标获取，如下图：

   ![版本](/img/version/version4.jpg)

4，打开手机上的APP，即可接收到新版本的推送。


# 二、使用API更新
也可使用mam模块更新，参考文档： http://docs.apicloud.com/%E7%AB%AFAPI/%E4%BA%91%E6%9C%8D%E5%8A%A1%E5%AF%B9%E6%8E%A5/mam

首先在项目代码config.xml中配置：


   ``` 
     <preference name="autoUpdate" value="false" />
  ```


示例代码：

	```
      function checkUpdate() {
				var mam = api.require('mam');
				mam.checkUpdate(function(ret, err) {
					if (ret) {
						var result = ret.result;
						if (result.update == true & result.closed == false) {
							var str = '新版本型号:' + result.version + ';更新提示语:' + result.updateTip + ';下载地址:' + result.source + ';发布时间:' + result.time;
							api.confirm({
								title : '有新的版本,是否下载并安装 ',
								msg : str,
								buttons : ['确定', '取消']
							}, function(ret, err) {
								if (ret.buttonIndex == 1) {
									if (api.systemType == "android") {
										api.download({
											url : result.source,
											report : true
										}, function(ret, err) {
											if (ret && 0 == ret.state) {/* 下载进度 */
												api.toast({
													msg : "正在下载应用" + ret.percent + "%",
													duration : 2000
												});
											}
											if (ret && 1 == ret.state) {/* 下载完成 */
												var savePath = ret.savePath;
												api.installApp({
													appUri : savePath
												});
											}
										});
									}
									if (api.systemType == "ios") {
										api.installApp({
											appUri : result.source
										});
									}
								}
							});
						} else {
							api.alert({
								msg : "暂无更新"
							});
						}
					} else {
						api.alert({
							msg : err.msg
						});
					}
				});
			}
		```


  

