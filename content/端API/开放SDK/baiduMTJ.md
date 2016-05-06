/*
Title: baiduMTJ
Description: baiduMTJ
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：开发者</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">
<div class="outline">
[init](#1)

[onEvent](#2)

[onPageStart](#3)

[onPageEnd](#4)
</div>

#**概述**

baiduMTJ 模块封装了百度移动统计SDK，通过调用本模块可实现百度移动统计功能。使用之前需要到[百度移动统计](http://mtj.baidu.com)创建应用。可以通过init接口以参数的形式将appKey传进去，也可以配置config文件，设置appkey，程序优先使用init初始化中传入的appkey，如未设置则在调用config文件中的appkey，其他方法需在初始化后才能使用。

**使用此模块之前可以配置  config 文件（如不进行配置，则一定要在init方法中做相关配置）配置方法如下：**

- 名称：baiduMTJ
- 参数：android_appkey、ios_appkey、android_channel、ios_channel
- 备注：一个 App 需要同时支持 iOS 和 Android 平台，则必须单独申请各自的 appKey，并同时配置在 config 文件中,android渠道和ios渠道分别标注。如非双平台APP，则只需写入一组参数，即：android平台的android_appkey和android_channel;ios平台的ios_appkey和ios_channel。
- 配置示例:

```js
<feature name="baiduMTJ">
   <param name="android_appkey" value="f7344363432as" />
   <param name="ios_appkey" value="81qz3dBY3432" />       
   <param name="android_channel" value="apicloud" /> 
   <param name="ios_channel" value="appstore" /> 
</feature>
```

- 字段描述:

		1. android_appkey：通过百度移动统计网站获得Android系统的key
		2. ios_appkey:通过百度移动统计网站获得iOS系统的key
		3. ios_channel: IOS渠道号
		4. android_channel: Android的渠道号

#**init**<div id="1"></div>

模块初始化

init({parmas}, callback(ret, err))

##params

appid：

- 类型：字符串
- 描述：（可选项）从百度申请的appKey，注意android和ios的key是不同的，在使用前需判断手机操作系统，以免错误统计。若不传则从 confgi.xml 文件内读取相关字段

path：

- 类型：字符串
- 描述：（可选项）app发布路径或渠道名称，自定义渠道名称(无需申请)后在统计时加以分别。若不传则从 confgi.xml 文件内读取相关字段


##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
   status:       //布尔类型；是否成功
   msg:          //JSON对象；初始化成功后得到SDK版本（IOS不返回版本号）            
}
```

##示例代码

```js
  //1、未配置 config.xml 中的参数时使用如下代码
  var baiduMTJ = api.require('baiduMTJ');
  baiduMTJ.init({
      appid:'e98dje263d',
      path:'google'
  },function(ret,err){
      if(ret){
          alert(JSON.stringify(ret));
      }else{
          alert(JSON.stringify(err));
      }
  });
  //2、已配置 config.xml 中的参数时可使用如下代码
  var baiduMTJ = api.require('baiduMTJ');
  baiduMTJ.init({},function(ret,err){
      if(ret){
          alert(JSON.stringify(ret));
      }else{
          alert(JSON.stringify(err));
      }
  });
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**onEvent**<div id="2"></div>

自定义事件统计，可将APP中需要统计的事件先在百度移动统计的应用中进行设定，然后把设定的事件ID写入方法中，并自定义一个标签用以区别相同事件。

onEvent({parmas}, callback(ret, err))

##params

eventid：

- 类型：字符串
- 描述：在百度移动统计平台中的应用内设置的自定义事件ID，必须一一对应，否则统计失败。

label：

- 类型：字符串
- 描述：自定义的事件标签，用于统计事件的细微操作。


##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
   status:      //布尔类型；是否成功
   msg:         //JSON对象；事件触发成功               
}
```


##示例代码

```js
var baiduMTJ = api.require('baiduMTJ');
baiduMTJ.onEvent({ 
  eventid:'buy',
  label:'open'       
}, function(ret, err){   
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**onPageStart**<div id="3"></div>

自定义页面统计开始，与`onPageEnd`成对使用，在页面打开时调用此方法，如页面不需要统计，则无需调用此方法。
  
**注意：本方法不会随页面打开自动调用，一定要在页面的初始化中写入。**

onPageStart({parmas}, callback(ret, err))

##params

pagename：

- 类型：字符串
- 描述：自定义的页面名称，统计开始和结束统计的页面名称必须一致。


##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
   status:        //布尔值，是否获取用户信息成功
   msg:           //JSON对象，页面统计开始
}
```

##示例代码

```js
var baiduMTJ = api.require('baiduMTJ');
baiduMTJ.onPageStart({
  pagename:'main',
}, function(ret, err){   
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**onPageEnd**<div id="4"></div>

自定义页面统计结束，与`onPageStart`成对使用，单独使用无效，在页面关闭前调用。
  
**注意：本方法不会随页面关闭自动调用，需要写在关闭页面的api.closeWin()或api.closeFrame()方法前有效。**

onPageEnd({parmas}, callback(ret, err))

##params

pagename：

- 类型：字符串
- 描述：自定义的页面名称，统计开始和结束统计的页面名称必须一致。


##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
   status:        //布尔值，是否获取用户信息成功
   msg:           //JSON对象，页面统计开始
}
```

##示例代码

```js
var baiduMTJ = api.require('baiduMTJ');
baiduMTJ.onPageEnd({
    pagename:'main',
}, function(ret, err){   
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本