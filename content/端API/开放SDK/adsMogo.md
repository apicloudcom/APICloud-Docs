/*
Title: adsMogo
Description: adsMogo
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">


<div class="outline">
[initBanner](#a1)

[hiddenBanner](#a2)

[showBanner](#a3)

[setLog](#a4)

[setListener](#a5)

[initInterstitial](#a6)

[showInterstitial](#a7)

[setLog](#a8)

[setListener](#a9)

[cancelWaitShow](#a10)
</div>

#**概述**

芒果移动广告优化平台是中国最大的移动广告优化及交易平台,通过与70余家广告平台、DSP平台以及广告交易平台合作,为开发者降低广告管理成本并大幅提升广告收入，本模块封装了芒果SDK，只需简单调用几个接口即可实现对广告平台的集成。

注意：由于芒果联盟的特殊性，本模块采用拆分的机制，减少编译的安装包的冗余。所以，在使用相关平台时，需要在勾选本模块的基础上，再勾选相应的平台模块。
adsMogoBaidu

注意：adsMogo，及其所属的adsMogoDomob，adsMogoInMobi，，adsMogoGDT 子模块，SDK版本过旧。暂未有更新计划。建议使用其他广告模块。 


#**Banner接口**

#**initBanner**<div id="a1"></div>

初始化Banner

initBanner({params},callback(ret,err))

##params

mogoId：

- 类型：字符串
- 默认值：无
- 描述：芒果后台创建APP后，会生成一个芒果ID，用于获取配置信息，不可为空

position：

- 类型：字符串
- 默认值：center_bottom
- 描述：广告位置[详情Banner位置](!Constant)，可为空

adsize：

- 类型：数字
- 默认值：0
- 描述：请求广告尺寸[详情Banner尺寸](!Constant)，可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true		//操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:“”    //错误描述
}
```

##示例代码

```js
var adsMogoBanner = api.require('adsMogoBanner');

adsMogoBanner.initBanner({
    mogoId:"5a10bcead61141689daf08c5fdd3426c",
    position:"center_bottom",
    adsize:0
},function(ret,err){
    if(ret.status){
        api.alert({msg:"调用广告初始化成功"});
    }else{
        api.alert({msg:"调用广告初始化失败msg:"+err.msg});
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**hiddenBanner**<div id="a2"></div>

隐藏Banner

hiddenBanner(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true           //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:“”    //错误描述
}
```

##示例代码

```js
var obj = api.require('adsMogoBanner');

obj.hiddenBanner(function(ret, err){
    if(ret.status){
        api.alert({msg:'调用隐藏广告成功'});
    }else{
        api.alert({msg:'调用隐藏广告失败msg+err.msg'});
    }
});
```

##补充说明

隐藏Banner

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**showBanner**<div id="a3"></div>

显示Banner

showBanner(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:           //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:””//错误描述
}
```

##示例代码

```js
var obj = api.require('adsMogoBanner');

obj.showBanner(function(ret, err){
	if(ret.status){
		api.alert({msg:'调用展示广告成功'});
    }else{
		api.alert({msg:'调用展示广告失败msg+err.msg'});
    }
});
```

##补充说明

显示Banner

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setLog**<div id="a4"></div>

设置Log

setLog({params}, callback(ret, err))

##params

debug：

- 类型：布尔值
- 默认值：false
- 描述：开启关闭日志，可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:           //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:”” //错误描述
}
```

##示例代码

```js
var obj = api.require('adsMogoBanner');

obj.setLog({
    debug:true
},function(ret, err){
    if(ret.status){
        api.alert({msg:'设置日志成功'});
    }else{
        api.alert({msg:'设置日志失败msg+err.msg'});
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setListener**<div id="a5"></div>

设置回调监听

setListener(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	name:			//事件名称（详情见Banner监听回调名称）
	value：         //广告平台名称
}
```

##示例代码

```js
var obj = api.require(' adsMogoBanner ');

obj.setListener(function(ret, err){
    if(ret.name == 'onRequestAd'){
        api.alert({msg:"开始请求广告"});
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**全插屏接口**

#**initInterstitial**<div id="a6"></div>

初始化全插屏

initInterstitial({params},callback(ret,err))

##params

mogoId：

- 类型：字符串
- 默认值：无
- 描述：芒果后台创建APP后，会生成一个芒果ID，用于获取配置信息，不可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:       //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:“”      //错误描述
}
```

##示例代码

```js
var adsMogoBanner = api.require('adsMogoInterstitial');
adsMogoBanner.initInterstitial({
	mogoId:"5a10bcead61141689daf08c5fdd3426c"
},function(ret,err){
	if(ret.status){
		api.alert({msg:"调用插屏广告初始化成功"});
	}else{
		api.alert({msg:"调用插屏广告初始化失败msg:"+err.msg});
	}
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**showInterstitial**<div id="a7"></div>

显示Banner

showInterstitial({params},callback(ret, err))

##params

isWait：

- 类型：布尔值
- 默认值：true
- 描述：true等待广告请求成功后展示广告，false不等待广告请求直接展示

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:           //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:””           //错误描述
}
```

##示例代码

```js
var obj = api.require('adsMogoInterstitial');

obj.showInterstitial(function(ret, err){
	if(ret.status){
		api.alert({msg:'调用展示广告成功'});
    }else{
		api.alert({msg:'调用展示广告失败msg+err.msg'});
    }
});
```

##补充说明

显示Banner

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setLog**<div id="a8"></div>

设置Log

setLog({params}, callback(ret, err))

##params

debug：

- 类型：布尔值
- 默认值：false
- 描述：开启关闭日志，可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:           //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:””          //错误描述
}
```

##示例代码

```js
var obj = api.require('adsMogoInterstitial');

obj.setLog({
    debug:true
},function(ret, err){
    if(ret.status){
        api.alert({msg:'设置日志成功'});
    }else{
        api.alert({msg:'设置日志失败msg+err.msg'});
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setListener**<div id="a9"></div>

设置回调监听

setListener(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	name:          //事件名称（详情见全插屏回调名称）
	value：         //广告平台名称
}
```

##示例代码

```js
var obj = api.require('adsMogoInterstitial');

obj.setListener(function(ret, err){
    if(ret.name == 'onShowInterstitialScreen'){
        api.alert({msg:"全插屏展示到屏幕上"});
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**cancelWaitShow**<div id="a10"></div>

取消等待展示

cancelWaitShow(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

##内部字段：

```js
{
	status:true           //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:“”    //错误描述
}
```

##示例代码

```js
var obj = api.require('adsMogoInterstitial');

obj.cancelWaitShow(function(ret, err){
    if(ret.status){
        api.alert({msg:'调用取消等待展示成功'});
    }else{
        api.alert({msg:'取消等待展示msg+err.msg'});
    }
});
```

##补充说明

隐藏Banner

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


</div>

<div id="const-content">
<div class="outline">
[Banner 广告位置](#a100)

[Banner 广告尺寸](#a101)

[Banner 监听回调名称](#a102)

[全插屏监听回调名称](#a103)
</div>

#**Banner 广告位置**<div id="a100"></div>

广告视图的位置。字符串类型

##取值范围：

- left_top		//上居左
- center_top		//上居中
- right_top		//上居右
- left_bottom		//下居左
- center_bottom		    //下居中
- right_bottom		//下居右

#**Banner 广告尺寸**<div id="a101"></div>

广告视图的大小。数字类型

##取值范围：

- 0		     //尺寸320*50
- 1		        //尺寸468*60
- 2		//尺寸728*90
- 3		//尺寸自适应


#**Banner 监听回调名称**<div id="a102"></div>

监听回调名称。字符串类型

##取值范围：

- onRequestAd//开始请求广告
- onReceiveAd //请求广告成功
- onRealClickAd//点击广告(每次点击)
- onInitFinish//初始化广告完成
- onFailedReceiveAd//请求广告失败
- onCloseMogoDialog//关闭下载类广告简介
- onCloseAd//关闭广告
- onClickAd//点击广告(一条广告只触发一次)


#**全插屏监听回调名称**<div id="a103"></div>

监听回调名称。字符串类型

##取值范围：

- onShowInterstitialScreen //广告展示在屏幕上
- onInterstitialStaleDated //广告过期
- onInterstitialRealClickAd //点击广告(每次点击)
- onInterstitialCloseAd//关闭广告
- onInterstitialClickCloseButton//点击关闭按钮关闭广告
- onInterstitialClickAd//点击广告
- onInitFinish//初始化广告完成

</div>