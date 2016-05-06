/*
Title: googleAnalytics
Description: googleAnalytics
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[onPageStart](#g1)
[onPageEnd](#g2)
[onEvent](#g3)
</div>

#**概述**

Google Analytics是著名互联网公司Google为提供的数据统计服务。可以对目标网站、移动端App进行访问数据统计和分析，并提供多种参数供网站、App拥有者使用。

根据今年早些时候的一份社交媒体报告显示，如今对于移动应用的市场分析正存在着巨大的缺口，需求显而易见。虽然目前市面上不乏这样的分析服务，但是能够真正追踪所有相关数据的应用还没有出现。而谷歌旗下知名产品Google Analytics（谷歌分析）适时发布了新的移动应用分析服务（Google Analytics App），旨在填补这一空白的同时帮助营销人员以及开发者更好地衡量他们的应用程序。

本模块封装了 Google Analytics 移动端统计分析的功能。开发者只要在 Google 开放平台注册账号，创建自己的项目，获取对应的追踪 ID 即可集成本模块到自己的 App。轻松实现应用统计分析功能（可统计用户打开了哪些页面，点击了页面上哪些按钮等功能）。

###**模块使用攻略**

**1，账号申请**

使用本模块之前需先到谷歌开放平台申请注册开发者账号。申请地址为：[http://www.google.com/intl/en_ALL/analytics/index.html](http://www.google.com/intl/en_ALL/analytics/index.html)。

![申请注册](/img/docImage/googleAnalytics/g1.png)
![申请注册](/img/docImage/googleAnalytics/g2.png)

**2，创建应用**

申请谷歌开发者账号后点击注册邮箱里的激活链接，激活开发者账号。当你成功注册 Google Analytics 开发者账号后就可以在此账号里创建自己的应用了。在创建应用前，需先创建一个账户。如下图：

![申请注册](/img/docImage/googleAnalytics/g3.png)

进入创建页面，填写相应信息，点击最下端获取跟踪 ID 按钮。

![申请注册](/img/docImage/googleAnalytics/g4.png)

**3，配置跟踪 ID**

应用创建完成后获取跟踪 ID。不管在 ios 平台还是 android 平台都必须先配置获取到的跟踪 ID。

***ios 平台上配置跟踪 ID***

在 iOS 平台上点击下图中入门指南按钮进入 Google [开发者中心](https://developers.google.com/analytics/devguides/collection/ios/v3/)，填写相关信息获取并下载配置文件 GoogleService-Info.plist。

![申请注册](/img/docImage/googleAnalytics/g5.png)

![申请注册](/img/docImage/googleAnalytics/g6.png)

***android 平台上配置跟踪 ID***

在 android 平台上点击上图中入门指南按钮进入 Google [开发者中心](https://developers.google.com/analytics/devguides/collection/android/v4/)，填写相关信息配置 android 平台的相关文件，**注意（与 ios 平台不同）此文件无需下载，只需配置即可。**

**4，配置 [config.xml](/APICloud/技术专题/app-config-manual) 文件**

在 iOS 平台上获取到的 GoogleService-Info.plist 文件全名是：Property List，属性列表文件，它是一种用来存储串行化后的对象的文件。属性列表文件的扩展名为.plist ，因此通常被称为 plist文件。文件是xml格式的。Plist文件通常用于储存用户设置，也可以用于存储捆绑的信息。 如下图所示：

![申请注册](/img/docImage/googleAnalytics/g7.png)

如果你是在 mac 系统下可用 xcode 以列表的形式打开此文件，如果你是在 window 系统下可直接用文本编辑器打开。将上图中红色框部分的字段配置在 [config.xml](/APICloud/技术专题/app-config-manual) 文件内，配置方法如下：

```js
   
    <feature name="googleAnalytics">
        <param name="trackingID" value="UA-74773768-1" />
        <param name="plistVersion" value="1" />
        <param name="bundleID" value="com.apicloud.apicloudad" />
        <param name="appID" value="1:460454799131:ios:4f8a423edde087c6" />
        <param name="projectID" value="apicloudad" />
        <param name="dispatchInterval" value="120" />
    </feature> 
    
```

- 字段描述:

    **feature name**：此处填写模块名 googleAnalytics

    **trackingID**：追踪 ID，plist 文件里 TRACKING_ID 对应的值
    
    **plistVersion**：版本号，plist 文件里 PLIST_VERSION 对应的值
    
    **bundleID**：包名，plist 文件里 BUNDLE_ID 对应的值
    
    **appID**：应用 ID，plist 文件里 GOOGLE_APP_ID 对应的值
    
    **projectID**：工程 ID，plist 文件里 PROJECT_ID 对应的值
    
    **dispatchInterval**：间隔一定时间向 google 服务器发送监听事件，单位为妙（s），默认值是120，若传小于零的数，则表示不自动发送监听事件


***注意：android 平台上只需配置 trackingID 即可，其余字段在 android 平台上忽略。***


**5，查看报告**

登陆谷歌[开发者账号](https://analytics.google.com/analytics/web/#report/app-content-event-events/a74773768w113109203p118122918/%3Fexplorer-segmentExplorer.segmentId%3Danalytics.eventCategory%26explorer-table.plotKeys%3D%5B%5D/)，在自己刚创建的工程里找到自己的项目，即可查看用户使用流量报告。如下图：

![申请注册](/img/docImage/googleAnalytics/g8.png)

在报告->行为->概览里可参看总量数据，本模块目前暂时不支持屏幕浏览类的监听，window 或 frame 的打开关闭事件，可以在事件类别里查看。如下图：

![申请注册](/img/docImage/googleAnalytics/g9.png)

其中的 page 事件即为 window 或 frame 的 open 、 close 事件，在事件操作里可查看事件类型，在事件标签里可查看页面名称（接口内传入的 pageName）。同时，亦可在事件类别->次级纬度->用户->操作系统里查看用户系统平台数据等相关信息，如下图：

![申请注册](/img/docImage/googleAnalytics/g10.png)

**本模块需云编译有效**

##**模块接口**

#**onPageStart**<div id="g1"></div>

监听进入一个页面  

onPageStart({params})  

##params

pageName：

- 类型：字符串
- 描述：页面（window 或 frame ）的名称

##示例代码

```js
var ga= api.require('googleAnalytics');
ga.onPageStart({pageName:'首页'});  
```

##补充说明 

调用此接口后，建议在同一页面调用onPageEnd方法。 
　　 
##可用性  

iOS系统，Android系统  

可提供的1.0.0及更高版本

#**onPageEnd**<div id="g2"></div>

监听离开一个页面  

onPageEnd({params})  

##params

pageName：

- 类型：字符串
- 描述：页面（window 或 frame ）的名称

##示例代码

```js
var ga= api.require('googleAnalytics');
ga.onPageEnd({pageName:'首页'});  
```

##补充说明 

调用此接口前，建议已调用过onPageStart方法 
　　 
##可用性  

iOS系统，Android系统  

可提供的1.0.0及更高版本

#**onEvent**<div id="g3"></div>

监听自定义事件

onEvent({params})  

##params

category：

- 类型：字符串
- 描述：自定义事件种类

action：

- 类型：字符串
- 描述：自定义事件行为

label：

- 类型：字符串
- 描述：自定义事件的标签

value：

- 类型：数字
- 描述：自定义事件的值

##示例代码

```js
var ga= api.require('googleAnalytics');
ga.onEvent({
   category: '按钮',
   action: '点击',
   label: '查看',
   value: 1
});  
```
　　 
##可用性  

iOS系统，Android系统  

可提供的1.0.0及更高版本