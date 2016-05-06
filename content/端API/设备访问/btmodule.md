/*
Title: btmodule
Description: btmodule
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：开发者</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[OpenBT](#a1)

[CloseBT](#a2)

[ScanBT](#a3)

[DisConnectBT](#a5)

[WriteBT](#a6)

[ReadBT](#a7)

[NotifyBT](#a8)


</div>



#**概述**

btmodule模块封装了蓝牙4.0的接口，本接口是BLE，和传统蓝牙不一样，本模块集成了打开蓝牙， 关闭蓝牙，扫描附近BLE设备并连接等功能，支持写数据到BLE外设，本模块暂只提供安卓接口， 苹果接口会在以后更新；本模块只能用于手机客户端连接到智能硬件设备，暂时不能实现手机端直接的互联，本模块由第三方模块开发者提供，使用本模块需在线云编译安装包 


#**OpenBT**<div id="a1"></div>

打开设备蓝牙功能

OpenBT()

##示例代码

```js
var obj = api.require('btmodule');
obj.OpenBT();
```

##可用性

Android系统，需设备支持蓝牙4.0且安卓版本在4.3以上

可提供的1.0.0及更高版本


#**CloseBT**<div id="a2"></div>

关闭蓝牙功能

CloseBT()


##示例代码

```js
var obj = api.require('btmodule');
obj.CloseBT();
```


##可用性

Android系统，需设备支持蓝牙4.0且安卓版本在4.3以上

可提供的1.0.0及更高版本

#**ScanBT**<div id="a3"></div>

扫描并连接附近BLE外设

ScanBT()



##示例代码

```js
var obj = api.require('btmodule');
obj.ScanBT();
```

##补充说明

此接口提供扫描附近BLE外设，并连接；一旦连接成功就可以对连接成功的设备进行数据写入，若已连接后 重复调用，则会只能操作最新连接的设备 ，若已经选择了设备却没有提示"connected",表达正在连接中，一般10s之内可以完成连接。

##可用性

Android系统，需设备支持蓝牙4.0且安卓版本在4.3以上

可提供的1.0.0及更高版本


#**DisConnectBT**<div id="a5"></div>

断开和BLE外设的连接，前提条件是已经和BLE外设连接

DisConnectBT()


##示例代码

```js
var obj = api.require('btmodule');
obj.DisConnectBT();
```

##补充说明

调用此接口前确保已经连接 

##可用性

Android系统，需设备支持蓝牙4.0且安卓版本在4.3以上 

可提供的1.0.0及更高版本

#**WriteBT**<div id="a6"></div>

写入数据到已经连接的BLE外设 

WriteBT(param)

##param

service：

- 类型：字符串
- 描述：BLE外设的service(服务)的UUID，不能为空

charUUID：

- 类型：字符串
- 描述：BLE外设的characteristic(特征值)的UUID，不能为空

data：

- 类型：数字
- 描述：需要传输给BLE外设的数据，范围为(0,255),不能为空


##示例代码

```js
var obj = api.require('btmodule');
 var param={service:"0000fff0-0000-1000-8000-00805f9b34fb" 
        ,charUUID:"0000fff1-0000-1000-8000-00805f9b34fb",data:25};
obj.WriteBT(param);
```

##补充说明

调用此接口前，需设定好需要写入的BLE外设的characteristic(特征值)的UUID 和其所属的service(服务)的UUID，本示例代码是设成TI-CC2540芯片的BLE协议栈例程 里面的simpleGATTprofile的service的UUID和char的UUID进行写入数据；另外:本接口只支持写入(0,255)范围的数据

##可用性

Android系统，需设备支持蓝牙4.0且安卓版本在4.3以上 

可提供的1.0.0及更高版本

#**ReadBT**<div id="a7"></div>

读取已经连接的BLE外设的数据

ReadBT(param, function(ret, err){var msg =ret.received;api.toast({msg:msg});})

##param

service：

- 类型：字符串
- 描述：BLE外设的service(服务)的UUID，不能为空

charUUID：

- 类型：字符串
- 描述：BLE外设的characteristic(特征值)的UUID，不能为空


##示例代码

```js
var obj = api.require('btmodule');
var param={service:"0000fff0-0000-1000-8000-00805f9b34fb"
		,charUUID:"0000fff1-0000-1000-8000-00805f9b34fb"};
		obj.ReadBT(param, function(ret, err){
	        	 var msg =ret.received;
	        	api.toast({
        msg:msg
    });
	        });
```


##callbacl(ret,err)

ret：

- 类型：JSON 对象

内部字段：
```js
{
  received: //读取到的数据
}
```

err：

- 类型：JSON 对象

内部字段：
```js
{
   msg:””        //错误描述
}
```


##补充说明

调用此接口前，需设定好需要读取的BLE外设的characteristic(特征值)的UUID 和其所属的service(服务)的UUID，本示例代码是设成TI-CC2540芯片的BLE协议栈例程 里面的simpleGATTprofile的service的UUID和char的UUID进行读取数据；

##可用性

Android系统，需设备支持蓝牙4.0且安卓版本在4.3以上 

可提供的1.0.0及更高版本

#**NotifyBT**<div id="a8"></div>

打开或者关闭的BLE外设的notify功能

NotifyBT(param, function(ret, err){var msg =ret.received;api.toast({msg:msg});})

##param

service：

- 类型：字符串
- 描述：BLE外设的service(服务)的UUID，不能为空

charUUID：

- 类型：字符串
- 描述：BLE外设的characteristic(特征值)的UUID，不能为空


enable：

- 类型：boolean类型
- 描述：打开或者关闭notify功能，不能为空
##示例代码

```js
var obj = api.require('btmodule');
		var param={service:"0000fff0-0000-1000-8000-00805f9b34fb"
		,charUUID:"0000fff4-0000-1000-8000-00805f9b34fb",enable:true};
		obj.NotifyBT(param,function(ret, err){
	        	 var msg =ret.received;
	        	api.toast({
        msg:msg
    });
	        });
```


##callbacl(ret,err)

ret：

- 类型：JSON 对象

内部字段：
```js
{
  received: //接收到的数据
}
```

err：

- 类型：JSON 对象

内部字段：
```js
{
   msg:””        //错误描述
}
```


##补充说明

调用此接口前，需设定好需要notify的BLE外设的characteristic(特征值)的UUID 和其所属的service(服务)的UUID，本示例代码是设成TI-CC2540芯片的BLE协议栈例程 里面的simpleGATTprofile的service的UUID和char的UUID进行打开notify功能；另外，需要注意的是，由于Apicloud的回调机制，只有调用函数才能回调获得Notify的值，所以就算BLE外设的UUID已经通过该功能打开notify了，当外设主动给app传数据的时候，也是不能触发NotifyBT的回调函数的，只能通过再次调用该函数来获取外设的值，所以该功能与ReadBT函数功能类似

##可用性

Android系统，需设备支持蓝牙4.0且安卓版本在4.3以上 

可提供的1.0.0及更高版本


<!--

#**GetBTState**<div id="a9"></div>

获取蓝牙状态

GetBTState(function(ret, err){
		 var msg1 =ret.rssi;
		 var msg2 =ret.isbtopen;
		 var msg3 =ret.isbtconnect;
		 var msg4 =ret.devicename;
		 var msg5 =ret.deviceMacAdd;
	        	api.toast({
        msg:msg2+msg3+msg4+msg5
    });
	        })

##示例代码

```js
var obj = api.require('btmodule');
		obj.GetBTState(function(ret, err){
		 var msg1 =ret.rssi;
		 var msg2 =ret.isbtopen;
		 var msg3 =ret.isbtconnect;
		 var msg4 =ret.devicename;
		 var msg5 =ret.deviceMacAdd;
	        	api.toast({
        msg:msg2+msg3+msg4+msg5
    });
	        })
```


##callbacl(ret,err)

ret：

- 类型：JSON 对象

内部字段：
```js
{
  rssi: //连接后的信号强度值
  isbtopen: //蓝牙是否打开
  isbtconnect: //蓝牙是否已经连接
  devicename: //连接到的外设名称
  deviceMacAdd: //连接到的外设的Mac地址
}
```

err：

- 类型：JSON 对象

内部字段：
```js
{
   msg:””        //错误描述
}
```


##补充说明

调用此接口前，如果没有连接到外设，则不能获取rssi值，只有连接成功了才能获取rssi值

##可用性

Android系统，需设备支持蓝牙4.0且安卓版本在4.3以上 

可提供的1.0.0及更高版本

-->