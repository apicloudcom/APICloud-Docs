/*
Title: imageClip
Description: imageClip
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#a1)

[save](#a2)

[close](#a3)

[reset](#a4)

</div>

#**概述**

imageClip模块封装了图片裁剪功能，本模块已停止更新，建议使用优化升级版[FNImageClip](http://docs.apicloud.com/端API/功能扩展/FNImageClip)

#**open**<div id="a1"></div>

打开图片裁剪

open({params}, callback(ret, err))

##params

path：

- 类型：字符串
- 默认值：无
- 描述：源图片路径，支持fs://、widget://等文件路径协议

bg：

- 类型：字符串
- 默认值：#000
- 描述：（可选项）背景，支持颜色（#、rgb、rgba等格式）和图片（支持fs://、widget://等文件路径协议）

x:

- 类型：数字
- 默认值：0
- 描述：（可选项）整个区域左上角x坐标

y:

- 类型：数字
- 默认值：0
- 描述：（可选项）整个区域左上角y坐标

w:

- 类型：数字
- 默认值：屏幕宽度
- 描述：（可选项）整个区域宽度

h:

- 类型：数字
- 默认值：屏幕高度
- 描述：（可选项）整个区域高度

clipRect：

- 类型：JSON对象
- 默认值：根据图片大小在整个区域居中显示
- 描述：（可选项）图片裁剪区域位置和大小

内部字段:

```js
{
	x:  	   //数字类型；裁剪框左上角x坐标
	y: 		   //数字类型；裁剪框左上角y坐标
	w:   	   //数字类型；裁剪框宽度
	h:		   //数字类型；裁剪框高度
	fixation:  //布尔类型；裁剪框位置大小是否固定，默认：false（不固定）
}
```

layerColor:

- 类型：字符串
- 默认值：rgba(69, 69, 69, 0.5)
- 描述：（可选项）裁剪框以外的遮罩层颜色，支持#、rgb、rgba等格式

borderColor：

- 类型：字符串
- 默认值：#fff
- 描述：（可选项）裁剪区域边框颜色，支持#、rgb、rgba等格式

borderWidth：

- 类型：数字
- 默认值：2
- 描述：（可选项）裁剪区域边框粗细

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:		//操作成功状态值，布尔类型
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:		//错误描述
}
```

##示例代码

```js
var imageClip = api.require('imageClip');
imageClip.open({
    path: 'widget://res/img/apicloud.png'
},function( ret, err ){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**save**<div id="a2"></div>

保存截图到指定位置

save ({params}, callback(ret, err))

##params

album：

- 类型：布尔类型
- 默认值：false
- 描述：（可选项）是否保存到系统相册

savePath：

- 类型：字符串类型
- 描述：存储路径，要求本地路径（fs://）

quality：

- 类型：数字
- 默认值：1.0
- 描述：（可选项）保存的截图质量，取值范围0-1

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	savePath:       //截图保存的绝对路径
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:		//错误描述
}
```

##示例代码

```js
var imageClip = api.require('imageClip');
imageClip.save(function( ret, err ){		
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**close**<div id="a3"></div>

关闭截图

close()

##示例代码

```js
var imageClip = api.require('imageClip');
imageClip.close();
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**reset**<div id="a4"></div>

重置裁剪区域，恢复到初始打开时的状态

reset()

##示例代码

```js
var imageClip = api.require('imageClip');
imageClip.reset();
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本




