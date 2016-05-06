/*
Title: umengTJ
Description: umengTJ
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：开发者</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>

<div id="method-content" />

<div class="outline">
[init](#a1)
[onEvent](#a2)
[onPageStart](#a3)
[onPageEnd](#a4)
</div>

#**概述**

umengTJ实现了友盟统计功能，包括启动次数、事件、页面等app数据的统计，使用此模块之前需要先去 [http://www.umeng.com/users/sign_up](http://www.umeng.com/users/sign_up) 注册用户，然后增加新的应用获取appkey用于统计。

**使用此模块之前可以配置  config 文件来设置appkey和渠道号，（如不进行配置，则一定要在init方法中做相关配置）配置方法如下：**

- 名称：umengTJ
- 参数：android_appkey、ios_appkey、android_channel、ios_channel
- 备注：一个 App 需要同时支持 iOS 和 Android 平台，则必须单独申请各自的 appKey，并同时配置在 config 文件中,android渠道和ios渠道分别标注。如非双平台APP，则只需写入一组参数，即：android平台的android_appkey和android_channel;ios平台的ios_appkey和ios_channel。
- 配置示例:


      <feature name="umengTJ">
       <param name="android_appkey" value="#########" />
       <param name="ios_appkey" value="**********" />       
       <param name="android_channel" value="apicloud" /> 
       <param name="ios_channel" value="appstore" /> 
      </feature>
   

- 字段描述:

		1. android_appkey：通过百度移动统计网站获得Android系统的key
		2. ios_appkey:通过百度移动统计网站获得iOS系统的key
		3. ios_channel: IOS渠道号
		4. android_channel: Android的渠道号



#如何获取友盟appkey

  - 注册应用，首先登录友盟统计

![image](http://www.sihee.com.cn/h/11.png)

然后添加新应用，如是多平台的，需要按平台申请多个应用。

![image](http://www.sihee.com.cn/h/12.png)

#**init**<div id="a1"></div>

模块初始化，所有统计方法都需要在init后被调用，所以init方法一般放在首页面的apiready函数中。

init({params}, callback(ret, err))

##params

appid：

- 类型：字符串
- 描述：（可选项）从友盟申请的appKey，注意android和ios的key是不同的，在使用前需判断手机操作系统，以免错误统计。

path：

- 类型：字符串
- 描述：（可选项）app发布路径或渠道名称，自定义渠道名称(无需申请)后在统计时加以分别。

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：


   
   { 

     status:       布尔类型；是否成功

     msg:          JSON对象；初始化成功后得到消息
                  
   }


err：

- 类型：JSON 对象
- 内部字段：


```js
  { 
     status:       //布尔类型；是否成功
     msg:          //JSON对象；初始化成功后得到消息             
  }
```


##示例代码

     ```js
      //如在 config.xml 配置了key和channel，则调用本方法可忽略appid和path参数
        var  umeng = api.require('umengTJ');//调用统计模块初始化，一般在app首页面调用
			 umeng.init({
			// appid:'56eba8b4e0f55acc430000a1',
			// path:'iosapp'
			 }, function(ret, err){ //通过 config.xml 配置appid
             if(ret.status){
                alert(JSON.stringify(ret));
             }else{
                alert(JSON.stringify(err));
            }
            });     
     ```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**onEvent**<div id="a2"></div>

触发自定义事件，需要提前在统计平台上定义事件


onEvent(params,callback(ret, err))

init({params}, callback(ret, err))


##params

eventid：

- 类型：字符串
- 描述：事件ID，与你在友盟中定义的id要一致，id不要是中文的，以免产生乱码。

labelkey：

- 类型：字符串
- 描述：事件参数，每个自定义事件可以有10个参数，
- ####本参数无需预先在平台上定义。

labelvalue：

- 类型：字符串
- 描述：参数取值，每个参数可以有1000个取值，
- ####本参数值无需在平台上预先定义。

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

     ```js
      {
       status:ture		//操作成功状态值，字符串类型
      }
      ```

##示例代码

      ```js
     var umeng = api.require('umengTJ');
         umeng.onEvent({
          eventid:'2',           //自定义事件ID
          labelkey:'money',      //自定义事件的参数
          labelvalue:'12.00'     //自定义事件的参数值
                  },function(ret, err){
                    if(ret.status){
                       alert(JSON.stringify(ret));
                    }else{
                        alert(JSON.stringify(err));
                  }
            });```

##补充说明

事件ID、参数、参数值在平台中的显示如下：


![image](http://www.sihee.com.cn/h/13.png)

查看自定义事件明细后显示参数及参数值

![image](http://www.sihee.com.cn/h/14.png)

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**onPageStart**<div id="a3"></div>

自定义页面统计开始，与`onPageEnd`成对使用，在页面打开时调用此方法，如页面不需要统计，则无需调用此方法。
  
**注意：本方法不会随页面打开自动调用，一定要在页面的初始化中写入。**

onPageStart({parmas},callback(ret, err))

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

    var umeng = api.require('umengTJ');
        umeng.onPageStart({
        pagename:'main',
           },function(ret,err){
             if(ret){
               alert(JSON.stringify(ret));
             }else{
              alert(JSON.stringify(err));
           }
      });

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**onPageEnd**<div id="a4"></div>

自定义页面统计结束，与`onPageStart`成对使用，单独使用无效，在页面关闭前调用。
  
**注意：本方法不会随页面关闭自动调用，需要写在关闭页面的api.closeWin()或api.closeFrame()方法前有效。**

onPageEnd({parmas},callback(ret, err))

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
   msg:           //JSON对象，页面统计开始}
```

##示例代码

    var umeng = api.require('umengTJ');
        umeng.onPageEnd({
           pagename:'main',
             },function(ret,err){
               if(ret){
                 alert(JSON.stringify(ret));
               }else{
                 alert(JSON.stringify(err));
             }
     });

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本