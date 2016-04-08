/*
Title: customToast
Description: 自定义Toast，让Toast更完美的融入应用，不影响应用的整体美观
*/
<div class="outline">
[toast](#a1)
</div>


#**概述**

customToast 弹出一个定时自动关闭的提示框，自定义Toast，自定义提示框颜色、透明度、字体大小、字体颜色、圆角幅度，显示时间；让Toast更完美的融入应用，不影响应用的整体美观

![](/img/docImage/customToast.jpg)

##toast({params})

显示提示框

##params

msg：

- 类型：字符串
- 描述：提示消息

msgSize：

- 类型：字符串
- 描述：文字大小
- 取值范围：10~40

msgColor：

- 类型：字符串
- 描述：（可选项）文字颜色
- 默认值：#FFFFFF

location：

- 类型：字符串
- 默认值：bottom
- 描述：提示框显示位置，分为上（top) 中（center） 下（bottom）

ico：

- 类型：字符串
- 描述：图标路径，要求本地路径（fs://、widget://）

icoLocation：

- 类型：字符串
- 默认值：left
- 描述：（可选项）图标显示位置，ico参数设置后有效，分为：上（top） 下（bottom） 左（left） 右（right）

duration：

- 类型：字符串
- 描述：持续时长，单位：毫秒

bgColor：

- 类型：字符串
- 描述：提示框背景颜色，颜色值参考：#000000

roundRadius：

- 类型：字符串
- 描述：设置提示框圆角度  只针对Android版本
- 取值范围：0~100

roundRadiusIos：

- 类型：字符串
- 描述：设置提示框圆角度  只针对Ios版本
- 取值范围：0~20

alpha：

- 类型：字符串
- 描述：设置提示框透明度
- 取值范围：0~255

##示例代码

```js
var toastApi = api.require('ToastApi');
var param = {
	msg : "holle world!!",
	msgSize : "23",
	msgColor : "#D52B2B",
	location : "center",
	icoLocation : "top",
	duration : "2000",
	bgColor : "#76916F",
	roundRadius : "100",
	roundRadiusIos : "10",
	alpha : "100"
};
toastApi.toast(param);
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本