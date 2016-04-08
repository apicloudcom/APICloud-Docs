/*
Title: UIPullRefreshFlash
Description: UIPullRefreshFlash
*/

<div class="outline">
[setCustomRefreshHeaderInfo](#m2)

[refreshHeaderLoading](#m3)

[refreshHeaderLoadDone](#m4)

</div>

<div id="m1"></div>

#**概述**

随着用户对 App 使用体验的要求不断提升，传统的下拉刷新动画和模式已经无法满足用户挑剔的视觉体验。为满足广大开发者对下拉刷新功能的需求，我们推出了最新最炫的下拉刷新模块助您提升 App 逼格。

从用户体验考虑，下拉刷新的实现不能简单粗暴的用一张 GIF 图片来完成，我们需要遵照原生动画理念，使用关键帧（即多张具有微小差别的图片）来完成完整的动画过程。本模块下拉刷新效果就是由一组关键帧图片配合补间动画实现的。

**下拉刷新简介**

下拉刷新是指在一个可上下拖动查看内容的支持弹动功能的窗体（frame、window）中，用户通过下拉触发刷新数据事件从而加载数据刷新页面的过程。

此过程可拆分为四个组成部分：

- 一，下拉过程
- 二，下拉高度达到一定阈值后触发加载事件
- 三，加载状态
- 四，数据加载完成后刷新页面并停止加载状态（恢复常态）

**模块概述**

UIPullRefreshFlash 模块对引擎新推出的下拉刷新接口进行了一层封装，App 可以通过此模块来实现带炫酷动画效果的下拉刷新功能。使用此模块，在用户下拉时本模块会随用户下拉高度而放大缩小下拉出的提示图标，同时会随用户下拉高度播放一组关键帧图片，该图片数组是通过 api.setCustomRefreshHeaderInfo 接口以图片数组（参考下文 pull 参数）的形式传给模块的，每下拉一定距离（阈值/图片数量），播放一帧图片；当下拉高度达到一定阈值后触发加载事件：进入加载状态时，刷新提示图标开始播放加载关键帧图片数组，此时图片每帧间隔为 50 毫秒，同时将下拉刷新事件回发给前端。前端得到下拉刷新事件后开始加载数据；数据加载完毕，调用接口 api.refreshHeaderLoadDone 以停止加载状态；

**模块使用攻略**

对于 APICloud 平台上的普通模块，在相应接口调用前需要先 require 该模块，但由于本模块是基于引擎下拉刷新功能扩展的模块，所以本模块使用方法比较特殊。可以不必 require 模块，改为在 config.xml 文件内配置模块。

config.xml 文件配置示例如下：

	<preference name="customRefreshHeader" value="UIPullRefreshFlash"/>

在 config.xml 配置后，则本模块为全局对象，可以在任意可弹动的窗体（frame、window）中调用 api.setCustomRefreshHeaderInfo 接口设置该下拉刷新样式，以及开始、停止刷新加载状态（api.refreshHeaderLoading、api.refreshHeaderLoadDone）。

若想在不同的 window 或 frame 使用不同的下拉刷新模块，开发者可以在 window 或 frame 打开时传入参数 customRefreshHeader:'下拉刷新模的块名'，以指定该窗体的下拉刷新模块。如：

```js
{
api.openFrame({
            name: 'UIPullRefreshFlash-con',
            url: './UIPullRefreshFlash-con.html',
            customRefreshHeader: 'UIPullRefreshFlash',
            bounces: true,
            rect: {
                x: offset.l,
                y: offset.t + offset.h,
                w: offset.w,
                h: bodyHeight - offset.h
            }
        });
}
```

*注意：本模块无接口，模块的所有功能都通过 api 对象的相应接口实现*

#**功能接口**

<div id="m2"></div>

##**setCustomRefreshHeaderInfo**

配置下拉刷新样式

api.setCustomRefreshHeaderInfo({params}, callback())

###params

- 类型：JSON 对象类型
- 描述：启用下拉刷新及其样式的配置
- 内部字段：

```js
{
	bgColor: '#C0C0C0',                             //（可选项）字符串类型；下拉刷新的背景设置，支持rgb、rgba、#，该背景大小同当前 window 或 frame 的宽高；默认：#C0C0C0
	image: {                                        //JSON 对象类型；下拉刷新相关图片设置
		pull: ['fs://t1.png','fs://t2.png',...],    //数组类型；组成下拉过程的动画关键帧图片数组，这组图片随下拉高度同步放大缩小，同时自动播放关键帧图片：每下拉一定距离（阈值/图片数量），播放一帧关键帧图片；图片规格为正方形，如：50*50、100*100
		load: ['fs://t1.png','fs://t2.png',...]     //数组类型；组成下拉刷新加载状态动画的关键帧图片数组，图片为正方形的，如：50*50、100*100，建议开发者传大小合适的图片以适配高分辨率手机屏幕
	}
}
```
##callback()

当用户下拉的高度达到阈值（本下拉模块的阈值为60）后抬起拖动手指 触发刷新事件，模块将该事件回调给前端。

##示例代码

```js
api.setCustomRefreshHeaderInfo({
    bgColor: '#C0C0C0',
    image: {
        pull: [
            'widget://image/refresh/dropdown0.png', 
            'widget://image/refresh/dropdown1.png',
            'widget://image/refresh/dropdown2.png',
            'widget://image/refresh/dropdown3.png',
            'widget://image/refresh/dropdown4.png',
            'widget://image/refresh/dropdown5.png',
            'widget://image/refresh/dropdown6.png'
        ],
        load: [ 
            'widget://image/refresh/loading0.png', 
            'widget://image/refresh/loading1.png',
            'widget://image/refresh/loading2.png', 
            'widget://image/refresh/loading3.png',
            'widget://image/refresh/loading4.png'
        ]
    }
}, function() {
    //下拉刷新被触发，自动进入加载状态，使用 api.refreshHeaderLoadDone() 手动结束加载中状态
    //下拉刷新被触发，使用 api.refreshHeaderLoadDone() 结束加载中状态  
	alert('开始加载刷新数据，摇一摇停止加载状态');
	api.addEventListener({
	   name:'shake'
	},function(ret,err){
	   api.refreshHeaderLoadDone()
	});
});
```

##可用性

IOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m3"></div>

##**refreshHeaderLoading**

手动开始下拉刷新的加载状态，**下拉刷新状态亦可通过用户下拉到阈值自动触发**

api.refreshHeaderLoading()


##示例代码

```js
   api.refreshHeaderLoading();
```

##可用性

IOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m4"></div>

##**refreshHeaderLoadDone**

手动停止下拉刷新的加载状态

api.refreshHeaderLoadDone()


##示例代码

```js
  api.refreshHeaderLoadDone();
```

##可用性

IOS系统，Android系统

可提供的1.0.0及更高版本