/*
Title: dkSDK
Description: dkSDK
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">方法</a></li>
</ul>
<div id="method-content">
<div class="outline">
[registerKey](#registerKey)
[getBannerAD](#getBannerAD)
[setHideDate](#setHideDate)
[getIntAD](#getIntAD)
</div>

#**概述**
   
   dkSDK 封装了点开广告平台的SDK，使用此模块可轻松实现添加广告到应用的功能,根据需求放置调用的位置。

#**registerKey**<div id="registerKey"></div>
注册key.

registerKey(params);

##params

DIANKAI_APP_KEY:

-	类型:字符串
-	默认值:无
-	描述:开发者在点开平台申请的APPKEY.


DIANKAI_INTAD_KEY:

-	类型: 字符串
-	默认值:无
-	描述:开发者在点开平台申请的插屏广告的使用KEY.

DIANKAI_BANNER_KEY:

-	类型:数组
-	默认值:无
-	描述:开发者在点开平台申请的横幅广告的使用KEY.

##示例代码

```js
var keys = {
    "ios": {
        DIANKAI_APP_KEY:"6b1b80d155dbbf468a48b65729f68219",
        DIANKAI_INTAD_KEY:"9c00ed79d40ee2f4bc20a891e86ca92c",
        DIANKAI_BANNER_KEY:"50a1290f30ec1964b10b6d6d306ef2a0"
    },
    "android": {
        DIANKAI_APP_KEY:"d86bdd51a028c377f8b68c6c5ffe3c71",
        DIANKAI_INTAD_KEY:"2c1ee0e567a6e1fb2a64874ad0698659",
        DIANKAI_BANNER_KEY:"b1adc08abf036aabed011fc2c8753de6"
    }
};

var key = keys[api.systemType];

var dkSDK = api.require('dkSDK');

dkSDK.registerKey({
    DIANKAI_APP_KEY:"YOUR_APPKEY",
    DIANKAI_INTAD_KEY:"YOUR_INTAD_KEY",
    DIANKAI_BANNER_KEY:"YOUR_BANNER_KEY"
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getBannerAD**<div id="getBannerAD"></div>
banner广告展示.

getBannerAD(params);

##params

height:

-	类型:数字
-	默认值: 屏幕高度
-	描述:宽度设置.


width:

-	类型: 数字
-	默认值: ios为 屏幕宽度.
-	描述:宽度设置.

##示例代码

```js
var dkSDK = api.require('dkSDK');

dkSDK.getBannerAD({
  height: 100,
  width: 200
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setHideDate**<div id="setHideDate"></div>
设置隐藏banner广告时间.

setHideDate(params);

##params

hideDate:

-	类型: number
-	默认值: 60 * 60 * 1000 .
-	描述:经过多长时间再次广告,单位毫秒.

##示例代码

```js
var dkSDK = api.require('dkSDK');

dkSDK.setHideDate({
   hideDate: 3000
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**removeBannerAD**<div id="removeBannerAD"></div>
隐藏广告.

setHideDate();

##示例代码

```js
var dkSDK = api.require('dkSDK');

dkSDK.removeBannerAD();
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**getIntAD**<div id="getIntAD"></div>
展示插屏广告.

getIntAD(params);

##params

height:

-	类型:数字
-	默认值: 屏幕高度
-	描述:宽度设置.


width:

-	类型: 数字
-	默认值: ios为 屏幕宽度.
-	描述:宽度设置.

##示例代码

```js
var dkSDK = api.require('getIntAD');

dkSDK.getBannerAD({
  height: 100,
  width:100
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本