/*
Title: adsDomob
Description: Domob APICloud 接口文档
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：多盟广告</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">

<div class="outline">
[presentFlexibleBanner](#a1)
[presentBanner](#a2)
[initInterstitial](#a3)
[presentInterstitial](#a4)
[presentSplash](#a5)
[initDBox](#a6)
[presentDBoxEntry](#a7)
[sendDBoxEntryImpression](#a8)
[sendDBoxEntryClick](#a9)
</div>

#**概述**

多盟（简称DOMOB），中国第一智能手机广告DSP+移动广告网络，本模块封装了多盟多个 SDK 产品，只需简单调用几个接口即可实现对广告平台的集成。目前包括：横幅(Banner)、插屏(Interstitial)、开屏(Splash)展示型广告，以及多宝屋(DBox)综合型广告等。
 
开发者需要注意在多盟后台为自己的 App 申请独立的 Publisher ID 和 Placement ID参见[基本概念](!Constant)。另外，发布 App 的时候也请参见[AppStore](!Constant)审核注意事项”。

注意：本模块暂时仅支持IOS平台

#**presentFlexibleBanner**<div id="a1"></div>

展示自适应横幅广告(banner)

presentFlexibleBanner({params}, callback(ret, err))

##params

publisherId：

- 类型：字符串
- 描述：应用 ID（详见[基本概念](!Constant)常量），不能为空，且必须为在多盟广告平台后台中申请的正确应用 ID

placementId：

- 类型：字符串
- 描述：广告位 ID（详见[基本概念](!Constant)常量），不能为空，且必须为您在多盟广告平台后台申请的对应横幅广告位 ID

x：

- 类型：浮点数
- 描述：横幅广告显示位置的 X 坐标

y：

- 类型：浮点数
- 描述：横幅广告显示位置的 Y 坐标

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
    type:0                   // banner 广告 详见[广告类型](!Constant)常量）
	status:-1~3              // banner 广告状态码 详见[广告请求状态码](!Constant)常量）
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
    code: 0,    //错误码
    msg: ''    //错误描述
}
```

##示例代码

```js
var adsDomob = api.require('adsDomob');

adsDomob.presentBanner({
    publiserId: '56OJyM1ouMGoULfJaL',
    placementId: '16TLwebvAchkANUH_krQ7vOz',
    x: '0',
    y: '20'
}, function(ret, err) {
    if (ret.type == 0) {
        switch (ret.status) {
            case -1:
                api.alert({msg:'Banner 广告加载失败:' + err});
                break;
            case 0:
                api.alert({msg:'Banner 广告加载完成'});
                break;
            case 1:
                api.alert({msg:'Banner 广告准备展现'});
                break;
            case 2:
                api.alert({msg:'Banner 广告被关闭'});
                break;
            case 3:
                api.alert({msg:'Banner 广告被切到后台'});
                break;
        }
    }
});

```

##补充说明

此接口向广告平台请求自适应横幅(banner)广告并自动显示

##可用性

iOS系统

可提供的1.0.0及更高版本

#**presentBanner**<div id="a2"></div>

展示横幅广告(banner)

presentBanner({params}, callback(ret, err))

##params

publisherId：

- 类型：字符串
- 描述：应用 ID（详见[基本概念](!Constant)常量），不能为空，且必须为在多盟广告平台后台中申请的正确应用 ID

placementId：

- 类型：字符串
- 描述：广告位 ID（详见[基本概念](!Constant)常量），不能为空，且必须为您在多盟广告平台后台申请的对应横幅广告位 ID

x：

- 类型：浮点数
- 描述：横幅广告显示位置的 X 坐标

y：

- 类型：浮点数
- 描述：横幅广告显示位置的 Y 坐标

x：

- 类型：浮点数
- 描述：横幅广告显示位置的 X 坐标

width：

- 类型：浮点数
- 描述：横幅广告的宽度

height：

- 类型：浮点数
- 描述：横幅广告的高度

autorefresh：

- 类型：整数，0 (false) 或者 1(true)
- 描述：是否自动刷新广告

目前我们所支持的横幅广告尺寸包括

Size     | Recommended
---------|--------------
320x50   | iPhone/iPod Touch
300x250  | iPhone/iPod Touch
488x80   | iPad
728x90   | iPad
600x500  | iPad
Flexible | All iOS Devices

`**我们强烈建议您使用Flexible Banner**`，它可以适应各种类型的设备，以及进行横竖屏的自适应（Flexible Banner的高度在iPhone/iPod Touch上为`50`，在iPad上为`90`，宽度自适应）。

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
    type:0                   // banner 广告 详见[广告类型](!Constant)常量）
	status:-1~3              // banner 广告状态码 详见[广告请求状态码](!Constant)常量）
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
    code:0    //错误码
    msg:''    //错误描述
}
```

##示例代码

```js
var adsDomob = api.require('adsDomob');
adsDomob.presentBanner({
    publiserId:'56OJyM1ouMGoULfJaL',
    placementId:'16TLwebvAchkANUH_krQ7vOz',
    x:'0',
    y:'20',
    width:'375',
    height:'325', autorefresh:'1'
}, function(ret, err) {
    if (ret.type == 0) {
        switch (ret.status) {
            case -1:
                api.alert({msg:'Banner 广告加载失败:' + err});
                break;
            case 0:
                api.alert({msg:'Banner 广告加载完成'});
                break;
            case 1:
                api.alert({msg:'Banner 广告准备展现'});
                break;
            case 2:
                api.alert({msg:'Banner 广告被关闭'});
                break;
            case 3:
                api.alert({msg:'Banner 广告被切到后台'});
                break;
        }
    }
});

```

##补充说明

此接口向广告平台请求横幅(banner)广告并自动显示

##可用性

iOS系统

可提供的1.0.0及更高版本
#**initInterstitial**<div id="a3"></div>

初始化插屏广告(interstitial)

presentBanner({params}, callback(ret, err))

##params

publisherId：

- 类型：字符串
- 描述：应用 ID（详见[基本概念](!Constant)常量），不能为空，且必须为在多盟广告平台后台中申请的正确应用 ID

placementId：

- 类型：字符串
- 描述：广告位 ID（详见[基本概念](!Constant)常量），不能为空，且必须为您在多盟广告平台后台申请的对应插屏广告位 ID

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
    type:1                   // interstitial 广告  详见[广告类型](!Constant)常量）
	status:-1~3              // interstitial 广告状态码 详见[广告请求状态码](!Constant)常量）
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
    code:0    //错误码
    msg:''    //错误描述
}
```

##示例代码

```js
var adsDomob = api.require('adsDomob');

adsDomob.initInterstitial({
    publiserId:'56OJyM1ouMGoULfJaL',
    placementId:'16TLwebvAchkAY6iOWkE6kpk'
}, function(ret, err) {
    if (ret.type == 1) {
        switch (ret.status) {
            case -1:
                api.alert({msg:'插屏广告加载失败:' + err});
                break;
            case 0:
                api.alert({msg:'插屏广告加载完成'});
                break;
            case 1:
                api.alert({msg:'插屏广告准备展现'});
                break;
            case 2:
                api.alert({msg:'插屏广告被关闭'});
                break;
            case 3:
                api.alert({msg:'插屏广告被切到后台'});
                break;
        }
    }
});
```

##补充说明

此接口初始化插屏环境

##可用性

iOS系统

可提供的1.0.0及更高版本
#**presentInterstitial**<div id="a4"></div>

展示插屏广告(banner)

presentInterstitial({params}, callback(ret, err))

##params

无

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
    type:1                   // interstitial 广告  详见[广告类型](!Constant)常量）
	status:-1~3              // interstitial 广告状态码 详见[广告请求状态码](!Constant)常量）
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
    code:0    //错误码
    msg:''    //错误描述
}
```

##示例代码

```js
var adsDomob = api.require('adsDomob');

adsDomob.presentInterstitial({},
    function(ret, err) {
        if (ret.type == 1) {
            switch (ret.status) {
                case -1:
                    api.alert({msg:'插屏广告加载失败:' + err});
                    break;
                case 0:
                    api.alert({msg:'插屏广告加载完成'});
                    break;
                case 1:
                    api.alert({msg:'插屏广告准备展现'});
                    break;
                case 2:
                    api.alert({msg:'插屏广告被关闭'});
                    break;
                case 3:
                    api.alert({msg:'插屏广告被切到后台'});
                    break;
            }
        }
    });

```

##补充说明

此接口展示插屏(interstitial)广告

##可用性

iOS系统

可提供的1.0.0及更高版本
#**presentSplash**<div id="a5"></div>

展示开屏广告(splash)

presentSplash({params}, callback(ret, err))

##params

publisherId：

- 类型：字符串
- 描述：应用 ID（详见[基本概念](!Constant)常量），不能为空，且必须为在多盟广告平台后台中申请的正确应用 ID

placementId：

- 类型：字符串
- 描述：广告位 ID（详见[基本概念](!Constant)常量），不能为空，且必须为您在多盟广告平台后台申请的对应开屏广告位 ID

splashBackgroundImageUrl：

- 类型：字符串
- 描述：当开屏广告是半屏时，最好有一个背景图，会比较美观。如果不指定，那么非广告区域将是透明的。这个参数指定一张可下载的 PNG/JPEG 图片。这张图片的规格是，
	1. iPhone4 1x: 320 x 480
	2. iPhone4s 2x: 640 x 960
	3. iPhone5/5s 2x: 640 x 1136
	4. iPhone6 2x: 750 x 1334
	5. iPhone6plus 3x: 1242 x 2208

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
    type:2                   // splash 广告  详见[广告类型](!Constant)常量）
	status:-1~3              // splash 广告状态码 详见[广告请求状态码](!Constant)常量）
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
    code:0    //错误码
    msg:''    //错误描述
}
```

##示例代码

```js
var adsDomob = api.require('adsDomob');
adsDomob.presentSplash({
    publiserId:'56OJyM1ouMGoULfJaL',
    placementId:'16TLwebvAchkAY6iOVhpfHPs',
    splashImageUrl:'http://static.hothdwallpaper.net/51aac68f51f8599006.jpg'
}, function(ret, err) {
    if (ret.type == 2) {
        switch (ret.status) {
            case -1:
                api.alert({msg:'开屏广告加载失败:' + err});
                break;
            case 0:
                api.alert({msg:'开屏广告加载完成'});
                break;
            case 1:
                api.alert({msg:'开屏广告准备展现'});
                break;
            case 2:
                api.alert({msg:'开屏广告被关闭'});
                break;
            case 3:
                api.alert({msg:'开屏广告被切到后台'});
                break;
        }
    }
});
```

##补充说明

此接口向广告平台请求开屏(splash)广告并缓存，并在下一次调用的时候显示开屏广告；另外，此次展示完毕后，会准备好下一条广告

##可用性

iOS系统

可提供的1.0.0及更高版本
#**initDBox**<div id="a6"></div>

初始化多宝屋广告环境

initDBox({params}, callback(ret, err))

##params

publisherId：

- 类型：字符串
- 描述：应用 ID（详见[基本概念](!Constant)常量），不能为空，且必须为在多盟广告平台后台中申请的正确应用 ID

placementId：

- 类型：字符串
- 描述：广告位 ID（详见[基本概念](!Constant)常量），不能为空，且必须为您在多盟广告平台后台申请的对应多宝屋广告位 ID

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
    type:3                   // 多宝屋(dbox)广告
	status:-1~3              // 多宝屋(dbox)广告状态码 详见[广告请求状态码](!Constant)常量）
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
    code:0    //错误码
    msg:''    //错误描述
}
```

##示例代码

```js
var adsDomob = api.require('adsDomob');
adsDomob.initDBox({
        publiserId:'56OJw+rouN8xdhPaW9',
        placementId:'16TLuFnvAp2p4NU06al1hNgi'
    },function(ret, err) {
        if (ret.type == 3) {
            switch (ret.status) {
                case -1:
                    api.alert({msg:'多宝屋广告加载失败:' + err});
                    break;
                case 0:
                    api.alert({msg:'多宝屋广告加载完成'});
                    break;
                case 1:
                    api.alert({msg:'多宝屋广告准备展现'});
                    break;
                case 2:
                    api.alert({msg:'多宝屋广告被关闭'});
                    break;
                case 3:
                    api.alert({msg:'多宝屋广告被切到后台'});
                    break;
            }
        }
    });
```

##补充说明

此接口初始化多宝屋广告环境

##可用性

iOS系统

可提供的1.0.0及更高版本
#**presentDBoxEntry**<div id="a7"></div>

展示多宝屋(dbox)广告入口

presentDBoxEntry({params}, callback(ret, err))

##params

publisherId：

- 类型：字符串
- 描述：应用 ID（详见[基本概念](!Constant)常量），不能为空，且必须为在多盟广告平台后台中申请的正确应用 ID

placementId：

- 类型：字符串
- 描述：广告位 ID（详见[基本概念](!Constant)常量），不能为空，且必须为您在多盟广告平台后台申请的对应的多宝屋广告位 ID

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
    type:3                   // 多宝屋(dbox)广告
	status:-1~3              // 多宝屋(dbox)广告状态码 详见[广告请求状态码](!Constant)常量）
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
    code:0    //错误码
    msg:''    //错误描述
}
```

##示例代码

```js
var adsDomob = api.require('adsDomob');
adsDomob.presentDBoxEntry({
    publiserId:'56OJw+rouN8xdhPaW9',
    placementId:'16TLuFnvAp2p4NU06al1hNgi'
},function(ret, err) {
    if (ret.type == 3) {
        switch (ret.status) {
            case -1:
                api.alert({msg:'多宝屋广告加载失败:' + err});
                break;
            case 0:
                api.alert({msg:'多宝屋广告加载完成'});
                break;
            case 1:
                api.alert({msg:'多宝屋广告准备展现'});
                break;
            case 2:
                api.alert({msg:'多宝屋广告被关闭'});
                break;
            case 3:
                api.alert({msg:'多宝屋广告被切到后台'});
                break;
        }
    }
});
```

##补充说明

此接口向广告平台请求多宝屋(dbox)广告并自动显示多宝屋入口

##可用性

iOS系统

可提供的1.0.0及更高版本
#**sendDBoxEntryImpression**<div id="a8"></div>

发送多宝屋入口展现报告

sendDBoxEntryImpression({params}, callback(ret, err))

##params

无

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
无
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
无
}
```

##示例代码

```js
var domob = api.require('adsDomob');
domob.sendDBoxEntryImpression(function(ret, err) {
    
});
```

##补充说明

此接口发送多宝屋入口展现报告。详见[多宝屋广告注意事项](!Constant)。

##可用性

iOS系统

可提供的1.0.0及更高版本
#**sendDBoxEntryClick**<div id="a9"></div>

发送多宝屋入口点击报告

sendDBoxEntryClick({params}, callback(ret, err))

##params

无

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	无
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
	无
}
```

##示例代码

```js
var adsDomob = api.require('adsDomob');
adsDomob.sendDBoxEntryClick(function(ret, err) {

});
```

##补充说明

此接口发送多宝屋入口点击报告。详见[多宝屋广告注意事项](!Constant)。

##可用性

iOS系统

可提供的1.0.0及更高版本
</div>
<div id="const-content">

<div class="outline">
[基本概念](#1)

[OS 支持](#2)

[广告类型](#3)

[广告请求状态码](#4)

[多宝屋广告注意事项](#5)

[AppStore 审核注意事项](#6)
</div>

#**基本概念**<div id="2"></div>

- PID：应用 ID，也叫 Publisher ID。您的 App 在多盟广告平台中的唯一标识。
- PPID：广告位 ID，也叫 Placement ID。媒体在多盟广告平台中为某类广告申请的广告位标识。

#**OS 支持**<div id="2"></div>
 `iOS 5.0 及以上`


#**广告类型**<div id="3"></div>


类型  |   编号   | 说明  
-----|--------|--------|
bannder| 0 | 横幅广告|
intersititial| 1 | 插屏广告|
splash| 2 | 开屏广告|
dbox| 3 | 多宝屋广告|


#**广告请求状态码**<div id="4"></div>
为了让开发者更细粒度地控制广告请求流程，我们会将广告请求的重要阶段用状态码的形式回调给调用者。具体的状态码信息描述如下，

1 横幅(banner)广告状态码

 状态码 | 状态  | 说明  
-----|--------|--------|
 -1 |failed| 横幅广告加载失败| 
 0  |loaded| 横幅广告加载成功|
 1  |will present|点击的广告即将展现|
 2  |dismissed| 弹出的广告被关闭|
 3  |enter background| 弹出的广告被切换到后台|  

2 插屏(interstitial)广告状态码

 状态码 | 状态  | 说明  
-----|--------|--------|
 -1 |failed| 插屏广告加载失败| 
 0  |loaded| 插屏广告加载成功|
 1  |will present|插屏广告即将展现|
 2  |dismissed| 插屏广告被关闭|
 3  |enter background| 插屏广告被切换到后台|  

3 开屏(splash)广告状态码

 状态码 | 状态  | 说明  
-----|--------|--------|
 -1 |failed| 开屏广告加载失败| 
 0  |loaded| 开屏广告加载成功|
 1  |will present|开屏广告即将展现|
 2  |dismissed| 开屏广告被关闭|

4 多宝屋(dbox)广告状态码

 状态码 | 状态  | 说明  
-----|--------|--------|
 -1 |failed| 多宝屋加载失败| 
 0  |loaded| 多宝屋加载成功|
 1  |presented|多宝屋界面已展现|
 2  |dismissed| 多宝屋被关闭|
 3  |enter background| 多宝屋被切换到后台| 
 

#**多宝屋广告注意事项**<div id="5"></div>
为了更好、更准确的帮助提升广告投放的准确率，请开发者协助我们发送2个相关的报告。具体如下，
1.发送入口展现报告：就是在您嵌入多宝屋的界面出现时发送此报告，表示入口已经展现出来。如，
<center> ![](images/docImage/domob-apicloud-ios-dbox-entry-impression.png) </center>
在“我的12306”界面出现时发送入口展现报告。

2.发送入口点击报告：就是在用户点击你为多宝屋设定的某个按钮或者表格中的某一行时，发送此报告，表示多宝屋入口被点击。
如上图，在用户点击“旅行休闲”时发送入口点击报告。


#**AppStore 审核注意事项**<div id="6"></div>


1 由于 iOS 广告平台获取了 IDFA，那么在提交 App Store 审核时，请按照下面的截图选择 IDFA 相关的选项。此处以多宝屋为例来说明，当然也可以通过打开横幅(banner)广告来说明获取 IDFA 的目的。

<center> ![](/img/docImage/domob-apicloud-idfa-banner.png) </center>

* <b>`选择一`</b>  在业务管理后台打开横幅广告，并在应用中展示

<center> ![](/img/docImage/domob-apicloud-banner-ad.png) </center>

* <b>`选择二`</b>  在业务管理后台打开多宝屋广告，并在应用中展示

<center> ![](/img/docImage/domob-apicloud-ios-dbox-banner.png) </center>

* 在审核界面的“备注”中，务必用英文或者中英文，详细说明找到横幅广告或者多宝屋 banner 广告的步骤。


 

