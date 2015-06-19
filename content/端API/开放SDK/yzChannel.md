/*
Title: yzChannel
Description: yzChannel
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#basic-content">方法</a></li>
</ul>
<div id="basic-content">

<div class="outline">
[init](#a1)

[show](#a2)
</div>

#**概述**

游族市场是游族网络[SZ.002174]为开发者量身打造的精品游戏中心。本模块能提供最新最优的游戏产品，以及更高的收入回报。
使用此模块之前，需要注册游族开放平台，获取Channelid。

注册方法如下：[游族市场管理后台](http://partner.open.youzu.com/)，注册登陆后在【我的渠道】中选择添加渠道，信息完善之后，即可获取Channelid 。
详情请咨询 游族技术支持QQ:2775807414

暂仅支持安卓.

#**init**<div id="a1"></div>

初始化游族渠道

init(params)

##params

### channel_id

- 类型：字符串
- 默认值: 无
- 描述: 注册游族开放平台后，从后台获得的ChannelID，不可为空

### Channel_data

- 类型：字符串
- 默认值: 无
- 描述: 渠道自定义参数，可为空

##示例代码

```js
var yzChannel = api.require('yzChannel');
var params = {
    "channel_id":"3b151b6fe72cfcb2512334130f7d70b8",
    "channel_data":"custom"
};

yzChannel.init(params);
```

##补充说明

使用此模块，必须先用init初始化

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**show**<div id="a2"></div>

打开渠道界面

show();

##示例代码

```js
var yzChannel = api.require('yzChannel');yzChannel.show();
```

##补充说明

调用该接口之前，一定要先调用init初始化，否则无法正确启动。

##可用性

Android系统

可提供的1.0.0及更高版本
