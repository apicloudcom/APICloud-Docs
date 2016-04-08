/*
Title: umengAnalytics
Description: umengAnalytics
*/

<div class="outline">
[init](#a1)

[onPageStart](#a2)

[onPageEnd](#a3)

[onEvent](#a4)

[profileSignIn](#a5)

[profileSignOff](#a6)

[testDeviceID](#a7)
</div>

#**概述**

umengAnalytics 模块封装了[友盟](http://www.umeng.com/analytics)APP统计SDK。它能帮助移动应用开发商统计和分析流量来源、内容使用、用户属性和行为数据，以便开发商利用数据进行产品、运营、推广策略的决策。

#**模块使用攻略**

**1. 注册帐号**

使用本模块之前需先到友盟注册账号。注册地址为：[http://www.umeng.com/users/sign_up](http://www.umeng.com/users/sign_up)

**2. 创建应用**

分别添加 Android 和 iOS 两个平台的应用，创建时请选择**标准统计分析**，创建地址为：[http://www.umeng.com/apps/new](http://www.umeng.com/apps/new)

**3. 添加自定义事件**

如果需要自定义事件统计，需进入应用，然后点击 设置 => 事件 => 添加事件 。[自定义事件功能说明](http://dev.umeng.com/analytics/functions/numekv)

**4. 配置 APICloud 项目的 config.xml 文件**

- 名称：umengAnalytics
- 参数：

     **ios_app_key：**iOS应用的 appkey

    **ios_app_channel：**（可选项）iOS应用的渠道名称。名称可自定义，去掉这一项的话将使用平台默认渠道名称

    **android_app_key：**Android应用的 appkey

    **android_app_channel：**（可选项）Android应用的渠道名称。名称可自定义，去掉这一项的话将使用平台默认渠道名称
- 备注：同一个 App 需要同时支持 iOS 和 Android 平台，必须在友盟平台分别创建 iOS 和 Android 的两个标准模式的统计分析应用，并同时配置在 config.xml 文件中；若要移除本模块，需要先删除 config.xml 中的配置项，提交代码到云端后方可在控制台的模块栏目移除。
- 配置示例:
```
<feature name="umengAnalytics">
    <param name="ios_app_key" value="56ea6ab0e0f45a2b3b000260"/>
    <param name="ios_app_channel" value="APICloud_iOS"/>
    <param name="android_app_key" value="562a6707e3f554ae02402144"/>
    <param name="android_app_channel" value="APICloud_Android"/>
</feature>
```

**4. 添加模块**

如果此时已正确配置了 config.xml 文件，那提交代码到 APICloud 云端后，umengAnalytics 模块将会自动添加到你的项目中。云编译或者通过 APICloud Studio 自定义loader 模块即可生效。

**5. 集成测试**

先初始化本模块，初始化时 ```debugMode``` 设为 ```true``` ， 然后再调用模块的 [testDeviceID](#a7) 接口来获取设备识别信息。最后打开[测试设备](http://www.umeng.com/test_devices)页面添加设备，把上面获取的设备识别信息填进去。关于集成测试的相关说明请[点击这里](http://dev.umeng.com/analytics/functions/testmode)。

**6. 启动次数的统计原理**

Android平台一次完整的启动包括如下三种情况：

 1. 从启动应用到关闭应用；
 2. 从启动应用到应用退至后台，且在后台运行时间超过30s；
 3. 启动应用后设备黑屏，黑屏时间超过30s；

iOS平台一次完整的启动包括如下两种情况：

 1. 从启动应用到关闭应用；
 2. 从启动应用到应用退至后台，此种情况iOS与Android不同，iOS只要退至后台就算本次启动的结束；

**7. 其他问题和说明**

 1. [友盟统计常见问题索引](http://bbs.umeng.com/thread-5421-1-1.html)；
 2. 由于苹果的App Store禁止不使用广告而采集IDFA的App上架，所以本模块的iOS版SDK使用的是不含IDFA的SDK，如果你需要包含IDFA的SDK模块，可以单独联系我。不过两个SDK在数据上并没有差异；
 3. 开发测试时，APP的统计信息是不会实时显示在后台统计报表中的，所以需要使用**集成测试**功能；
 4. 自定义页面统计的报表为什么没有数据，请[点击这里](http://bbs.umeng.com/thread-9166-1-1.html)；
 5. 为提高数据安全性，防止网络攻击，统计数据已加密上报；

#**模块接口**
下面时本模块的相关接口

<div id="a1"></div>
#**init**

模块初始化

init(callback(ret, err))

##params

debugMode:

- 类型：布尔类型
- 描述：使用平台的集成测试时，需开启调试模式
- 默认值：false

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true      //布尔型；true||false，操作是否成功
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    code: 1,                                 //错误码
    msg: "初始化失败，请配置 config.xml 文件"   //字符串类型；错误信息
}
```

##示例代码

```js
    // index.html
    apiready = function(){
        var umengAnalytics = api.require('umengAnalytics');
        umengAnalytics.init({
        	debugMode:false,
        },function(ret, err){
             if(ret.status){
                   //api.alert({msg: '友盟初始化成功'});
             }else{
                   api.alert({msg: err.code+' '+err.msg});
             }
        });
    }
```

##补充说明

为了数据统计完整，请在APP入口文件中执行。例如：APP入口文件是 index.html，则在 index.html 中执行模块初始化操作

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="a2"></div>
#**onPageStart**

自定义页面统计开始。与[onPageEnd](#a3)成对使用，在页面打开时调用此方法，如果页面不需要统计，则无需调用此方法

onPageStart({params}, callback(ret, err))

##params

pageName:

- 类型：字符串
- 描述：自定义的页面名称，统计开始和结束统计的页面名称必须一致

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true,                 //布尔型；true||false，操作是否成功
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    code: 2,                     //错误码；
	msg: "请设置 pageName"        //字符串类型；错误信息
}
```

##示例代码

```js
        var umengAnalytics = api.require('umengAnalytics');
        umengAnalytics.onPageStart({
            pageName:'列表页',
        },function(ret,err){
             if(ret.status){
                   //api.alert({msg: '开始统计自定义页面'});
             }else{
                   api.alert({msg: err.code+' '+err.msg});
             }
		});
```

##补充说明

调用此接口后，需要在同一页面调用[onPageEnd](#a3)方法。

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="a3"></div>
#**onPageEnd**

自定义页面统计结束。与[onPageStart](#a2)成对使用，单独使用无效，在页面关闭前调用

onPageEnd({params}, callback(ret, err))

##params

pageName:

- 类型：字符串
- 描述：自定义的页面名称，统计开始和结束统计的页面名称必须一致

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true      //布尔型；true||false，操作是否成功
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    code: 2,                 //错误码；
	msg: "请设置 pageName"    //字符串类型；错误信息
}
```

##示例代码

```js
	var umengAnalytics = null;
	// 点击界面中的返回按钮(图标)时结束自定义页面统计
    function closeWin(){
        onPageEnd();
        api.closeWin();
    }
	function onPageEnd(){
		umengAnalytics.onPageEnd({
			pageName:'列表页',
		},function(ret,err){
             if(ret.status){
                   //api.alert({msg: '结束统计自定义页面'});
             }else{
                   api.alert({msg: err.code+' '+err.msg});
             }
		});
	}
    apiready = function(){
        umengAnalytics = api.require('umengAnalytics');
		// ...此处省略 onPageStart 的代码....
        // iOS手势关闭页面时结束自定义页面统计
        api.addEventListener({
            name:'viewdisappear'
        },function(ret,err){
            onPageEnd()
        });
        // Android按返回键关闭页面时结束自定义页面统计
        api.addEventListener({
            name:'keyback'
        },function(ret,err){
        	closeWin();
        });
	};
```

##补充说明

调用此接口前，需要先在同一页面调用[onPageStart](#a2)方法。

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="a4"></div>
#**onEvent**

自定义事件统计，自定义事件可以实现在应用程序中埋点来统计用户的点击行为。自定义事件目前包括“计数事件”和“计算事件”，二者的区别以及详细说明请[点击这里](http://dev.umeng.com/analytics/functions/numekv)

onEvent({params}, callback(ret, err))

##params

eventId:

- 类型：字符串
- 描述：自定义事件id

attributes:

- 类型：JSON 类型
- 描述：（可选项）事件的属性和取值（Key-Value键值对）

counter:

- 类型：字符串
- 描述：（可选项）当前事件的数值。如果设置此参数，则必须设置 attributes 参数

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true            //布尔型；true||false，操作是否成功
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    code: 3,               //错误码；
			               //3（请设置 eventId）
			               //4（请设置 attributes）
	msg: "请设置 eventId"  //字符串类型；错误信息
}
```

##示例代码

```js
    var umengAnalytics = null;
    apiready = function () {
        umengAnalytics = api.require('umengAnalytics');
    }
    // 计数事件1：统计发生次数（只有 eventId 一个参数时）
	// 例：统计微博转发次数
    function forward(){
        umengAnalytics.onEvent({
             eventId: 'Forward',
        },function(ret, err){
             if(ret.status){
                   alert(JSON.stringify(ret));
             }else{
                   alert(JSON.stringify(err));
             }
        });
    }
    // 计数事件2：统计点击行为各属性被触发的次数（有 eventId、attributes 两个参数时）
    // 例：统计购买商品类型为book，数量为3本
    function purchase(){
        umengAnalytics.onEvent({
             eventId: 'Purchase',
             attributes: {
                    type: 'book',
                    quantity: '3'
             }
        },function(ret, err){
             if(ret.status){
                   alert(JSON.stringify(ret));
             }else{
                   alert(JSON.stringify(err));
             }
        });
    }
    // 计算事件：统计数值型变量的值的分布（有 eventId、attributes、 counter 三个参数时）
    // 统计书名为《APICloud入门》，付款金额为52元
    function pay(){
        umengAnalytics.onEvent({
             eventId: 'Pay',
             attributes: {
                    book: 'APICloud入门'
             },
             counter: 52,
        },function(ret, err){
             if(ret.status){
                   alert(JSON.stringify(ret));
             }else{
                   alert(JSON.stringify(err));
             }
        });
    }
```

##补充说明

[关于自定义事件的那些事儿](http://bbs.umeng.com/thread-11284-1-1.html) （可看使用部分的相关说明）

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="a5"></div>
#**profileSignIn**

账号统计：登录。友盟在统计用户时以设备为标准，如果需要统计应用自身的账号，请使用此接口

profileSignIn({params}, callback(ret, err))

##params

uid:

- 类型：字符串
- 描述：用户账号ID，长度小于64字节

provider:

- 类型：字符串
- 描述：（可选项）账号来源。如果用户通过第三方账号登陆，可以调用此接口进行统计。支持自定义，不能以下划线"_"开头，使用大写字母和数字标识，长度小于32 字节; 如果是上市公司，建议使用股票代码。

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true             //布尔型；true||false，操作是否成功
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    code: 6,               //错误码；
	msg: "请设置 uid"       //字符串类型；错误信息
}
```

##示例代码

```js
        var umengAnalytics = api.require('umengAnalytics');
        umengAnalytics.profileSignIn({
            uid:'8888',
            provider:"WeiBo"
        },function(ret,err){
             if(ret.status){
                  //api.alert({msg: '开始账号统计'});
             }else{
                  api.alert({msg: err.code+' '+err.msg});
             }
        });
```

##补充说明

如何[启动账号统计](http://dev.umeng.com/analytics/android-doc/integration#2_3_1)

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="a6"></div>
#**profileSignOff**

账号统计：退出。友盟在统计用户时以设备为标准，如果需要统计应用自身的账号，请使用此接口

profileSignOff(callback(ret, err))

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true            //布尔型；true||false，操作是否成功
}
```

##示例代码

```js
        var umengAnalytics = api.require('umengAnalytics');
        umengAnalytics.profileSignOff(function(ret){
			if(ret.status){
				//api.alert({msg: '结束账号统计'});
			}
        });
```

##补充说明

如何[启动账号统计](http://dev.umeng.com/analytics/android-doc/integration#2_3_1)

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="a7"></div>
#**testDeviceID**

获取测试设备ID

testDeviceID(callback(ret, err))

##callback(ret, err)

ret：

- 类型：字符串类型
- 描述：在平台上添加测试设备时要求的JSON格式字符串

err：

- 类型：JSON对象
- 内部字段：

```js
{
    code: 5,                  //错误码；
	msg: "deviceID获取失败"    //字符串类型；错误信息
}
```

##示例代码

```js
        var umengAnalytics = api.require('umengAnalytics');
        umengAnalytics.testDeviceID(function(ret, err){
             if(ret){
                   api.alert({msg: '测试设备识别信息：' + ret});
                   console.log('测试设备识别信息：' + ret);
             }else{
                   api.alert({msg: err.code+' '+err.msg});
             }
        });
```

##补充说明

如何使用平台的[集成测试](http://dev.umeng.com/analytics/functions/testmode)

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本