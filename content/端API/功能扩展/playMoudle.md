/*
Title: playModule
Description: playModule
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[play](#a1)
</div>

#**概述**

playMoudle封装了在线播放视频和离线视频播放功能，支持多种文件格式的播放，
如：mp3，flv，avi，mpeg，wmv，3gp，mov等。 本模块暂仅支持IOS。


#**play**<div id="a1"></div>

播放视频

play({params},callback(ret, err))
##params

x：
- 类型：数字
- 默认值：0
- 描述：（可选项）视频的左上角点的x坐标

y：
- 类型：数字
- 默认值：0
- 描述：（可选项）视频的左上角点的y坐标

w：
- 类型：数字
- 默认值：父窗口的宽
- 描述：（可选项）视频的宽

h：
- 类型：数字
- 默认值：父窗口的高
- 描述：（可选项）视频的高

fixedOn：
- 类型：字符串
- 默认值：当前主窗口的名字
- 描述：（可选项）将此模块视图添加到指定窗口的名字

url：
- 类型：字符串
- 默认值：无
- 描述：（可选项）视频地址，支持fs://，widget://，http:等文件路径协议

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
code:0    //错误码
msg:""    //错误描述
}
```

##示例代码

```js
var obj = api.require('playModule');
obj.play({
x : 0,
y : 0,
w : 250,
h : 200,
fixedOn:api.frameName,
url:'http://www.cnncw.cn/d/file/shipin/2015/1506/ncxw0614.flv'
}, function(ret, err) {

});
```

##补充说明

视频播放

##可用性

iOS系统

可提供的1.0.0及更高版本