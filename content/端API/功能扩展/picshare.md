/*
Title: picshare
Description: 打开自定义浏览页面下载分享.
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">方法</a></li>
</ul>
<div id="method-content">

<div class="outline">

[startActivityForResult](#startActivityForResult)

</div>

# 概述 #

本模块打开自定义浏览页面下载分享。

## startActivityForResult(params, callback(ret, err))<div id="startActivityForResult"></div>
打开设置密码页面

startActivityForResult ({params}, callback(ret, err))

## params ##
url：

- 类型：字符串
- 默认值：无
- 描述：需要分享的网络图片路径

## callback(ret, err) ##
ret：

- 类型：fxurl

- 描述：要分享的图片网址


### 示例代码 ###

```js
		var uzmoduledemo = null;
		apiready = function(){
		
	    	uzmoduledemo = api.require('picshare');
	    }
		
		function startActivityForResult(){ 
	
		    var param = {url:"http://www.chxx.cn/Uploads/54b3a2de281cf.png,http://www.chxx.cn/Uploads/54b3a325b8a90.png,http://www.chxx.cn/Uploads/54b3a345d0b22.png,http://www.chxx.cn/Uploads/54b3a360a4bc8.png,http://www.chxx.cn/Uploads/54b3a37d214fa.png,http://www.chxx.cn/Uploads/54b3a3cfcd13c.png,http://www.chxx.cn/Uploads/54b3a3eb24433.png"}
			var resultCallback = function(ret, err){
				     JSON.stringify(err);
			}
	        uzmoduledemo.startActivityForResult(param, resultCallback);
		}
```


### 补充说明 ###



### 可用性 ###

android系统

可提供的1.0.0及更高版本