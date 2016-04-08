/*
Title: alldk_jh
Description: alldk_jh
*/


<div class="outline">

[registerKey](#a1)

[getBannerAD](#a2)

[removeBannerAD](#a4)

[getIntAD](#a5)

[getSplashAD](#a6)

</div>
 

## 概述
   
   *dkSDK*封装了点开广告平台的SDK，使用此模块可轻松实现添加广告到应用的功能,根据需求放置调用的位置。 

<div id="a1"></div>

## registerKey:

注册key:

开发者需要在[点开](http://www.alldk.com/index.php?action=main.register)注册key,注册成功后才能使用模块

registerKey();
##params   

DIANKAI_APP_KEY:

 - 类型：String  
 - 描述：此字段为开发者在点开平台申请的横幅广告的使用KEY

DIANKAI_INTAD_KEY:

 - 类型：String  
 - 描述：此字段为开发者在点开平台申请的插屏广告的使用KEY

DIANKAI_BANNER_KEY:

 - 类型：String  
 - 描述：此字段为开发者在点开平台申请的横幅广告的使用KEY


##示例代码

 ```
   	var dkapi = api.require('alldkJH');
   	function registerKey(){ 	
     	var param = {DIANKAI_APP_KEY:"YOUR_APPKEY",
     		DIANKAI_INTAD_KEY:"YOUR_INTAD_KEY", 
			DIANKAI_SPLASH_KEY:"YOUR_SPLASH_KEY",
     		DIANKAI_BANNER_KEY:"YOUR_BANNER_KEY"};	 
     	dkapi.registerKey(param); 		
     } 
 ```    	
##字段描述：
    		1、YOUR_APPKEY：此字段为开发者在点开平台申请的APPKEY,类型:String
   		 	2、YOUR_INTAD_KEY：此字段为开发者在点开平台申请的插屏广告的使用KEY,类型:String
			3、YOUR_BANNER_KEY：此字段为开发者在点开平台申请的横幅广告的使用KEY,类型:String
##注意:
			把value中的值替换成点开平台申请的key
    	
##可用性: 

android 

<div id="a2"></div>   

##getBannerAD

banner广告展示(展示之前先要注册key)

getBannerAD(params);
## params

w:

- 类型:String
- 默认值:铺满屏幕
- 描述:宽度设置,用于设置宽度


x:

- 类型:String
- 默认值:0
- 描述:banner左上角横坐标

y:

- 类型:String
- 默认值:0
- 描述:banner左上角纵坐标

##示例代码:
```		
		function getBannerAD(){ 			
		var param = {w:"400",x:"170",y:"0"};
		
		dkapi.getBannerAD(param);
		}		
	
```		
##可用性:

android 系统 



		
<div id="a4"></div>	

##removeBannerAD
	
移除广告
 
removeBannerAD();

##params

msg:

- 类型:String
- 默认值:无
- 描述:无意义
    
##示例代码:
```
    function removeBannerAD (){ 
    		var par = {msg:"Hello diankai!"};
    		dkapi.removeBannerAD(par); 		
    }
```

##可用性:

android 系统


<div id="a5"></div>  
  
##getIntAD

插屏广告展示

getIntAD();

##params

msg

- 类型:String

    	
##示例代码:

```
		function getIntAD(){
    		var param = {msg:"Hello diankai!"};
    		dkapi.getIntAD(param);
  		}
```

##可用性:

android


<div id="a6"></div>  
		
##getSplashAD

开屏广告展示

getSplashAD();

##params

msg

- 类型:String	
    
##示例代码:
```
		function getSplashAD(){
    		var param = {msg:"Hello diankai!"};
    		dkapi.getSplashAD(param);
  		}

```

##可用性:

android
		
警告:调用广告之前 必须先执行注册key