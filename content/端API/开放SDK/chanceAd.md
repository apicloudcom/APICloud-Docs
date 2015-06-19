/*
Title: chanceAd
Description: chanceAd
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">方法</a></li>
	<li><a href="#const-content">常量</a></li>
</ul>



<div id="method-content">

<div class="outline">
[initChanceAd](#initChanceAd)
[showBanner](#showBanner)
[removeBanner](#removeBanner)
[showInterstitial](#showInterstitial)
[closeInterstitial](#closeInterstitial)
[showMoreGame](#showMoreGame)
[closeMoreGame](#closeMoreGame)
</div>

#**概述**

畅思广告平台，是触控科技旗下的专业移动开发者和广告主服务平台。本模块封装了畅思多个 SDK 产品，只需简单调用几个接口即可实现对广告平台的集成。目前包括：横幅(Banner)、插屏(Interstitial)、精品推荐(MoreGame)展示型广告。
 
开发者需要注意在畅思后台为自己的 App 申请独立的 Publisher ID 和 Placement ID参见[基本概念](!Constant)。


#**initChanceAd**<div id="initChanceAd"></div>

广告SDK初始化

##params

adType：

- 类型：字符串
- 描述：广告类型，0 横幅类型；1 插屏类型；2 精品推荐类型

publisherID：

- 类型：字符串
- 描述：应用 ID（详见[基本概念](!Constant)），不能为空，且必须为在畅思广告平台后台中申请的正确应用 ID

placementID：

- 类型：字符串
- 描述：广告位 ID（详见[基本概念](!Constant)），不能为空，且必须为您在畅思广告平台后台申请的对应横幅广告位 ID

##示例代码

```js
var chance = api.require('chanceAd');

chance.initChanceAd({adType:"0", publisherID:"100032-4CE817-ABA2-5B48-14D009296720", placementID:""}, function(ret, err) {
});

```

## 补充说明

该方法只适用于Android平台，每种广告类型使用前均需要调用。iOS平台可以不调用

## 可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**showBanner**<div id="showBanner"></div>

展示横幅广告(banner)

showBanner(params, callback)

##params

publisherID：

- 类型：字符串
- 描述：应用 ID（详见[基本概念](!Constant)），不能为空，且必须为在畅思广告平台后台中申请的正确应用 ID

placementID：

- 类型：字符串
- 描述：广告位 ID（详见[基本概念](!Constant)），不能为空，且必须为您在畅思广告平台后台申请的对应横幅广告位 ID

x：

- 类型：浮点数
- 描述：横幅广告显示位置的 X 坐标

y：

- 类型：浮点数
- 描述：横幅广告显示位置的 Y 坐标

requestInterval：

- 类型：整数
- 描述：横幅广告相邻两次广告请求的请求间隔

displayTime：

- 类型：整数
- 描述：横幅广告一次广告的展现时长

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
     Type:Banner                                  // 广告类型Banner
	 Msg:ReceiveAd、ADError、WillShow、DidRemove   // banner 广告状态
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    errorid:0    //错误码
    msg:""       //错误描述
}
```

##示例代码

```js
var chance = api.require('chanceAd');

chance.showBanner({publisherID:"100032-4CE817-ABA2-5B48-14D009296720", placementID:"", x:"0", y:"20", "requestInterval":"20", "displayTime":"15"}, function(ret, err) {
});

```

##补充说明

此接口向广告平台请求横幅(banner)广告并自动显示

目前我们所支持的横幅广告尺寸包括

Size     | Recommended
---------|--------------
320x50   | iPhone/iPod Touch
728x90   | iPad

## 可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**removeBanner**<div id="removeBanner"></div>

移除横幅广告(banner)

removeBanner(params, callback)

##params
为空即可

##callback
无回调

##示例代码

```js
var chance = api.require('chanceAd');

chance.removeBanner({}, function(ret, err) {
});

```

#**showInterstitial**<div id="showInterstitial"></div>

展现插屏广告(interstitial)

showInterstitial(params, callback)

##params

publisherID：

- 类型：字符串
- 描述：应用 ID（详见[基本概念](!Constant)），不能为空，且必须为在畅思广告平台后台中申请的正确应用 ID

placementID：

- 类型：字符串
- 描述：广告位 ID（详见[基本概念](!Constant)），不能为空，且必须为您在畅思广告平台后台申请的对应横幅广告位 ID

scale：

- 类型：浮点数
- 描述：插屏广告显示比例

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    Type:Interstitial,                                            // 广告类型Interstitial
	Msg:LoadFinished、ADError、DidShow、WillClose、DidClose       // Interstitial广告状态
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    errorid:0    //错误码
    msg:""       //错误描述
}
```

##示例代码

```js
var chance = api.require('chanceAd');

chance.showInterstitial({publisherID:"100032-4CE817-ABA2-5B48-14D009296720", placementID:"", scale:"0.9"}, function(ret, err) {
   });
```

## 可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
#**closeInterstitial**<div id="closeInterstitial"></div>

关闭插屏广告(Interstitial)

closeInterstitial(params, callback)

##params

为空即可

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    Type:Interstitial                                            // 广告类型Interstitial
    Msg:LoadFinished、ADError、DidShow、WillClose、DidClose       // Interstitial广告状态
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code:0    //错误码
    msg:""    //错误描述
}
```

##示例代码

```js
var chance = api.require('chanceAd');

chance.closeInterstitial({}, function(ret, err) {
});

```

## 可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
#**showMoreGame**<div id="showMoreGame"></div>

展示精品推荐广告(MoreGame)

showMoreGame(params, callback)

##params

publisherID：

- 类型：字符串
- 描述：应用 ID（详见[基本概念](!Constant)），不能为空，且必须为在畅思广告平台后台中申请的正确应用 ID

placementID：

- 类型：字符串
- 描述：广告位 ID（详见[基本概念](!Constant)），不能为空，且必须为您在畅思广告平台后台申请的对应横幅广告位 ID

scale：

- 类型：浮点数
- 描述：插屏广告显示比例

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    Type:MoreGame                                               // 广告类型MoreGame
	Msg:LoadFinished、ADError、DidShow、WillClose、DidClose       // Interstitial广告状态
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    errorid:0    //错误码
    msg:""       //错误描述
}
```

##示例代码

```js
var chance = api.require('chanceAd');

chance.showMoreGame({publisherID:"100032-4CE817-ABA2-5B48-14D009296720", placementID:"", scale:"0.9"}, function(ret, err) {
   });
```

## 可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**closeMoreGame**<div id="closeMoreGame"></div>

关闭精品推荐广告(MoreGame)

closeMoreGame(params, callback)

##params

为空即可

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    Type:Interstitial                                            // 广告类型Interstitial
    Msg:LoadFinished、ADError、DidShow、WillClose、DidClose       // Interstitial广告状态
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code:0    //错误码
    msg:""    //错误描述
}
```

##示例代码

```js
var chance = api.require('chanceAd');

chance.closeMoreGame({}, function(ret, err) {
});

```

## 可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

</div>




<div id="const-content">

<div class="outline">
[基本概念](#1)

[广告类型](#2)
</div>

#**基本概念**<div id="1"></div>

- PublisherID：应用 ID，您的 App 在畅思广告平台中的唯一标识。
- PlacementID：广告位 ID，媒体在畅思广告平台中为某类广告申请的广告位标识。


#**广告类型**<div id="2"></div>


类型  |   说明  
-----|--------|
Banner| 横幅广告|
Intersititial| 插屏广告|
MoreGame| 精品推荐|

</div>




 

