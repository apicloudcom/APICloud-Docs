/*
Title: FNImageClip
Description: FNImageClip
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

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

FNImageClip 模块封装了图片裁剪功能。**该模块是 imageClip 模块的优化版。**

#**open**<div id="a1"></div>

打开图片裁剪

open({params}, callback(ret, err))

##params

rect：

- 类型：JSON 类型
- 描述：（可选项）模块的位置及尺寸
- 内部字段：

```js
{
    x: 0,                              //（可选项）数字类型；模块左上角的 x 坐标（相对于所属的 Window 或 Frame）；默认值：0
    y: 0,                              //（可选项）数字类型；模块左上角的 y 坐标（相对于所属的 Window 或 Frame）；默认值：0
    w: 320,                            //（可选项）数字类型；模块的宽度；默认值：所属的 Window 或 Frame 的宽度
    h: 480                             //（可选项）数字类型；模块的高度；默认值：所属的 Window 或 Frame 的高度
}
```

srcPath：

- 类型：字符串类型
- 描述：源图片路径，要求本地路径（fs://、widget://）

style：

- 类型：JSON 类型
- 描述：图片裁剪的样式设置
- 内部字段：

```js
{
    mask: '#888',                      //（可选项）字符串类型；图片裁剪控件遮罩层背景，支持 rgb，rgba，#；默认：#888
    clip: {                         
        w: 100,                        //（可选项）数字类型；裁剪区域的宽度，当 appearance 为 circular 时，w 为半径；默认：rect.w / 2
        h: 100,                        //（可选项）数字类型；裁剪区域的高度，当 appearance 为 circular 时，h 无效；默认：w
        x: 50,                         //（可选项）数字类型；裁剪区域左侧相对于裁剪控件左侧的距离；默认：(rect.w - w) / 2
        y: 50,                         //（可选项）数字类型；裁剪区域顶部相对于裁剪控件顶部的距离；默认：(rect.h - h) / 2
        borderColor: '#0f0',           //（可选项）字符串类型；裁剪区域边线颜色，支持 rgb，rgba，#；默认：透明
        borderWidth: 1,                //（可选项）数字类型；裁剪区域边线；默认：0
        appearance: 'circular',        //（可选项）字符串类型；裁剪区域的形状，支持 circular | rectangle；默认：rectangle
    }
}
```

mode：

- 类型：字符串类型
- 描述：（可选项）裁剪模式
- 默认：all
- 取值范围：
	- clip：裁剪框可移动或缩放，图片固定位置和大小，当 appearance 值为 circular 时，无法改变大小
	- image：图片可以移动或缩放，裁剪框固定位置和大小
	- all：裁剪框可移动或缩放，图片可移动或缩放，**该模式下用户的放大操作只对图片有效，裁剪框只能通过拖动改变大小**，当 appearance 值为 circular 时，无法改变大小


fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:		//布尔类型；操作成功状态值，true|false 
}

```

##示例代码

```js
var FNImageClip = api.require('FNImageClip');
FNImageClip.open({
    rect: {
        x: 0,
        y: 0,
        w: api.winWidth,
        h: api.winHeight
    },
    srcPath: 'fs://imageClip/image.png',
    style: {
        mask: '#888',
        clip: {
            w: 100,
            h: 100,
            x: 50,
            y: 50,
            borderColor: '#0f0',
            borderWidth: 1,
            appearance: 'rectangle'
        }
    },
    fixedOn: api.frameName
}, function(ret, err){        
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

FNImageClip 同时只能运行一个实例，当重复调用 open 时，会将已存在的 FNImageClip 实例弹出到当前窗口的最上层

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**save**<div id="a2"></div>

保存截图

save({params}, callback(ret, err))

##params

destPath：

- 类型：字符串类型
- 描述：保存图片路径，要求本地路径（fs://、widget://）

copyToAlbum：

- 类型：布尔类型
- 描述：（可选项）是否将结果同时保存到系统相册
- 默认：false

quality：

- 类型：数字类型
- 描述：（可选项）保存图片的质量，取值范围 0 至 1 的浮点数
- 默认：1

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	destPath:           //字符串类型；图片保存到指定路径后的绝对路径，若保存失败则为该参数为 undefined
	albumPath:          //字符串类型；图片保存到相册后的绝对路径，若保存失败则该参数为 undefined
}

```

##示例代码

```js
var FNImageClip = api.require('FNImageClip');
FNImageClip.save({
    destPath: 'fs://imageClip/result.png',
    copyToAlbum: false,
    quality: 1
},function(ret, err){		
    if(ret) {
        alert(JSON.stringify(ret));
    } else{
        alert(JSON.stringify(err));
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**close**<div id="a3"></div>

关闭截图器

close()

##示例代码

```js
var FNImageClip = api.require('FNImageClip');
FNImageClip.close();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**reset**<div id="a4"></div>

重置裁剪区域，恢复到初始打开时的状态

reset()

##示例代码

```js
var FNImageClip = api.require('FNImageClip');
FNImageClip.reset();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本