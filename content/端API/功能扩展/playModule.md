/*
Title: playModule
Description: playModule
*/
<div class="outline">
[init](#a1)
[play](#a2)
[pause](#a3)
[start](#a4)
[stop](#a5)
[getDuration](#a6)
[getCurrentPosition](#a7)
[full](#a8)
[unfull](#a9)
[isfull](#a10)
</div>

#**概述**

playModule 封装了视频播放功能（不支持音频播放）。使用本模块时可把本模块当做一个 frame 添加在 window 或 frame 上。IOS 、Android平台上支持的视频文件格式有：MOV，MP4，M4V，3gp，flv，ACC等    ; 

<div id="a1"></div>
#**init**

初始化视频播放配置(仅Android系统使用)

init({params}, callback(ret, err))

##params

defaultBtn：

- 类型：布尔
- 描述：（可选项）是否显示默认自带的播放控制按钮
- 默认值：true（显示）

##示例代码

```js
var obj= api.require('playModule');
obj.init({defaultBtn:false},function(ret, err){
alert(JSON.stringify(ret));
});
```

##可用性
Android系统

可提供的1.0.0及更高版本

<div id="a2"></div>
#**play**

播放本地视频或者网络视频

play({params}, callback(ret, err))

##params

x：

- 类型：数字类型
- 描述：（必填项）模块左上角的 x 坐标（相对于所属的 Window 或 Frame）；
- 默认值：0

y：

- 类型：数字类型
- 描述：（必填项）模块左上角的 y 坐标（相对于所属的 Window 或 Frame）；默认：0
- 默认值：0

w：

- 类型：数字类型
- 描述：（可选项）模块的宽度；默认：所属的 Window 或 Frame 的宽度

h：

- 类型：数字类型
- 描述：（可选项）模块的高度；默认：所属的 Window 或 Frame 的高度
- 默认值：300

fixedOn：

- 类型：字符串
- 描述：（可选项）模块所属 Frame 的名字，若不传则模块归属于当前 Window

fixed：

- 类型：布尔
- 描述：（（可选项）模块是否随所属 Window 或 Frame 滚动
- 默认值：true（不随之滚动）

url：

- 类型：字符串
- 描述：（必填项）视频资源地址，支持fs://、widget://、http://

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
status: true   //布尔型；true||false
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
msg: ""
}
```

##示例代码

```js
var obj= api.require('playModule');
obj.play({
x: 0,
y: 45,
h: 200,
fixedOn:api.frameName,
url: 'http://resource.apicloud.com/video/apicloud3.mp4'
}, function(ret, err){
});
```

##可用性

iOS、Android系统

可提供的1.0.0及更高版本



<div id="a3"></div>
#**pause**

暂停播放(仅Android系统使用)

pause(callback(ret, err))

##示例代码

```js
var obj= api.require('playModule');
obj.pause(function(ret, err){
alert(JSON.stringify(ret));
});
```

##可用性
Android系统

可提供的1.0.0及更高版本



<div id="a4"></div>
#**start**

暂停后开始播放(仅Android系统使用)

start(callback(ret, err))

##示例代码

```js
var obj= api.require('playModule');
obj.start(function(ret, err){
alert(JSON.stringify(ret));
});
```

##可用性
Android系统

可提供的1.0.0及更高版本

<div id="a5"></div>
#**stop**

停止播放(仅Android系统使用)

stop(callback(ret, err))

##示例代码

```js
var obj= api.require('playModule');
obj.stop(function(ret, err){
alert(JSON.stringify(ret));
});
```

##可用性
Android系统

可提供的1.0.0及更高版本

<div id="a6"></div>
#**getDuration**

获取视频的时长(仅Android系统使用)

getDuration(callback(ret, err))

##示例代码

```js
var obj= api.require('playModule');
obj.getDuration(function(ret, err){
alert(JSON.stringify(ret));
});
```

##可用性
Android系统

可提供的1.0.0及更高版本


<div id="a7"></div>
#**getCurrentPosition**

获取已经播放的时长(仅Android系统使用)

getCurrentPosition(callback(ret, err))

##示例代码

```js
var obj= api.require('playModule');
obj.getCurrentPosition(function(ret, err){
alert(JSON.stringify(ret));
});
```

##可用性
Android系统

可提供的1.0.0及更高版本



<div id="a8"></div>
#**full**

全屏播放(仅Android系统使用)

full(callback(ret, err))

##示例代码

```js
var obj= api.require('playModule');
obj.full(function(ret, err){
alert(JSON.stringify(ret));
});
```

##可用性
Android系统

可提供的1.0.0及更高版本



<div id="a9"></div>
#**unfull**

退出全屏(仅Android系统使用)

unfull()


##示例代码

```js
var obj= api.require('playModule');
obj.unfull();
```

##可用性
Android系统

可提供的1.0.0及更高版本



<div id="a10"></div>
#**isfull**

是否全屏(仅Android系统使用)

isfull()


##示例代码

```js
var obj= api.require('playModule');
obj.isfull();
```

##可用性
Android系统

可提供的1.0.0及更高版本
