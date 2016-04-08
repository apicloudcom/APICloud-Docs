/*
Title: tencentMTA
Description: tencentMTA
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">方法</a></li>
</ul>
<div id="method-content">
<div class="outline">
[init](#init)
[onEvent](#onEvent)
[onPageStart](#onPageStart)
[onPageEnd](#onPageEnd)
</div>

#**概述**
   
   tencentMTA 封装了腾讯统计平台的SDK，使用此模块可实现APP统计的功能。
   在使用前需要在腾讯统计平台进行注册账号[http://mta.qq.com](http://mta.qq.com)   
####    *config.xml参数配置*
使用模块前可以配置相关key和channel参数，如不愿配置的，也可在初始化时传入参数进行配置。

    <feature name="tencentMTA">
        <param name="android_appkey" value="*********"/>
        <param name="android_channel" value="apicloud"/>
        <param name="ios_appkey" value="*********"/>
        <param name="ios_channel" value="appstore"/>
    </feature>
参数注明：

1、android_appkey:你申请的android平台应用的app key

2、android_chanel:你自定义的android渠道号

3、ios_appkey:你申请的ios平台应用的app key

4、ios_chanel:你自定义的ios渠道号

#APPKEY申请步骤
![image](http://www.sihee.com.cn/h/1.png)


用 QQ号登陆平台，申请新应用：


![image](http://www.sihee.com.cn/h/2.png)  

新建应用，记录相应的key
 
 ![image](http://www.sihee.com.cn/h/3.png)

![image](http://www.sihee.com.cn/h/4.png)


## **自定义事件**


需要有事件统计的，请先进行事件定义：

![image](http://www.sihee.com.cn/h/5.png)

## **页面统计**

页面统计只要统计页面ID及时长，后台可预先定义页面id及页面名称，也可不定义，而通过pagename参数传入页面ID。

**注意点：onPageStart与onPageEnd必须成对使用，pagename在一个页面中也必须一致，如不使用onPageStart，则后台不会自动统计页面**

统计后台对页面统计的数据反映在12个小时左右，所以触发方法后隔天才能看到数据。

![image](http://www.sihee.com.cn/h/21.png)

#**init**<div id="init"></div>
模块初始化.

init(params,callback(ret));

##params

appid:

-	类型：字符串
-	描述：（可选项）开发者在腾讯统计平台申请的APPKEY，若不传则读取config.xml里的参数


path:

-	类型：字符串
-	描述：（可选项）开发者自定义的通道号，若不传则读取config.xml里的参数

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
   {
     status:       //布尔类型；是否成功
     msg:          //JSON对象；初始化成功后得到消息             
   }
```

##示例代码

 ```js
    var mta = api.require('tencentMTA');
         mta.init({
           appid:'申请的key',
           path:'自定义通道'          
         },function(ret){
             if(ret.status){
                  alert(JSON.stringify(ret));
                } 
         });
 ```

##补充说明

开发者如在config.xml中配置了appkey和channel的，可不填写参数，直接init 

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**onEvent**<div id="onEvent"></div>

统计自定义事件的一次触发，使用前需要到统计后台定义时间id及详细参数。

onEvent(params,callback(ret, err));

##params

eventid:

-	类型：字符串
-	描述：平台上自定义事件对应的事件ID

labelkey:

-	类型：字符串
-	描述：事件参数配置中的参数

labelvalue:

-	类型：字符串
-	描述：事件参数配置中的参数名称

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
 {
    status:ture		//布尔类型；操作成功状态值
 }
```


##示例代码

```js
      var mta = api.require('tencentMTA');
          mta.onEvent({
             eventid:'1',
             labelkey:'subit',
             labelvalue:'提交'
          },function(ret){
                if(ret.status){
                  alert(JSON.stringify(ret));
                }
          });
```

##补充说明

事件ID（eventid）

![image](http://www.sihee.com.cn/h/6.png)

事件参数（labelkey）和参数名称（labelvalue）

![image](http://www.sihee.com.cn/h/7.png)

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**onPageStart**<div id="onPageStart"></div>

自定义页面统计触发开始，本方法与下面的onPageEnd方法成对使用，其中的pagename参数必须一致，否则无法统计页面使用时间。

onPageStart(params,callback(ret));

##params

pagename:

-	类型: 字符串
-	描述:自定义的页面名称，不需要预先在平台中定义，当然如果定义了也没问题

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
   status:        //布尔类型；是否获取用户信息成功
   msg:           //JSON对象；页面统计开始
}
```

##示例代码

```js
       var mta = api.require('tencentMTA');
           mta.onPageStart({
               pagename:'开始页面'
           },function(ret){
               if(ret.status){
                  alert(JSON.stringify(ret));
               }
          });
```

##补充说明

页面统计为非实时性统计，一般在app调用方法后12小时内，统计后台反应统计数据，所以在短时间内页面统计数据无变化是正常现象。

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**onPageEnd**<div id="onPageEnd"></div>

自定义页面统计结束，与onPageStart方法配对使用，其中pagename参数必须一致。

onPageEnd(params,callback(ret));

##params

pagename:

-	类型: 字符串
-	描述:自定义的页面名称，不需要预先在平台中定义，当然如果定义了也没问题


##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
   status:        //布尔类型；是否获取用户信息成功
   msg:           //JSON对象；页面统计开始
}
```

##示例代码

```js
     var mta = api.require('tencentMTA');
         mta.onPageEnd({
             pagename:'开始页面'
         },function(ret){
             if(ret.status){
                alert(JSON.stringify(ret));
             }
         });
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


