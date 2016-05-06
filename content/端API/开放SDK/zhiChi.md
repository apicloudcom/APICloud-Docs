/*
Title: zhiChi
Description: chichi
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：智齿</p>

<ul id="tab" class="clearfix">
<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">
</div>
[startZhiChi](#1)

#**概述**
智齿客服全面支持桌面网站、移动网站、微信、微博、APP五种接入方式，只要10分钟就可以将智齿客服嵌入所有营销路径，各渠道用户反馈汇总至智齿客服平台统一轻松管理，企业客服效率提升50%以上。

zhiChi是一款实现手机用户与企业保持随时随刻沟通的客服工具。本模块封装了智齿客服的相关接口。使用此模块之前需要先注册智齿获取sysNum （enterpriseId）

![图片说明](/img/docImage/zhiChi_app_sdk.jpg)

**注册方法如下:**

使用管理员账号登陆[智齿管理后台](https://www.sobot.com/console/register?adv=apicloud)，在 **桌面网站客服 > 接入桌面网站** 页面中即可得到 `sysNum` 用于配置。

注意：本模块在ios上支持最低版本为6.0

<div id="1"></div>
#**startZhiChi**

启动智齿客服

startZhiChi({params})

##params
***
初始化信息相关参数，适用于iOS和android系统(特殊说明除外)
***
>sysNum：

- 类型：字符串
- 默认值：无
- 描述：注册智齿后，从智齿后台获得的enterpriseId，不可为空

>userId：

- 类型：字符串
- 默认值：无
- 描述：用户标识，自动备注客户资料，可为空（建议填写，对数据统计更准确，不填默认是设备唯一标识）

>nickName：

- 类型：字符串
- 默认值：无
- 描述：用户昵称，可为空（填写后，客服后台会同步到备注）

>phone：

- 类型：字符串
- 默认值：无
- 描述：用户电话，可为空

>email

- 类型：字符串
- 默认值：无
- 描述：用户邮箱，可为空


>customInfo（仅适用iOS）

- 类型：json串
- 默认值：无
- 描述：自定义用户资料，自动同步到客户工作台，可为空


>isKeepSession（仅适用iOS）

- 类型：bool
- 默认值：NO
- 描述：是否保持会话，默认NO,点击返回直接断开会话链接


> isShowEvaluate（仅适用iOS）

- 类型：bool
- 默认值：NO
- 描述：自定义关闭的时候是否推送满意度评价

> isSettingSkillSet（仅适用iOS）

- 类型：bool
- 默认值：NO
- 描述：是否主动传递技能组 值为YES，SDK内部转接人工将不再弹出技能组选项




>skillSetId（仅适用iOS）

- 类型：字符串
- 默认值：无
- 描述：技能组编号，根据传递的值转接到对应的技能组；配合isSettingSkillSet使用，仅当值为YES时有效


> goodsTitle（仅适用iOS）

- 类型：字符串
- 默认值：无
- 描述：内容描述，如果要显示必须填写；自定义咨询内容，在转接人工成功时，方便用户发送自己咨询的信息

>goodsSendText（仅适用iOS）

- 类型：字符串
- 默认值：无
- 描述：发送给客服的内容，如果要显示必须填写；自定义咨询内容，在转接人工成功时，方便用户发送自己咨询的信息

>goodsImage（仅适用iOS）

- 类型：字符串
- 默认值：无
- 描述：图片URL；自定义咨询内容，在转接人工成功时，方便用户发送自己咨询的信息


>themeColor（仅适用Android）：

- 类型：字符串
- 默认值：#09aeb0
- 描述：可设置头部颜色; 提交评价问题选中背景色以及提交评价按钮背景色; 聊天内容中，相似问题字体颜色和富文本类型中“阅读全文”字体颜色，可为空

>isShowTansfer（仅适用iOS）:

- 类型：boolean
- 默认值：YES
- 描述：机器人优先模式，是否直接显示转人工按钮(值为NO时，会在机器人无法回答时显示转人工按钮)


>isCustomLinkClick（仅适用iOS）:

- 类型：boolean
- 默认值：0
- 描述：自己处理消息中的链接，如果设置为1，将通过callBack返回到页面ret=1,value为link实际地址，desc为描述



>backButtonTitle（仅适用iOS）:

- 类型：字符串
- 默认值：“关闭”
- 描述：返回按钮的文字



>backButtonImage（仅适用iOS）:

- 类型：字符串
- 默认值：无
- 描述：返回按钮的图片名称(项目的直接路径[UIImage imageNamed:图片名称])，可以与backButtonTitle同时存在

***
自定义字体，（所有参数可选，并且仅适用iOS）
***
>titleFont：

- 类型：CGFloat
- 默认值：18.0
- 描述：顶部标题颜色、评价标题，可为空

>listTitleFont：

- 类型：CGFloat
- 默认值：16.0
- 描述：页面返回按钮，输入框，评价提交按钮、Toast提示语，可为空

>listDetailFont：

- 类型：CGFloat
- 默认值：14.0
- 描述：各种按钮，网络提醒，可为空


>listTimeFont：

- 类型：CGFloat
- 默认值：12.0
- 描述：消息提醒(转人工、客服接待等)，可为空

>chatFont：

- 类型：CGFloat
- 默认值：15.0
- 描述：聊天气泡中文字，可为空

***
自定义背景颜色，（所有参数可选，并且仅适用iOS）
***

>backgroundColor：

- 类型：字符串
- 默认值：#f0f0f0
- 描述：对话页面背景，可为空

>customBannerColor：

- 类型：字符串
- 默认值：#08b0b0
- 描述：顶部banner颜色值，可为空


>leftChatColor：
- 类型：字符串
- 默认值：#FFFFFF
- 描述：左侧气泡颜色，可为空

>rightChatColor：

- 类型：字符串
- 默认值：#08b0b0
- 描述：右边气泡颜色，可为空


>backgroundBottomColor：

- 类型：字符串
- 默认值：#e6e9e9
- 描述：底部工具栏的背景颜色，可为空



> bottomLineColor：

- 类型：字符串
- 默认值：#e6e9e9
- 描述：底部工具栏边框线颜色(输入框、录音按钮、分割线)，可为空


> commentButtonBgColor：

- 类型：字符串
- 默认值：#08b0b0
- 描述：评价普通按钮选中颜色(默认跟随主题色customBannerColor)，可为空


> commentCommitButtonColor：

- 类型：字符串
- 默认值：#08b0b0
- 描述：评价提交按钮颜色(默认跟随主题色customBannerColor)，可为空


> BgTipAirBubblesColor：

- 类型：字符串
- 默认值：#cacacb
- 描述：提示气泡的背景颜色，可为空



***
自定义文字颜色，（所有参数可选，并且仅适用iOS）
***


> topViewTextColor：

- 类型：字符串
- 默认值：#FFFFFF
- 描述：顶部文字颜色(返回、标题)，可为空

> leftChatTextColor：

- 类型：字符串
- 默认值：#000000
- 描述：左边聊天气泡文字颜色，可为空

> rightChatTextColor：

- 类型：字符串
- 默认值：#FFFFFF
- 描述：右边聊天气泡文字颜色，可为空

> timeTextColor：

- 类型：字符串
- 默认值：#666f6f
- 描述：聊天时间文字的颜色，可为空


> tipLayerTextColor：

- 类型：字符串
- 默认值：#FFFFFF
- 描述：提示气泡文字颜色，可为空

> serviceNameTextColor：

- 类型：字符串
- 默认值：#67706e
- 描述：客服昵称文字颜色，可为空


***
回调函数说明（仅适用iOS）
***
> ret：

- 类型：字典
- 描述：包含3个参数

 type:1 返回，2 点击了消息内容链接（仅当isCustomLinkClick=1时触发）
 
 value:仅当type=2时，返回链接地址
 
 desc:当前操作


> err：未使用



##示例代码
```js
var param = {
sysNum:"*******************",
userId:"Your User ID",
nickName:"Your nickName",
phone:"4008-690-981",
email:"service@sobot.com",
isShowTansfer:1,
titleFont:18.0,
backgroundColor:"#f0f0f0",
topViewTextColor:"#FFFFFF",
    isCustomLinkClick:1,
    backButtonTitle:"返回",
    backButtonImage:"SobotKit.bundle/ZCWebTitleBack_normal.png",
};

function callback(ret, err){
    alert("ret.type="+ret.type+"\nvalue="+ret.value+"\nret.desc="+ret.desc);
}

var zhichi = api.require('zhiChi');
zhichi.startZhiChi(param,callBack);
```

##补充说明

使用此模块，必须先传入sysNum参数，其它参数可根据自己实际情况选择设置；

##可用性

iOS系统，Android系统

可提供的1.4.1及更高版本
