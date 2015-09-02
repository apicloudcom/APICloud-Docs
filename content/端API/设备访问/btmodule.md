
/*
Title: btmodule
Description: btmodule
*/

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

##补充说明

无

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

##补充说明

无

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

此接口提供扫描附近BLE外设，并连接；一旦连接成功必须断开连接才能再次进行扫描，若已连接后 重复调用，则会提示"BLE is connected,can't scan" ，若已经选择了设备却没有提示"connected",表达正在连接中，一般10s之内可以完成连接。

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
- 默认值：无
- 描述：BLE外设的service(服务)的UUID，不能为空

charUUID：

- 类型：字符串
- 默认值：无
- 描述：BLE外设的characteristic(特征值)的UUID，不能为空

data：

- 类型：数字
- 默认值：无
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