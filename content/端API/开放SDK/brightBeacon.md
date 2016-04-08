/*
Title: brightBeacon
Description: brightBeacon
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
   
<div id="method-content"></div>

<div class="outline">

[registerAppKey](#a1)

[startRanging](#a2)

[stopRanging](#a3)

[startMonitoring](#a4)

[stopMonitoring](#a5)

[sendLocalNotification](#a6)

[startAdvertising](#a7)

[stopAdvertising](#a8)

[connectBeacon](#a9)

[disconnectBeacon](#a10)

[isBeaconConnected](#a11)

[writeBeaconValues](#a12)

[checkBeaconFirmwareUpdate](#a13)

[updateBeaconFirmwareWithProgress](#a14)

[resetBeacon](#a15)

[resetBeaconAppKey](#a16)

[monitorRegions](#a17)

</div>

#概述
---
>brightBeacon是一个基于Web的API库，以便与iBeacon设备互动。该SDK安装要求IOS6.0+iPhone4s以上、Android4.3及以上支持蓝牙低功耗（BLE）的设备。
>brightBeacon是[智石网络科技有限公司](http://www.brtbeacon.com)提供给开发者使用的API库。

　
>

##<div id="a1"></div>registerAppKey
---
初始化应用AppKey
registerAppKey(params,callback(ret,err))

####params
key：

- 类型：字符串
- 描述：[BrightBeacon开发者中心](http://sdk.brtbeacon.com:8183)创建APP后，会生成一个16位的APPKEY，用于获取配置信息和加密beacon设备，不可为空（默认可填写32个0）


####callback(ret, err)
ret：

- 类型：JSON对象

内部字段：

```
status:true/false        //操作成功、失败状态值
```

err：

- 类型：JSON对象

内部字段：

```
error:""    //错误描述
code:""    	//错误码
```

###示例代码

```
var bbsdk = api.require("brightBeacon");
bbsdk.registerAppKey({key:"00000000000000000000000000000000";},
   function(ret,err){
  	if(ret.status){
 		alert("调用初始化KEY成功");
  	}else{
  		alert(err.error});
   	}
   });
```

###补充说明
APPKEY用来标识不同应用的Beacon设备，同时对Beacon的连接进行加密，防止Beacon被恶意篡改
###可用性
iOS系统，Android系统

##<div id="a2"></div>startRanging

开启扫描周边Beacon
startRanging(params,callback(ret, err))

####params

uuids：

- 类型：JSON数组
- 默认值：无
- 描述：IOS需要传递UUID数组,来提高设备的RSSI精度和开启区域感知功能

####callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```
status:true/false           //操作状态值
list:[{"uuid":"","major":""...},{...},...]	//Beacon数组（详情见Beacon解释）
```

err：

- 类型：JSON对象

内部字段：

```
error:"错误详情"    //错误描述
```

###示例代码

```
var bb = api.require("brightBeacon");
bb.startRanging({uuids:["00000000-0000-0000-0000-000000000000","E2C56DB5-DFFB-48D2-B060-D0F5A71096E0"]},function(ret, err){
	if(ret.status){
		alert("调用开启扫描成功");
	}else{
		alert(err.error);
	}
	});
```
###补充说明

开启扫描周边Beacon，需要打开系统蓝牙（ios打开定位会获取更稳定的距离）

###可用性

iOS系统，Android系统

####<div id="a3"></div>stopRanging

---
关闭扫描周边Beacon
stopRanging(callback(ret, err))

####params

uuids：

- 类型：JSON数组
- 默认值：无
- 描述：IOS需要传递UUID数组

####callback(ret, err)
ret：

- 类型：JSON对象

内部字段：

```
status:true/false          //操作状态值
```
err：

- 类型：JSON对象

内部字段：

```
error:"错误详情"//错误描述
```

###示例代码

```
var obj = api.require("brightBeacon");
obj.stopRanging(function(ret, err){
if(ret.status){
alert("调用关闭扫描周边Beacon成功");
}else{
alert(err.error);
}
});
```
###补充说明

关闭扫描周边Beacon

###可用性

iOS系统，Android系统

####<div id="a4"></div>startMonitoring

开启区域监听

startMonitoring(params, callback(ret, err))

####params

uuid：

- 类型：字符串
- 默认值：无
- 描述：区域UUID

mac：

- 类型：字符串
- 默认值：无
- 描述：mac地址

major：

- 类型：整型
- 默认值：无
- 描述：Major

minor：

- 类型：整型
- 默认值：无
- 描述：Minor

in：

- 类型：整型
- 默认值：无
- 描述：描述：1监听进入区域状态 0 否

out：

- 类型：整型
- 默认值：无
- 描述：1监听离开区域状态 0否

display：

- 类型：整型
- 默认值：无
- 描述：1开启点亮屏幕检测该区域状态 0否

####callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```
status:true/false	//操作状态值
state：1/2        		//离开（进入）状态值
display:0/1       		//ios 是否是点亮屏幕
list:				//Beacon数组（详情见Beacon）
```

err：

- 类型：JSON对象

内部字段：

```
 error:"错误详情" //错误描述
```

###示例代码

```
//启动打开监听区域回调通道，使已监听区域有效
apiready = function(){
	BBSDK = api.require('brightBeacon');
	//所有区域监听回调都会是该回调出口
	BBSDK.startMonitoring(function(ret,err){
		if(ret.status){
		        if(ret.state){
		            var param = {"msg":(ret.state==1?"进入区域通知":"离开区域通知"),"action":"立即查看","userInfo":"自定义传输参数"};
		            BBSDK.sendLocalNotification(param,function(ret1,err1){
		                                        if(ret1.status){
		                                        	alert(JSON.stringify(ret1));
		                                        }else{
		                                        	alert(err1.error);
		                                        }
		                                        });
		        }
		    }else{
		        alert(err.error);
		    }
	});
};
```

```
//再次开启监听区域，但区域监听只会继续使用初次打开的通道出口。
	var obj = api.require("brightBeacon");
obj.startMonitoring({
   uuid:"E2C56DB5-DFFB-48D2-B060-D0F5A71096E0",
   mac:"xx:xx:xx:xx:xx:xx"
   major:1,
   minor:1，
   in:1,//ios进入区域检测
   out:1,//ios离开区域检测
   display:1//ios点亮屏幕区域检测
   },function(ret, err){
	   if(!ret.status)alert(err.error);}
});
```
###补充说明

1、请在apiready函数初始化该方法至少传人callback,以保证区域检测回调通道被打开，该callback即是整个区域监听回调的总方法，之后再次调用该方法传人的callback将不会接收区域监听回调 2、IOS区域监听上限为20个

###可用性

iOS系统，Android系统

##<div id="a5"></div>stopMonitoring

停止区域监听
stopMonitoring(params,callback(ret, err))

####params

uuid：

- 类型：字符串
- 默认值：无
- 描述：区域UUID

mac：

- 类型：字符串
- 默认值：无
- 描述：mac地址

major：

- 类型：整型
- 默认值：无
- 描述：Major

minor：

- 类型：整型
- 默认值：无
- 描述：Minor

####callback(ret, err)

ret：

- 类型：JSON对象

###示例代码

```
var obj = api.require("brightBeacon");
obj.stopMonitoring({
   uuid:"E2C56DB5-DFFB-48D2-B060-D0F5A71096E0",
   mac:"78:A5:6B:12:7B"
   major:1,
   minor:1
   },function(ret, err){
	 }
});
```
###补充说明

不传入任何参数即可以停止所有监听区域

###可用性

iOS系统，Android系统

####sendLocalNotification<div id="a6"></div>

发送通知并显示在通知栏
sendLocalNotification(params,callback(ret,err))

####params

action：

- 类型：字符串
- 默认值：无
- 描述：通知标题

msg：

- 类型：字符串
- 默认值：无
- 描述：通知内容

userInfo：

- 类型：字符串
- 默认值：无
- 描述：自定义字符串

####callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```
status:       //操作状态值
```
err：

- 类型：JSON对象

内部字段：

```
error:"错误详情"      //错误描述
```
###示例代码

```
var bb = api.require("brightBeacon");
bb.sendLocalNotification({msg:"区域通知","action":"立即查看","userInfo":"自定义传输参数"},
function(ret,err){
   if(ret.status){
    	alert(JSON.stringify(ret1));
   }else{
   		alert(err.error);
   }
});
```
###补充说明

支持后台发送通知到系统通知栏

###可用性

iOS系统，Android系统

####startAdvertising<div id="a7"></div>

模拟Beacon发射广播信号
startAdvertising(params,callback(ret, err))

####params

uuid：

- 类型：字符串
- 默认值：无
- 描述：UUID

major：

- 类型：整型
- 默认值：无
- 描述：Major

minor：

- 类型：整型
- 默认值：无
- 描述：Minor

####callback(ret, err)
ret：

- 类型：JSON对象

内部字段：

```
status:           //操作状态值
```

err：

- 类型：JSON对象

内部字段：

```
error:"错误详情"           //错误描述
```
###示例代码

```
var obj = api.require("brightBeacon");
obj.startAdvertising({"uuid":"E2C56DB5-DFFB-48D2-B060-D0F5A71096E0","major":1,"minor":"","mac":"","identifier":"demo"},
function(ret, err){
   if(ret.status){
   	alert("调用模拟Beacon成功");
   }else{
   	alert(err.error);
   }
});
```
###补充说明

该方法目前仅支持IOS，Android会在5.0后系统提供该支持

###可用性

iOS系统，Android系统

####stopAdvertising<div id="a8"></div>

停止模拟Beacon
stopAdvertising(callback(ret, err))

####callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```
status:           //操作状态值
```

err：

- 类型：JSON对象

内部字段：

```
error:"错误详情"          //错误描述
```

###示例代码

```
var obj = api.require("brightBeacon");
obj.stopAdvertising(function(ret, err){
   if(ret.status){
   alert("停止模拟Beacon成功");
   }else{
   alert("停止模拟Beacon失败"+err.error);
   }
});
```
###补充说明
无
###可用性

iOS系统

####connectBeacon<div id="a9"></div>

连接Beacon
connectBeacon(params,callback(ret, err))

####params
mac：

- 类型：字符串
- 默认值：无
- 描述：mac地址
version：

- 类型：整型
- 默认值：无
- 描述：固件类型
####callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```
status:          //操作状态值
beacon：         //Beacon(详情见Beacon)
```
###示例代码

```
var obj = api.require("brightBeacon");
obj.connectBeacon({mac:"xx:xx:xx:xx:xx"，version:772},function(ret, err){
   if(ret.status){
	   alert(JSON.stringify(ret.beacon));
   }
});
```
###补充说明

连接状态持续超过3分钟会自动断开

###可用性

iOS系统，Android系统

####disconnectBeacon<div id="a10"></div>

关闭Beacon连接
disconnectBeacon(params,callback(ret, err))

####callback(ret, err)

ret：

- 类型：JSON对象

###内部字段：

```
status:true/false           //操作状态值
```
err：

- 类型：JSON对象

内部字段：

```
error:"错误详情"    //错误描述
```
###示例代码

```
var obj = api.require("brightBeacon");
obj.disconnectBeacon({"mac":"xx:xx:xx:xx:xx:xx"}，function(ret, err){
   if(ret.status){
   alert("调用关闭Beacon连接成功");
   }else{
   alert(err.error);
   }
});
```
###补充说明

关闭Beacon连接

###可用性

iOS系统，Android系统

####isBeaconConnected<div id="a11"></div>

是否连接
isBeaconConnected(params,callback(ret, err))

####callback(ret, err)
ret：

- 类型：JSON对象

###内部字段：

```
status:true/false           //1连接 0未连接
```

err：

- 类型：JSON对象

内部字段：

```
error:"错误详情"    //错误描述
```

###示例代码

```
var obj = api.require("brightBeacon");
obj.isBeaconConnected(mac:"xx:xx:xx:xx:xx:xx",function(ret, err){
   if(ret.status){
   alert("连接状态");
   }else{
   alert("未连接状态");
   }
});
```
###补充说明

是否连接

###可用性
iOS系统，Android系统

####writeBeaconValues<div id="a12"></div>

设置Beacon值
writeBeaconValues(params,callback(ret, err))

####params

major：

- 类型：整型
- 默认值：无
- 描述：Major

minor：

- 类型：整型
- 默认值：无
- 描述：Minor

uuid：

- 类型：字符串
- 默认值：无
- 描述：UUID

txPower：

- 类型：整型
- 默认值：无
- 描述：发射功率

mPower：

- 类型：整型
- 默认值：无
- 描述：测量功率

txInterval：

- 类型：整型
- 默认值：无
- 描述：发射频率

pMode：

- 类型：整型
- 默认值：无
- 描述：1发布模式 0测试模式 开启发布模式需registerAppKey传人您申请的应用APPKEY

broadcastMode：

- 类型：整型
- 默认值：无
- 描述：参数值：1（只广播iBeacon）、2（轮播iBeacon和Eddystone(UID)）、3（轮播iBeacon和Eddystone(URL)）、4（仅广播Eddystone(UID)）、5（仅广播Eddystone(URL)）、6（轮播Eddystone(UID/URL)）

eddystoneUrl：

- 类型：字符串
- 默认值：无
- 描述：Eddystone 的URL(此参数启用了Eddystone的URL广播模式才有效)
- 
####callback(ret, err)
ret：

- 类型：JSON对象

###内部字段：

```
status:true/false           //操作状态值
```
err：

- 类型：JSON对象

内部字段：

```
error:"错误详情"    //错误描述
```
###示例代码

```
var obj = api.require("brightBeacon");
obj.writeBeaconValues({mac:"xx:xx:xx:xx:xx:xx","uuid":"E2C56DB5-DFFB-48D2-B060-D0F5A71096E0","major":"0","minor":"0","name":"BrightBeacon","txInterval":"400","mPower":"-65","pMode":0,"txPower":"2"}，function(ret, err){
   if(ret.status){
   alert("调用设置Beacon值成功");
   }else{
   alert(err.error);
   }
});
```
###补充说明

设置Beacon值,参数可选,mac必填

###可用性

iOS系统，Android系统

####checkBeaconFirmwareUpdate<div id="a13"></div>

检查固件是否可更新
checkBeaconFirmwareUpdate(params,callback(ret, err))

####callback(ret, err)
ret：

- 类型：JSON对象

###内部字段：

```
status:true/false           //操作状态值
update:true/false           //true有更新false无更新
```
err：

- 类型：JSON对象

内部字段：

```
error:"错误详情"    //错误描述
```
###示例代码

```
var obj = api.require("brightBeacon");
obj.checkBeaconFirmwareUpdate({mac:"xx:xx:xx:xx:xx:xx"},function(ret, err){
   if(ret.status){
   	if(ret.update)alert("调用检查固件版本成功,现在可以调用updateBeaconFirmwareWithProgress进行更新");
   }else{
   alert("调用检查固件版本msg+err.msg");
   }
});
```
###补充说明

检查固件是否可更新，检查成功之后，之后可以调用updateBeaconFirmwareWithProgress进行升级操作

###可用性

iOS系统，Android系统

####updateBeaconFirmwareWithProgress<div id="a14"></div>

固件升级
updateBeaconFirmwareWithProgress(params,callback(ret, err))

####callback(ret, err)

ret：

- 类型：JSON对象

###内部字段：

```
status:true/false      //操作状态值
progress:0~100         //更新进度值(百分比值)
```

err：

- 类型：JSON对象

内部字段：

```
error:"错误详情"    //错误描述
```

###示例代码


```
var obj = api.require("brightBeacon");
obj.updateBeaconFirmwareWithProgress({mac:"xx:xx:xx:xx:xx:xx"},function(ret, err){
   if(ret.status){
	   if(ret.progress=='100'){
   			alert("固件升级成功");
	   }
   }else{
   	alert(err.error);
   }
});
```
###补充说明

固件升级必须先检查更新 checkBeaconFirmwareUpdate

###可用性

iOS系统，Android系统

####resetBeacon<div id="a15"></div>

重置Beacon
resetBeacon(params,callback(ret, err))

####callback(ret, err)
ret：

- 类型：JSON对象

###内部字段：

```
status:true/false           //操作状态值
```

err：

- 类型：JSON对象

内部字段：

```
error:"错误详情"    //错误描述
```

###示例代码


```
var obj = api.require("brightBeacon");
obj.resetBeacon({mac:"xx:xx:xx:xx:xx:xx"},function(ret, err){
   if(ret.status){
   alert("重置Beacon成功");
   }else{
   alert(err.error);
   }
});
```

###补充说明

重置Beacon所有参数,包含AppKey

###可用性

iOS系统，Android系统

####resetBeaconAppKey<div id="a16"></div>

重置AppKey
resetBeaconAppKey(params,callback(ret, err))

####callback(ret, err)

ret：

- 类型：JSON对象

###内部字段：

```
status:true/false           //操作状态值
```
err：

- 类型：JSON对象

内部字段：

```
error:"错误详情"    //错误描述
```
###示例代码

```
var obj = api.require("brightBeacon");
obj.resetBeaconAppKey({mac:"xx:xx:xx:xx:xx:xx"},function(ret, err){
   if(ret.status){
   alert("重置AppKey成功");
   }else{
   alert(err.error);
   }
});
```

###补充说明

只重置Beacon的AppKey，可以重新连入应用AppKey

###可用性

iOS系统，Android系统

####monitorRegions<div id="a17"></div>

---
获取正在监听的区域
monitorRegions(callback(ret, err))

####callback(ret, err)
ret：

- 类型：JSON对象

###内部字段：

```
status:true/false           //操作状态值
regions：				//详情见regions监听区域;
```

err：

- 类型：JSON对象

内部字段：

```
error:"错误详情"    //错误描述
```
###示例代码

```
var obj = api.require("brightBeacon");
obj.monitorRegions(function(ret, err){
   if(ret.status){
   JSON.stringify(ret.regions);
   }else{
   alert(err.error);
   }
});
```
###补充说明

无

###可用性

iOS系统，Android系统

<div id="const-content"></div>

Constant|-|-|-|-
-|-|-|-|-
<a href="#a100">status 操作状态值</a>|<a href="#a101">state 区域监听状态</a>|<a href="#a102">Beacon属性值</a>|<a href="#a103">update 是否可升级状态</a>|<a href="#a104">region 监听区域</a>

####status 操作状态值<div id="a100"></div>

status 操作状态值
###取值范围：

- true        //成功
- false        //失败

####state 区域监听状态值<div id="a101"></div>

区域监听状态
###取值范围：

- 1        //进入范围
- 2       //离开范围

####Beacon<div id="a102"></div>
---
Beacon 属性
###属性：

- name             //名称
- distance                //距离
- mac        //Mac地址
- uuid        //UUID
- major        //Major
- minor        //Minor
- mPower        //测量功率
- txInterval        //发射频率
- txPower        //发射功率
- pMode        //0开发模式1发布模式
- battery        //电量（百分比）
- temperature        //温度（摄氏度）
- rssi        //信号强度指示
- version        //固件类型（旧固件不支持此属性）
- firmware        //固件版本号
- eddystoneUrl        //Eddystone URL（旧固件不支持此属性）

####是否可升级状态<div id="a103"></div>

是否可升级状态
###取值范围：

- true        //可升级
- false        //无


####region 监听区域<div id="a104"></div>

region 监听区域

###region属性：

- minor        //minor
- major        //major
- mac        //蓝牙地址
- uuid        //uuid
- identifier //区域ID

Copyright &copy; 2015 API [BrightBeacon](http://www.brtbeacon.com) Docs