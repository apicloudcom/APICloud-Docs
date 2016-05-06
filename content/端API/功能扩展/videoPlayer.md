/*
Title: videoPlayer
Description: videoPlayer
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">
<div class="outline">
[play](#0)

[open](#1)

[setPath](#2)

[start](#3)

[pause](#4)

[stop](#5)

[close](#6)

[show](#7)

[hide](#8)

[fullScreen](#9)

[cancelFullScreen](#10)

[forward](#11)

[rewind](#12)

[seekTo](#13)

[setBrightness](#14)

[getBrightness](#15)

[setVolume](#16)

[getVolume](#17)

[addEventListener](#18)

[removeEventListener](#19)

[setRect](#20)

</div>

#**概述**

videoPlayer 封装了视频播放功能（不支持音频播放）。可快进、快退设置播放位置等操作，亦可设置屏幕亮度和系统声音大小。通过监听接口可获取模块上的各种手势操作事件。使用本模块时可把本模块当做一个 frame 添加在 window 或 frame 上。Android 平台上支持的的视频文件格式有：MP4、3gp；IOS 平台上支持的视频文件格式有：MOV，MP4，M4V。本模块封装了两道播放方案：一，通过调用 play 接口，直接打开一个自带默认播放界面的播放器；二，通过 open 接口，打开一个纯播放器界面，再配合 frame 自定义完整的播放页面，通过start、pause、stop等接口控制播放操作。

#**play**<div id="0"></div>

打开一个自带界面的视频播放器，本播放器为全屏横屏显示，支持屏幕随设备自动旋转。用户单击播放器时，会弹出 foot 和 head 导航条，再次单击则关闭之。**仅 setPath 接口对本接口打开的播放器有效**

play({params}, callback(ret, err))
##params

texts：

- 类型：JSON 对象
- 描述：（可选项）聊天输入框模块可配置的文本
- 内部字段：

```js
{
    head: {          //（可选项）JSON 对象；顶部文字
        title: ''    //（可选项）字符串类型；顶部标题文字
    }
}
```

styles：

- 类型：JSON 对象
- 描述：（可选项）模块的样式设置
- 内部字段：

```js
{
    head:{                           //（可选项）JSON对象；播放器顶部导航条样式    
       bg: 'rgba(161,161,161,0.5)',  //（可选项）字符串类型；顶部导航条背景，支持#、rgb、rgba、img；默认：rgba(161,161,161,0.5)
       height: 44,                   //（可选项）数字类型；顶部导航条的高；默认：44
       titleSize: 20,                //（可选项）数字类型；顶部标题字体大小；默认：20
       titleColor: '#fff',           //（可选项）字符串类型；顶部标题字体颜色；默认：#fff
       backSize: 44,                 //（可选项）数字类型；顶部返回按钮大小；默认：44
       backImg:'fs://img/back.png',  //（可选项）字符串类型；顶部返回按钮的背景图片，要求本地路径（widget://、fs://）；默认：返回小箭头图标
       setSize: 44,                  //（可选项）数字类型；顶部右边设置按钮大小；默认：44
       setImg:'fs://img/set.png'     //（可选项）字符串类型；顶部右边设置按钮背景图片，要求本地路径（widget://、fs://）；默认：设置小图标
    },  
    foot:{                           //（可选项）JSON对象；播放器底部导航条样式    
       bg: 'rgba(161,161,161,0.5)',  //（可选项）字符串类型；底部导航条背景，支持#、rgb、rgba、img；默认：rgba(161,161,161,0.5)
       height: 44,                   //（可选项）数字类型；底部导航条的高；默认：44
       playSize: 44,                 //（可选项）数字类型；底部播放/暂停按钮大小；默认：44
       playImg:'fs://img/back.png',  //（可选项）字符串类型；底部播放按钮的背景图片，要求本地路径（widget://、fs://）；默认：播放按钮图标
       pauseImg:'fs://img/back.png', //（可选项）字符串类型；底部暂停按钮的背景图片，要求本地路径（widget://、fs://）；默认：暂停按钮图标
       nextSize: 44,                 //（可选项）数字类型；底部下一集按钮大小；默认：44
       nextImg:'fs://img/back.png',  //（可选项）字符串类型；底部下一集按钮的背景图片，要求本地路径（widget://、fs://）；默认：下一集按钮图标
       timeSize: 14,                  //（可选项）数字类型；底部时间标签大小；默认：14
       timeColor:'#fff',              //（可选项）字符串类型；底部时间标签颜色，支持#、rgba、rgb；默认：#fff
       sliderImg:'fs://img/slder.png',//（可选项）字符串类型；底部进度条滑块背景图片，要求本地路径（widget://、fs://）；默认：滑块小图标
       progressColor: '#696969',      //（可选项）字符串类型；进度条背景色，支持#、rgba、rgb；默认：#696969
       progressSelected: '#76EE00'    //（可选项）字符串类型；滑动后的进度条背景色，支持#、rgb、rgba；默认：#76EE00
    }
}
```

path：

- 类型：字符串
- 描述：（可选项）文档的路径，支持网络和本地（fs://）路径，**在 android 平台上不支持 widget**

autoPlay：

- 类型：布尔
- 描述：（可选项）打开时是否自动播放
- 默认值：true（自动播放）

coverImg：

- 类型：布尔
- 描述：（可选项）封面图路径，播放器打开尚未播放时的封面图，要求本地路径（widget://、fs://）

autorotation:

- 类型：布尔
- 描述：（可选项）视频播放页面是否支持自动旋转（横竖屏），若为 false 则手动点击右下角按钮旋转
- 默认值：true（根据设备当前方向自动适配旋转）

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    eventType:        //字符串类型；回调事件类型，取值范围如下：
                      //show（打开成功并显示）
                      //back（返回）
                      //play（播放）
                      //pause（暂停）
                      //next （下一集）
                      //failed（播放失败）
}
```

##示例代码

```js
var videoPlayer = api.require('videoPlayer');
videoPlayer.play({
    texts: {
        head: {
            title: '顶部文字'
        }
    },
    styles: {
        head: { 
            bg: 'rgba(0.5,0.5,0.5,0.7)', 
            height: 44,
            titleSize: 20,
            titleColor: '#fff',
            backSize: 44,
            backImg: 'fs://img/back.png', 
            setSize: 44,
            setImg: 'fs://img/set.png' 
        },
        foot: {
            bg: 'rgba(0.5,0.5,0.5,0.7)',
            height: 44,
            playSize: 44,
            playImg: 'fs://img/back.png',
            pauseImg: 'fs://img/back.png', 
            nextSize: 44,
            nextImg: 'fs://img/back.png', 
            timeSize: 14,
            timeColor: '#fff',
            sliderImg: 'fs://img/slder.png', 
            progressColor: '#696969', 
            progressSelected: '#76EE00'
        }
    },
    path: 'http://7o50kb.com2.z0.glb.qiniucdn.com/c1.1.mp4', //（可选项）字符串类型；文档的路径，支持网络和本地（fs://）路径；默认：未传值时不播放
    //在 android 平台上不支持 widget://
    autoPlay:true //（可选项）布尔类型；打开时是否自动播放；默认：true（自动播放）
},function(ret, err) {
    if (ret) {
        alert(JSON.stringify(ret));
    } else {
        alert(JSON.stringify(err));
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**open**<div id="1"></div>

打开一个视频播放器

open({params}, callback(ret, err))

##params

rect：

- 类型：JSON 对象
- 描述：（可选项）模块的位置及尺寸
- 内部字段：

```js
{
    x: 0,   //（可选项）数字类型；模块左上角的 x 坐标（相对于所属的 Window 或 Frame）；默认：0
    y: 0,   //（可选项）数字类型；模块左上角的 y 坐标（相对于所属的 Window 或 Frame）；默认：0
    w: 320, //（可选项）数字类型；模块的宽度；默认：所属的 Window 或 Frame 的宽度
    h: 300  //（可选项）数字类型；模块的高度；默认：w的3/4
}
```

path：

- 类型：字符串
- 描述：（可选项）文档的路径，支持网络和本地（fs://）路径，**在 android 平台上不支持 widget**

autoPlay：

- 类型：布尔
- 描述：（可选项）打开时是否自动播放
- 默认值：true（自动播放）

coverImg：

- 类型：布尔
- 描述：（可选项）封面图路径，播放器打开尚未播放时的封面图，要求本地路径（widget://、fs://）

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

fixed：

- 类型：布尔
- 描述：（可选项）模块是否随所属 window 或 frame 滚动
- 默认值：true（不随之滚动）

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:           //布尔类型；是否打开播放组件并显示，true|false；Will be deprecated in ther future
    duration:         //数字类型；视频总时长，单位为s，仅当 status 为 true 时有值
    eventType:        //字符串类型；交互事件类型，取值范围：
                      //show（打开成功并显示）
                      //error（播放器打开失败）
                      //playing（开始播放）
                      //failed（播放失败）
}
```

##示例代码

```js
var videoPlayer = api.require('videoPlayer');
videoPlayer.open({
    path: 'http://7o50kb.com2.z0.glb.qiniucdn.com/c1.1.mp4'
}, function(ret, err){		
	if( ret.status ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setPath**<div id="2"></div>

设置音/视频的文件路径

setPath({params}, callback(ret, err))

##params

path：

- 类型：字符串
- 描述：文档的路径，支持网络和本地（fs://）路径，**在 android 平台上不支持 widget**

coverImg：

- 类型：布尔
- 描述：（可选项）封面图路径，播放器打开尚未播放时的封面图，要求本地路径（widget://、fs://）

title：

- 类型：字符串
- 描述：（可选项）当设置 play 接口打开的视频时，本参数表示设置该视频的标题，本参数仅对 play 接口有效
- 默认值：原标题

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:            //布尔类型；路径是否重设成功，true|false
    duration:          //数字类型；视频总时长，单位为s，仅当 status 为 true 时有值
}
```

##示例代码

```js
var videoPlayer = api.require('videoPlayer');
videoPlayer.setPath({
    path: 'http://7o50kb.com2.z0.glb.qiniucdn.com/c1.1.mp4',
    coverImg:''
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**start**<div id="3"></div>

开始播放

start()

##示例代码

```js
var videoPlayer = api.require('videoPlayer');
videoPlayer.start();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**pause**<div id="4"></div>

暂停播放

pause()

##示例代码

```js
var videoPlayer = api.require('videoPlayer');
videoPlayer.pause();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**stop**<div id="5"></div>

停止播放

stop()

##示例代码

```js
var videoPlayer = api.require('videoPlayer');
videoPlayer.stop();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**close**<div id="6"></div>

关闭播放器

close()

##示例代码

```js
var videoPlayer = api.require('videoPlayer');
videoPlayer.close();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**show**<div id="7"></div>

显示视频播放视图

show()

##示例代码

```js
var videoPlayer= api.require('videoPlayer');
videoPlayer.show();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="8"></div>

隐藏视频播放视图

hide()

##示例代码

```js
var videoPlayer= api.require('videoPlayer');
videoPlayer.hide();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**fullScreen**<div id="9"></div>

全屏播放（横屏模式）

fullScreen()

##示例代码

```js
var videoPlayer= api.require('videoPlayer');
videoPlayer.fullScreen();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**cancelFullScreen**<div id="10"></div>

取消全屏播放

cancelFullScreen()

##示例代码

```js
var videoPlayer= api.require('videoPlayer');
videoPlayer.cancelFullScreen();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**forward**<div id="11"></div>

快进

forward({params})

##params

seconds：

- 类型：数字
- 描述：快进的秒数

##示例代码

```js
var videoPlayer= api.require('videoPlayer');
videoPlayer.forward({
    seconds: 5
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**rewind**<div id="12"></div>

快退

rewind({params})

##params

seconds：

- 类型：数字
- 描述：快退的秒数

##示例代码

```js
var videoPlayer = api.require('videoPlayer');
videoPlayer.rewind({
    seconds: 5
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**seekTo**<div id="13"></div>

跳转

seekTo({params})

##params

seconds：

- 类型：数字
- 描述：跳转到音视频播放的秒数

##示例代码

```js
var videoPlayer = api.require('videoPlayer');
videoPlayer.seekTo({
    seconds: 20
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setBrightness**<div id="14"></div>

设置屏幕亮度

setBrightness({params})

##params

brightness：

- 类型：数字
- 描述：（可选项）设置的屏幕的亮度，取值范围：0-100，**在 iOS 平台上设置的是系统屏幕亮度。Android 平台上设置的本应用内的屏幕亮度**
- 默认值：80


##示例代码

```js
var videoPlayer = api.require('videoPlayer');
videoPlayer.setBrightness({
    brightness: 50
});
```


##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**getBrightness**<div id="15"></div>

获取当前屏幕亮度值

getBrightness(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	brightness:            //数字类型；当前屏幕亮度值
}
```

##示例代码

```js
var videoPlayer = api.require('videoPlayer');
videoPlayer.getBrightness(function( ret, err ){		
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setVolume**<div id="16"></div>

设置音量

setVolume({params})

##params

volume：

- 类型：数字
- 描述：（可选项）音量大小，取值范围：0-1
- 默认值：0

##示例代码

```js
var videoPlayer = api.require('videoPlayer');
videoPlayer.setVolume({
	volume: 0.6
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**getVolume**<div id="17"></div>

获取当前播放音量

getVolume(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	volume:            //数字类型；当前音量值
}
```

##示例代码

```js
var videoPlayer = api.require('videoPlayer');
videoPlayer.getVolume(function( ret, err ){		
	if( ret ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**addEventListener**<div id="18"></div>

添加动作监听(当全屏或者fixed为true且页面不能被左右滑动时有效)

addEventListener({params}，callback(ret, err))

##params

name：

- 类型：字符串
- 描述：（可选项）所要监听的动作名称
- 取值范围：
   - 'leftUp'：播放器靠左的二分之一内的上滑事件，每滑动5（百分比）回调执行一次
   - 'leftDown'：播放器靠左的二分之一内的下滑事件，每滑动5（百分比）回调执行一次
   - 'rightUp'：播放器靠右的二分之一内的上滑事件，每滑动5（百分比）回调执行一次
   - 'rightDown'：播放器靠右的二分之一内的下滑事件，每滑动5（百分比）回调执行一次
   - 'swipeLeft'：播放器上的左滑事件，每滑动5（百分比）回调执行一次
   - 'swipeRight'：播放器上的右滑事件，每滑动5（百分比）回调执行一次
   - 'click'：点击播放器事件（单击手势）
   - 'doubleClick'：双击播放器事件（单击手势）
   - 'play'：播放事件，包括开始播放（start）、正在播放（playing）、暂停（pause）、停止（stop）、播放完成（complete），在回调里用 eventType 区分。**播放事件为 playing 时，回调函数每秒执行四次**

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
   eventType:             //字符串类型；播放事件类型，仅当 name 为 play 时有值；取值范围如下：
                          //start（开始播放）
                          //playing（正在播放）
                          //pause（播放暂停）
                          //stop（播放停止）
                          //complete（播放完成）
   current:               //数字类型；当前播放位置，单位为s，仅当 name 为 play，eventType 为 playing 时有值
}
```

##示例代码

```js
var videoPlayer = api.require('videoPlayer');
videoPlayer.addEventListener({
    name:'leftUp'
}, function(ret, err){		
	if( ret ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**removeEventListener**<div id="19"></div>

移除动作监听

removeEventListener({params})

##params

name：

- 类型：字符串
- 描述：（可选项）所要移除的监听的动作名称
- 取值范围：
   - 'leftUp'：      播放器靠左的二分之一内的上滑事件，每滑动5（百分比）回调执行一次
   - 'leftDown'：    播放器靠左的二分之一内的下滑事件，每滑动5（百分比）回调执行一次
   - 'rightUp'：     播放器靠右的二分之一内的上滑事件，每滑动5（百分比）回调执行一次
   - 'rightDown'：   播放器靠右的二分之一内的下滑事件，每滑动5（百分比）回调执行一次
   - 'swipeLeft'：   播放器上的左滑事件，每滑动5（百分比）回调执行一次
   - 'swipeRight'：  播放器上的右滑事件，每滑动5（百分比）回调执行一次
   - 'click'：       点击播放器事件（单击手势）
   - 'doubleClick'： 双击播放器事件（单击手势）
   - 'play'：        播放事件，包括开始播放（start）、正在播放（playing）、暂停（pause）、停止（stop）、播放完成（complete）

##示例代码

```js
var videoPlayer = api.require('videoPlayer');
videoPlayer.removeEventListener({
    name: 'leftUp'
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setRect**<div id="20"></div>

设置视频播放器位置、尺寸，以及是否全屏

setRect({params}, callback(ret, err))

##params

rect：

- 类型：JSON 对象
- 描述：（可选项）模块的位置及尺寸
- 内部字段：

```js
{
    x: 0,         //（可选项）数字类型；模块左上角的 x 坐标（相对于所属的 Window 或 Frame）；默认：0
    y: 0,         //（可选项）数字类型；模块左上角的 y 坐标（相对于所属的 Window 或 Frame）；默认：0
    w: 'auto',    //（可选项）数字类型；模块的宽度；当w为'auto'时，w为所属的 Window 或 Frame 的宽度，默认：open中设置的宽度
    h: 300        //（可选项）数字类型；模块的高度；当h为'auto'时，h为所属的 Window 或 Frame 的高度，默认：open中设置的高度
}
```

fullscreen：

- 类型：布尔类型
- 描述：（可选项）模块的位置及尺寸是否全屏（不显示状态栏）
- 默认值：false（不随全屏）

##示例代码

```js
var videoPlayer = api.require('videoPlayer');
videoPlayer.setRect({
    rect:{
	    x: 0,
	    y: 0,
		w: 'auto',
		h: 'auto'
	},
	fullscreen: true
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
