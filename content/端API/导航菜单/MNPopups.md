/*
Title: MNPopups
Description: MNPopups
*/
<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">
<div class="outline">
[open](#1)

[reloadData](#2)

[deleteItem](#3)

[insertItem](#4)

[updateItem](#5)

[close](#6)

[show](#7)

[hide](#8)
</div>

#**概述**

MNPopups 封装了一个带有方向指针的弹出气泡式菜单视图。该菜单视图根据开发者指定的指针坐标（position）、指针在菜单视图的位置（styles->pointer）和菜单视图大小（rect），确定弹出的菜单视图坐标，然后以动画的形式弹出一个 rect 大小的菜单视图。所弹出的菜单依附于当前主窗口，其生命周期也同当前主窗口；点击非菜单区域亦可以动画的形式隐藏该菜单栏。支持上、下、左、右四种指针方向指向；支持列表项的增、删、改，支持批量更新数据。

styles 参数可自定义及列表的样式。datas 参数可自定义列表数据源。如果列表项太多而超过 open-> rect 区域，可上下滚动查看。

![图片说明](/img/docImage/MNPopups.jpg)

#**open**<div id="1"></div>

打开

open({params}, callback(ret, err))

##params

rect:

- 类型：JSON 类型
- 描述：（可选项）弹出模块的大小配置
- 默认值：见内部字段
- 内部字段：

```js
{         
    w: 100,                         //（可选项）数字类型；弹出模块的宽度；默认值：100
    h: 180                          //（可选项）数字类型；弹出模块的高度；默认值：180
}
```

position：

- 类型：JSON 对象
- 描述：（可选项）弹出模块的指针位置配置
- 默认值：见内部字段
- 内部字段：

```js
{       
    x: api.winWidth-10,             //（可选项）数字类型；弹出模块指针的 x 坐标；默认值：主窗口宽度-10
    y: 0                            //（可选项）数字类型；弹出模块指针的 y 坐标；默认值：0
}
```

animation：

- 类型：布尔类型
- 描述：弹出和隐藏菜单时是否带动画效果（时长300毫秒）；弹出时从指针位置由小到大的渐大动画，隐藏时由大到小的渐小动画回到指针位置处隐藏
- 默认：true

styles：

- 类型：JSON 类型
- 描述：模块整体样式
- 内部字段： 

```js
{
    mask: 'rgba(0,0,0,0.2)'          //（可选项）字符串类型；遮罩层背景，支持 rgb、rgba、#；默认：rgba(0,0,0,0.2)
    bg: '#fff',                      //（可选项）字符串类型；列表背景，支持rgb、rgba、#；默认：#fff
    cell: {                          //（可选项）列表项的样式配置
		bg:{                         //（可选项）JSON对象；背景配置
			normal: '',              //（可选项）字符串类型；列表项的背景，支持rgb、 rgba、#、img；默认：#fff
			highlight: ''            //（可选项）字符串类型；列表项的高亮背景，支持 rgb、rgba、#、img；默认：bg
		},                        
		h: 45,                       //（可选项）数字类型；列表项的高度；默认：45
		title: {                     //（可选项）JSON 类型；列表项标题样式设置，上下居中显示
			marginL: 45,             //（可选项）数字类型；列表项标题相对于列表项左边的间距大小；默认：45
			color: '#636363',        //（可选项）字符串类型；列表项标题文字颜色，支持rgb、rgba、#；默认：#636363
			size: 12,                //（可选项）数字类型；列表项标题字体大小；默认：12
		},
		icon: {                      //（可选项）JSON 类型；列表项图标的样式设置，上下居中
			marginL: 10,             //（可选项）数字类型；图标相对于列表项左边的间距大小；默认：10
			w: 25,                   //（可选项）数字类型；图标的宽度；默认：25
			h: 25,                   //（可选项）数字类型；图标的高度；默认：同 w
			corner: 2                //（可选项）数字类型；图标的圆角半径；默认：2
		}
    },
    pointer: {                       //（可选项）JSON类型；尖角配置
        size: 7,                     //（可选项）数字类型；尖角大小，该尖角为等边三角形，本参数为该三角形边长；默认：7
        xPercent: 90,                //（可选项）数字类型；尖角底边中点 x 坐标占模块宽度的百分比；默认：90
        yPercent: 0,                 //（可选项）数字类型；尖角底边中点 y 坐标占模块高度的百分比；默认：0
        orientation: 'downward'      //（可选项）字符串类型；气泡菜单弹出方向，取值范围如下：
                                     // upward：向上弹出
                                     // downward：向下弹出  
                                     // leftward：向左边弹出
                                     // rightward：向右边弹出
    }
}
```

datas：

- 类型：数组类型
- 描述：菜单列表数据源
- 内部字段：

```js                       
[{                           
	title: '添加朋友',                //字符串类型；列表标题文字
	icon: 'fs://creater.png'         //字符串类型；图标地址，支持本地路径（widget://、fs://）
}]
```

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	eventType: 'show',  // 字符串类型；交互事件类型,取值范围如下：
                        // show：模块加载成功并显示在屏幕上的事件（show接口不会触发此事件）
                        // click：点击菜单列表项
			            
	index: 0            // 数字类型；点击目标对应菜单列表项的索引，仅当 eventType 为 click 时有效
}
```

##示例代码

```js
var mnPopups = api.require('MNPopups');
mnPopups.open({
    rect: {
	    w: 100,
	    h: 180
    },
    position: {       
		x: api.winWidth-10,             
		y: 0                            
	},
    styles: {
		mask: 'rgba(0,0,0,0.2)',
		bg: '#eee',                        
		cell: {                            
			bg:{ 
				normal: '',              
				highlight: ''            
			},                   
	    	h: 45,                         
	    	title: {                      
	    		marginL: 45,               
	    		color: '#636363',          
	    		size: 12,                 
	    	},
	    	icon: {                        
	    		marginL: 10,               
	    		w: 25,                     
	    		h: 25,                     
	    		corner: 2                  
	    	}
	    },
	    pointer: {
			size: 7,                     
			xPercent: 90,                
			yPercent: 0,                 
			orientation: 'downward'
		}
    },
    datas: [{                           
		title: '添加朋友',  
		icon: 'fs://MNPopups/addFriends.png'
	},
	{                           
		title: '扫一扫',  
		icon: 'fs://MNPopups/scan.png'
	},
	{                           
		title: '面对面快传',  
		icon: 'fs://MNPopups/send.png'
	}],
	animation: true
}, function(ret) {
    if (ret) {
        alert(JSON.stringify(ret));
    }
});
```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**reloadData**<div id="2"></div>

刷新 MNPopups 列表数据

reloadData({params})

##params

datas：

- 类型：数组类型
- 描述：（可选项）菜单列表数据源，若为空则等待 reloadData 接口刷新后显示该模块
- 内部字段：

```js                       
[{                           
	title: '添加朋友',         //字符串类型；列表标题文字
	icon: 'fs://creater.png'  //字符串类型；图标地址，支持本地路径（widget://、fs://）
}]
```

##示例代码

```js
var mnPopups = api.require('MNPopups');
mnPopups.reloadData({
    datas: [{                           
		title: '添加群',  
		icon: 'fs://MNPopups/addGroup.png'
	},
	{                           
		title: '发送到电脑',  
		icon: 'fs://MNPopups/sendComputer.png'
	}]
});

```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**deleteItem**<div id="3"></div>

从菜单列表中移除指定索引的数据

deleteItem({params})

##params

index：

- 类型：数字类型
- 描述：数据列表的索引
- 默认值：0

##示例代码

```js
var mnPopups = api.require('MNPopups');
mnPopups.deleteItem({
    index:1
});
```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**insertItem**<div id="4"></div>

从菜单列表中的指定位置插入数据

insertItem({params})

##params

index：

- 类型：数字类型
- 描述：（可选项）数据列表的索引
- 默认值：列表最后一条数据的索引

data：

- 类型：JSON 类型
- 描述：数据源
- 内部字段：

```js
{                                    
	title: '创建群组',         //字符串类型；列表标题文字
	icon: 'fs://creater.png'  //字符串类型；图标地址，支持本地路径（widget://、fs://）
}

```

##示例代码

```js
var mnPopups = api.require('MNPopups');
mnPopups.insertItem({
    index: 1,
    data: {
        title: '创建讨论组',         
        icon: 'fs://creater.png'  
    }
});

```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**updateItem**<div id="5"></div>

更新指定分组中指定位置的数据

updateItem({params})

##params

index：

- 类型：数字类型
- 描述：（可选项）数据列表的索引
- 默认值：0

data：

- 类型：JSON 类型
- 描述：数据源
- 内部字段：

```js
{                             //JSON 数组类型；菜单列表项的数据
	title: '添加朋友',         //字符串类型；列表标题文字
	icon: 'fs://creater.png'  //字符串类型；图标地址，支持本地路径（widget://、fs://）
}
```

##示例代码

```js
var mnPopups = api.require('MNPopups');
mnPopups.updateItem({
    index: 1,
    data: {                          
		title: '付款',  
		icon: 'fs://MNPopups/pay.png'
    }
});

```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**close**<div id="6"></div>

关闭 MNPopups 列表视图

close()

##示例代码

```js
var obj = api.require('MNPopups');
obj.close();
```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**show**<div id="7"></div>

显示已隐藏的 MNPopups 列表视图

show()

##示例代码

```js
var mnPopups = api.require('MNPopups');
mnPopups.show();
```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="8"></div>

隐藏 MNPopups 列表视图，并没有从内存里清除

hide()

示例代码

```js
var mnPopups = api.require('MNPopups');
mnPopups.hide();
```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本