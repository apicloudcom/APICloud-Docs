/*
Title: welcomePage
Description: welcomePage
*/
<div class="outline">
[openWelcomePage](#a1)

[setWelcome](#a2)

</div>

#**概述**

welcomePage 封装了首次启动应用时的导航页，模块自动记录是否为第一次启动，可自己设置页数、图标和切换动画，在最后一页整个页面点击会关闭导航页。** 本模块暂仅支持Android 

<div id="a1"></div>
#**openWelcomePage**

打开welcomePage

openWelcomePage({params}, callback(ret))

##params

isFullscreen:

- 类型：布尔
- 描述：（可选项）是否全屏(全屏不显示状态栏)
- 默认值：false

AnimationType:

- 类型：字符串
- 描述：（可选项）动画类型  "Default"  默认, "DepthPage"  深入浅出, "Cube"  立方体, "Rotate"  旋转,"Accordion"  左右折叠, "InRightUp"   右上角进入, "InRightDown"  右下角进入, "ZoomOutPage"  淡入淡出。
- 默认值："Default"

imgs: 

- 类型：数组
- 描述：导航图片（支持 widget:// fs://  不支持相对路径）。

setting:

- 类型：JSON对象
- 描述：（可选项）导航页相关设置。
- 内部字段：

```js
{
	isShow:true,                           // 布尔型；true||false，是否显示导航点 默认不显示
	SelectedImg:  "widget://image/2.png",  // 字符串；导航点选中图片  默认红色小圆圈
	NotSelectedImg: "widget://image/1.png",// 字符串；导航点未选中图片  默认白色小圆圈
	ImgSize:30,                            // 数字型；导航点图片size  默认0
	ImgMarginLeft:30                       // 数字型；导航点图片之间的间隔 默认0
}

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    result: true，      //布尔型；true  是否已经进入过导航页  true 则不会进入导航页  点击最后一张导航页才会让它变成true
    msg: ""            //字符串；一段话，不会变
}
```

```
##示例代码

```js
var WelcomePage = api.require('welcomePage');	
var param = {
	isFullscreen: true,  //是否全屏(全屏不显示状态栏)  默认false
	AnimationType: "ZoomOutPage",  //动画类型   "Default默认", "DepthPage深入浅出", "Cube立方体", "Rotate旋转","Accordion左右折叠", "InRightUp右上角进入" , "InRightDown右下角进入", "ZoomOutPage淡入淡出"
	imgs: ["widget://image/Welcome/3.png","widget://image/Welcome/3.png","widget://image/Welcome/3.png","widget://image/Welcome/3.png"],
	setting: {
		isShow: true, // 是否显示页面点 默认不显示
		SelectedImg: "widget://image/Welcome/2.png",
		NotSelectedImg: "widget://image/Welcome/1.png",
		ImgSize: 30, // 图片size
		ImgSpacing: 30 // 图片之间的间隔
	}
};
WelcomePage.openWelcomePage(param,function(ret){
	alert(JSON.stringify(ret));
});
```

##可用性

Android系统

可提供的1.0.0及更高版本

<div id="a2"></div>
#**setWelcome**

重新设置是否打开导航页

setWelcome({params}, callback(ret))

##params

setWelcome：

- 类型：布尔型
- 描述：（必选项）false 表示设置启动页为未打开状态  true 反之
- 默认值：false


##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    result: true   //布尔型；true  操作成功
}
```

##示例代码

```js
var WelcomePage = api.require('welcomePage');	
var param = {
	setWelcome:false
};
WelcomePage.setWelcome(param,function(ret){
	alert(JSON.stringify(ret));
});
```

##可用性
Android系统

可提供的1.0.0及更高版本