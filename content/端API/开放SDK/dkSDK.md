/*
Title: dkSDK
Description: dkSDK
*/
<div class="outline">
[registerKey](#a1)

[getBannerAD](#a2)

[setHideDate](#a3)

[removeBannerAD](#a4)

[getIntAD](#a5)

</div>


## 概述
   
   *dkSDK*封装了点开广告平台的SDK，使用此模块可轻松实现添加广告到应用的功能,根据需求放置调用的位置。 

<div id="a1"></div>

## registerKey
		
注册key:开发者需要在http://www.alldk.com/index.php?action=main.register注册key,注册成功后才能使用模块

registerKey(params);
   	
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
   	
 ``` 
   var dkapi = api.require('dkSDK');
   	function registerKey(){ 	
     	var param = {DIANKAI_APP_KEY:"YOUR_APPKEY",
     		DIANKAI_INTAD_KEY:"YOUR_INTAD_KEY", 
     		DIANKAI_BANNER_KEY:"YOUR_BANNER_KEY"};	 
     	dkapi.registerKey(param); 		
     } 
  ```

##可用性: 
android ios系统 

<div id="a2"></div>   

##getBannerAD

banner广告展示(展示之前先要注册key)

getBannerAD(params);

## params

h:

- 类型:String
- 默认值:自适应
- 描述:高度设置,用于设置高度,

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

```		
		function getBannerAD(){ 			
		var param = {h:"100",w:"500",x:"100",y:"1000"};
		
		dkapi.getBannerAD(param);
		}		
		getBannerAD();

```
		
##可用性:
android 系统 


<div id="a3"></div> 	
	
##setHideDate

关闭插屏广告时间设置

setHideDate(params);


##params  
  
hideDate:

- 类型:Long
- 默认值:0 表示调用一次  用户点击取消,不再调用插屏广告
- 描述:经过多长时间再次调用广告,单位毫秒

```
		function setHideDate(){ 
    		var hideDate = {hideDate:"5000"};
				dkapi.setHideDate(hideDate);
    	} 
```


##可用性:
android 系统
    
<div id="a4"></div> 
    
##removeBannerAD	

移除广告 

removeBannerAD(params);
    
- msg:
- 类型:String
- 描述:移除广告
    
```
    function removeBannerAD (){ 
    		var par = {msg:"Hello diankai!"};
    		dkapi.removeBannerAD(par); 		
    }
```

##可用性:
android ios系统
 
<div id="a5"></div> 
   
##getIntAD

插屏广告展示

getIntAD(params);

##params 
	
height:

- 类型:String
- 描述:ios设置int广告的高度,android 已经实现了根据屏幕自适应可任意填写

width:
    
- 类型:String
- 默认值:android默认值为0.9,表示插屏宽度占屏幕宽度的90%,ios默认为宽式屏幕.
- 描述:ios设置int广告的宽度和高度,android 已经实现了根据屏幕自适应可任意填写
   
```    	
function getIntAD(){
    		var param = {height:"200", width:"320"};
    		dkapi.getIntAD(param);
  		}
```

##可用性:
android ios系统
		
警告:调用广告之前 必须先执行注册key