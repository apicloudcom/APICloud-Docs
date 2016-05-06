/*
Title: groupList
Description: groupList
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：开发者</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[close](#2)

[reloadData](#3)

[removeCellAt](#4)

[addCellAt](#5)

[updateCellAt](#6)

[setRefreshHeader](#7)

[show](#8)

[hide](#9)
</div>

#**概述**

groupList 封装了一个列表控件，实现了一个可向左拖动 cell 的列表视图。开发者可根据需求自定义列表的元素布局，亦可自定义相关字段的样式。支持设置下拉刷新和上拉加载更多事件。支持删除、刷新、在指定位置（index）插入 cell 数据。**本模块是由第三方模块开发者提供，使用本模块需在线云编译安装包**

![图片说明](/img/docImage/groupList.jpg)

#**open**<div id="1"></div>

打开

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

styles：

- 类型：JSON 类型
- 描述：模块整体样式
- 内部字段： 

```js
{
    bg: '#eee',                        //（可选项）字符串类型；列表背景，支持 rgb、rgba、#、img；默认：'rgba(0,0,0,0)'
    title: {                           //（可选项）JSON 对象类型，分组标题的通用样式设置
    	bg: '#E0E0E0',                 //（可选项）字符串类型；分组标题的背景，支持 rgb、rgba、#、img；默认：'#E0E0E0'
    	h: 25,                         //（可选项）数字类型；分组标题的高度；默认：25
    	align: 'left',                 //（可选项）字符串类型；分组标题的对齐方式，可为 left|center|right；默认：left
    	color: '#838383',              //（可选项）字符串类型；分组标题的字体颜色，支持 rgb、rgba、#；默认：#838383
    	size: 15,                      //（可选项）数字类型；分组标题的字体大小；默认：15
        marginT: 7,                    //（可选项）数字类型；分组标题的上边距；默认：7
        marginL: 18                    //（可选项）数字类型；分组标题的左边距；默认：18
    },
    cell: {                            //（可选项）JSON 对象类型，分组子项的通用样式
    	bg: '#fff',                    //（可选项）字符串类型；分组子项的背景，支持 rgb、rgba、#、img；默认：#fff
    	h: 68,                         //（可选项）数字类型；分组子项的高度；默认：68
    	main: {                        //（可选项）JSON 类型；主标题样式设置，当未设置副标题时不显示副标题且不占高度，主标题会自己上下居中显示
    		marginL: 74,               //（可选项）数字类型；主标题相对于分组子项左边的间距大小；默认：74
    		color: '#636363',          //（可选项）字符串类型；主标题文字颜色，支持 rgb、rgba、#；默认：#636363
    		size: 13,                  //（可选项）数字类型；主标题字体大小；默认：13
    	},
    	sub: {                         //（可选项）JSON 类型；副标题样式设置；当未设置时不显示副标题且不占高度，主标题会自己上下居中显示
    		marginL: 74,               //（可选项）数字类型；副标题相对于分组子项左边的间距大小；默认：74
    		marginT: 8,               //（可选项）数字类型；副标题和主标题之间的间隙大小；默认：8
    		color: '#999999',          //（可选项）字符串类型；副标题文字颜色，支持 rgb、rgba、#；默认：#999999
    		size: 12,                  //（可选项）数字类型；副标题字体大小；默认：12
    	},
    	icon: {                        //（可选项）JSON 类型；头像的样式设置
    		marginL: 15,               //（可选项）数字类型；头像相对于分组子项左边的间距大小；默认：15
    		marginT: 9,                //（可选项）数字类型；头像相对于分组子项上边的间距大小；默认：9
    		w: 50,                     //（可选项）数字类型；头像的宽度；默认：50
    		h: 50,                     //（可选项）数字类型；头像的高度；默认：同 w
    		corner: 25                 //（可选项）数字类型；头像的圆角半径；默认：2
    	},
    	handler: {                     //（可选项）JSON 类型；cell右边拉手图标的样式设置；若不传则不显示
    		url: 'fs://handler.png',   //JSON 类型；拉手图标的图片地址，要求本地路径（widget://、fs://）；未设置时认为 allowHandler 为 false
    		marginR: 20,               //（可选项）数字类型；拉手图标相对于分组子项右边的间距大小；默认：20
    		marginT: 25,               //（可选项）数字类型；拉手图标相对于分组子项上边的间距大小；默认：25
    		w: 18,                     //（可选项）数字类型；拉手图标的宽度；默认：18
    		h: 18                      //（可选项）数字类型；拉手图标的高度；默认：同 w
    	},
    	options:[{                     //（可选项）数组类型；cell 左滑后显示的选项按钮样式组成的数组；未设置则 cell 不可侧滑，侧滑距离为当前cell所有侧滑按钮总宽度。侧滑按钮从右依次往左排列，其索引由0开始
			w: 76,                     //（可选项）数字类型；每个 option 的宽度；默认：76
			bg: 'rgba(0,0,0,0)' ,      //（可选项）字符串类型；每个 option 的背景，支持 rgb、rgba、#、img；默认：'rgba(0,0,0,0)'
			title: '关注',              //（可选项）字符串类型；侧滑按钮上的标题，若不传则不显示
    	    align: 'center',           //（可选项）字符串类型；侧滑按钮标题的对齐方式，可为 left|center|right；默认：center
			marginB: 13,               //（可选项）数字类型；侧滑按钮标题距离按钮下边间隙大小；默认：13
			color: '#fff',             //（可选项）字符串类型；侧滑按钮标题的颜色，支持 rgb、rgba、#；默认：'#fff'
			size: 11                   //（可选项）数字类型；侧滑按钮标题文字大小；默认：11
		}],
	    line: {                        //（可选项）JSON 类型；同 group 下的 cell 之间的分隔线样式
	    	h: 0.8,                    //（可选项）数字类型；分隔线的高度；默认：0.8
	    	marginL: 0,                //（可选项）数字类型；分隔线距 group 左侧的内边距；默认：0
	    	marginR: 0,                //（可选项）数字类型；分隔线距 group 右侧的内边距；默认：0
	    	bg: '#eee',                //（可选项）字符串类型；分隔线的颜色，支持：rgb、rgba、#；默认：'#eee'
		}
    }
}
```

datas：

- 类型：数组类型
- 描述：（可选项）列表数据源，若为空则等待reloadData接口刷新后显示该模块
- 内部字段：

```js
[{                                    //JSON 对象类型组成的数组；一个分组的数据信息
	title: '分组标题',                 //（可选项）字符串类型；分组标题文字，若不传则不显示
	cells: [{                         //JSON 数组类型；该分组中的 cell 数据
		icon: 'fs://creater.png', //字符串类型；图标地址，支持本地和网络资源路径（widget://、fs://、http://、https://），若是网络路径则图片会被缓存到本地
		main: '张泉灵',                //字符串类型；主标题文字
		sub: '活跃值：200' ,           //（可选项）字符串类型；副标题
    	options:[{                    //（可选项）数组类型；cell 左滑后显示的选项按钮样式组成的数组；若未设置则以styles->cell->options为准，若亦未设置，则该cell不可侧滑
			w: 76,                    //（可选项）数字类型；每个 option 的宽度；默认：76
			bg: 'rgba(0,0,0,0)' ,     //（可选项）字符串类型；每个 option 的背景，支持 rgb、rgba、#、img；默认：'rgba(0,0,0,0)'
			title: '关注',             //（可选项）字符串类型；侧滑按钮上的标题，若不传则不显示
    	    align: 'center',          //（可选项）字符串类型；侧滑按钮标题的对齐方式，可为 left|center|right；默认：center
			marginB: 13,              //（可选项）数字类型；侧滑按钮标题距离按钮下边间隙大小；默认：13
			color: '#fff',            //（可选项）字符串类型；侧滑按钮标题的颜色，支持 rgb、rgba、#；默认：'#fff'
			size: 11                  //（可选项）数字类型；侧滑按钮标题文字大小；默认：11
		}],
    	handler: {                    //（可选项）JSON 类型；cell右边拉手图标的样式设置；若不传则以styles->cell->handler为准，若亦未设置，则该cell不显示拉手图标
    		url: 'fs://handler.png',  //JSON 类型；拉手图标的图片地址，要求本地路径（widget://、fs://）；未设置时认为 allowHandler 为 false
    		marginR: 20,              //（可选项）数字类型；拉手图标相对于分组子项右边的间距大小；默认：20
    		marginT: 25,              //（可选项）数字类型；拉手图标相对于分组子项上边的间距大小；默认：25
    		w: 18,                //（可选项）数字类型；拉手图标的宽度；默认：18
    		h: 18                //（可选项）数字类型；拉手图标的高度；默认：同 w
    	}
	}]
}]
```

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

fixed：

- 类型：布尔
- 描述：（可选项）是否将模块视图固定到窗口上，不跟随窗口上下滚动
- 默认：true

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	eventType: 'show',  //字符串类型；交互事件类型
			            //取值范围如下：
				        //show（模块加载成功）
			            //clickOption（点击侧滑出现的右侧按钮）
			            //clickContent（点击列表项的内容，除了配图和备注以外的区域）
			            //clickImg（点击列表项的配图）
			            //clickHandler（点击列表项右拉手按钮）
	groupIndex: 0,      //数字类型；点击目标对应数据源的 group 的索引
	cellIndex: 1,       //数字类型；点击目标对应数据源中 cell 的索引
    optionIndex: 0 ,    //数字类型；eventType 为 clickOption 时有效，被点击 option 对应的索引
    cellData: {}         //JSON对象；open时传入的 cell 的原始数据              
}
```

##示例代码

```js
var groupList = api.require('groupList');
groupList.open({
    rect: {
        x: 0,
        y: 0,
        w: 320,
        h: 480
    },
    styles: {
        bg: '#eee',
        title: {
            bg: '#E0E0E0',
            h: 25,
            align: 'left',
            color: '#838383',
            size: 15,
            marginT:7,
            marginL:18
        },
        cell: {
            bg: '#fff',
            h: 68,
            main: {
                marginL: 74,
                marginT: 17,
                color: '#636363',
                size: 13,
            },
            sub: {
                marginL: 74,
                marginT: 8,
                color: '#999999',
                size: 12,
            },
            icon: {
                marginL: 15,
                marginT: 9,
                w: 50,
                h: 50,
                corner: 25
            },
            handler: {
                url: 'fs://handler.png',
                marginR: 20,
                marginT: 25,
                w: 18,
                h: 18
            },
            options: [{
                w: 76,
                bg: 'rgba(0,0,0,0)',
                title: '关注',
                align: 'center',
                marginB: 13,
                color: '#fff',
                size: 11
            }],
            line: {
                h: 0.8,
                marginL: 0,
                marginR: 0,
                bg: '#eee',
            }
        }
    },
    datas: [{
        title: '分组标题',
        cells: [{
            icon: 'fs://creater.png',
            main: '张泉灵',
            sub: '活跃值：200',
            options: [{
                w: 76,
                bg: 'rgba(0,0,0,0)',
                title: '关注',
                align: 'center',
                marginB: 13,
                color: '#fff',
                size: 11
            }],
            handler: {
                url: 'fs://handler.png',
                marginR: 20,
                marginT: 25,
                w: 18,
                h: 18
            }
        }]
    }],
    fixedOn: api.frameName,
    fixed: true
}, function(ret, err) {
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

#**close**<div id="2"></div>

关闭 groupList 列表视图

close()

##示例代码

```js
var groupList = api.require('groupList');
groupList.close();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**reloadData**<div id="3"></div>

刷新列表数据

reloadData({params})

##params

datas：

- 类型：数组类型
- 描述：（可选项）列表数据源，若为空，则仅停止下拉刷新状态
- 内部字段：

```js
[{                                    //JSON 对象类型组成的数组；一个分组的数据信息
	title: '分组标题',                 //（可选项）字符串类型；分组标题文字，若不传则不显示
	cells: [{                         //JSON 数组类型；该分组中的 cell 数据
		icon: 'fs://creater.png', //字符串类型；图标地址，支持本地和网络资源路径（widget://、fs://、http://、https://），若是网络路径则图片会被缓存到本地
		main: '张泉灵',                //字符串类型；主标题文字
		sub: '活跃值：200' ,           //（可选项）字符串类型；副标题
    	options:[{                    //（可选项）数组类型；cell 左滑后显示的选项按钮样式组成的数组；若未设置则以open->styles->cell->options为准，若亦未设置，则该cell不可侧滑
			w: 76,                    //（可选项）数字类型；每个 option 的宽度；默认：76
			bg: 'rgba(0,0,0,0)' ,     //（可选项）字符串类型；每个 option 的背景，支持 rgb、rgba、#、img；默认：'rgba(0,0,0,0)'
			title: '关注',             //（可选项）字符串类型；侧滑按钮上的标题，若不传则不显示
    	    align: 'center',          //（可选项）字符串类型；侧滑按钮标题的对齐方式，可为 left|center|right；默认：center
			marginB: 13,              //（可选项）数字类型；侧滑按钮标题距离按钮下边间隙大小；默认：13
			color: '#fff',            //（可选项）字符串类型；侧滑按钮标题的颜色，支持 rgb、rgba、#；默认：'#fff'
			size: 11                  //（可选项）数字类型；侧滑按钮标题文字大小；默认：11
		}],
    	handler: {                    //（可选项）JSON 类型；cell右边拉手图标的样式设置；若不传则以open->styles->cell->handler为准，若亦未设置，则该cell不显示拉手图标
    		url: 'fs://handler.png',  //JSON 类型；拉手图标的图片地址，要求本地路径（widget://、fs://）；未设置时认为 allowHandler 为 false
    		marginR: 20,              //（可选项）数字类型；拉手图标相对于分组子项右边的间距大小；默认：20
    		marginT: 25,              //（可选项）数字类型；拉手图标相对于分组子项上边的间距大小；默认：25
    		w: 18,                //（可选项）数字类型；拉手图标的宽度；默认：18
    		h: 18                //（可选项）数字类型；拉手图标的高度；默认：同 w
    	}
	}]
}]
```

##示例代码

```js
var groupList = api.require('groupList');
groupList.reloadData({
    datas: [{
        title: '分组标题',
        cells: [{
            icon: 'fs://creater.png',
            main: '张泉灵',
            sub: '活跃值：200',
            options: [{
                w: 76,
                bg: 'rgba(0,0,0,0)',
                title: '关注',
                align: 'center',
                marginB: 13,
                color: '#fff',
                size: 11
            }],
            handler: {
                url: 'fs://handler.png',
                marginR: 20,
                marginT: 25,
                w: 18,
                h: 18
            }
        }]
    }]
});

```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**removeCellAt**<div id="4"></div>

从分组列表中移除指定索引的数据

removeCellAt({params})

##params

groupIndex：

- 类型：字符串类型
- 描述：要删除数据的分组 index

cellIndex：

- 类型：数字类型
- 描述：要删除数据在 cells 中的 index

##示例代码

```js
var groupList = api.require('groupList');
groupList.removeCellAt({
	groupIndex: 1,
	cellIndex: 1
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**addCellAt**<div id="5"></div>

在指定分组中的指定位置插入数据

addCellAt({params})

##params

groupIndex：

- 类型：字符串类型
- 描述：插入目标分组的 index

cellIndex：

- 类型：数字类型
- 描述：（可选项）要插入的数据的索引下标
- 默认：将新数据附加到当前分组最后一条数据后

cell：

- 类型：JSON 类型
- 描述：数据源
- 内部字段：

```js
{                                    //JSON 数组类型；该分组中的 cell 数据
	icon: 'fs://creater.png', //字符串类型；图标地址，支持本地和网络资源路径（widget://、fs://、http://、https://），若是网络路径则图片会被缓存到本地
	main: '张泉灵',                //字符串类型；主标题文字
	sub: '活跃值：200' ,           //（可选项）字符串类型；副标题
	options:[{                    //（可选项）数组类型；cell 左滑后显示的选项按钮样式组成的数组；若未设置则以open->styles->cell->options为准，若亦未设置，则该cell不可侧滑
		w: 76,                    //（可选项）数字类型；每个 option 的宽度；默认：76
		bg: 'rgba(0,0,0,0)' ,     //（可选项）字符串类型；每个 option 的背景，支持 rgb、rgba、#、img；默认：'rgba(0,0,0,0)'
		title: '关注',             //（可选项）字符串类型；侧滑按钮上的标题，若不传则不显示
	    align: 'center',          //（可选项）字符串类型；侧滑按钮标题的对齐方式，可为 left|center|right；默认：center
		marginB: 13,              //（可选项）数字类型；侧滑按钮标题距离按钮下边间隙大小；默认：13
		color: '#fff',            //（可选项）字符串类型；侧滑按钮标题的颜色，支持 rgb、rgba、#；默认：'#fff'
		size: 11                  //（可选项）数字类型；侧滑按钮标题文字大小；默认：11
	}],
	handler: {                    //（可选项）JSON 类型；cell右边拉手图标的样式设置；若不传则以open->styles->cell->handler为准，若亦未设置，则该cell不显示拉手图标
		url: 'fs://handler.png',  //JSON 类型；拉手图标的图片地址，要求本地路径（widget://、fs://）；未设置时认为 allowHandler 为 false
		marginR: 20,              //（可选项）数字类型；拉手图标相对于分组子项右边的间距大小；默认：20
		marginT: 25,              //（可选项）数字类型；拉手图标相对于分组子项上边的间距大小；默认：25
		w: 18,                //（可选项）数字类型；拉手图标的宽度；默认：18
		h: 18                //（可选项）数字类型；拉手图标的高度；默认：同 w
	}
}

```

##示例代码

```js
var groupList = api.require('groupList');
groupList.addCellAt({
    groupIndex: 1,
    cellIndex: 2,
    cell: {
        icon: 'fs://creater.png',
        main: '张泉灵',
        sub: '活跃值：200',
        options: [{
            w: 76,
            bg: 'rgba(0,0,0,0)',
            title: '关注',
            align: 'center',
            marginB: 13,
            color: '#fff',
            size: 11
        }],
        handler: {
            url: 'fs://handler.png',
            marginR: 20,
            marginT: 25,
            w: 18,
            h: 18
        }
    }
});

```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**updateCellAt**<div id="6"></div>

更新指定分组中指定位置的数据

updateCellAt({params})

##params

groupIndex：

- 类型：字符串类型
- 描述：更新目标分组的 index

cellIndex：

- 类型：数字类型
- 描述：要更新数据的索引下标

cell：

- 类型：JSON 类型
- 描述：数据源
- 内部字段：

```js
{                                    //JSON 数组类型；该分组中的 cell 数据
		icon: 'fs://creater.png', //字符串类型；图标地址，支持本地和网络资源路径（widget://、fs://、http://、https://），若是网络路径则图片会被缓存到本地
		main: '张泉灵',                //字符串类型；主标题文字
		sub: '活跃值：200' ,           //（可选项）字符串类型；副标题
    	options:[{                    //（可选项）数组类型；cell 左滑后显示的选项按钮样式组成的数组；若未设置则以open->styles->cell->options为准，若亦未设置，则该cell不可侧滑
			w: 76,                    //（可选项）数字类型；每个 option 的宽度；默认：76
			bg: 'rgba(0,0,0,0)' ,     //（可选项）字符串类型；每个 option 的背景，支持 rgb、rgba、#、img；默认：'rgba(0,0,0,0)'
			title: '关注',             //（可选项）字符串类型；侧滑按钮上的标题，若不传则不显示
    	    align: 'center',          //（可选项）字符串类型；侧滑按钮标题的对齐方式，可为 left|center|right；默认：center
			marginB: 13,              //（可选项）数字类型；侧滑按钮标题距离按钮下边间隙大小；默认：13
			color: '#fff',            //（可选项）字符串类型；侧滑按钮标题的颜色，支持 rgb、rgba、#；默认：'#fff'
			size: 11                  //（可选项）数字类型；侧滑按钮标题文字大小；默认：11
		}],
    	handler: {                    //（可选项）JSON 类型；cell右边拉手图标的样式设置；若不传则以open->styles->cell->handler为准，若亦未设置，则该cell不显示拉手图标
    		url: 'fs://handler.png',  //JSON 类型；拉手图标的图片地址，要求本地路径（widget://、fs://）；未设置时认为 allowHandler 为 false
    		marginR: 20,              //（可选项）数字类型；拉手图标相对于分组子项右边的间距大小；默认：20
    		marginT: 25,              //（可选项）数字类型；拉手图标相对于分组子项上边的间距大小；默认：25
    		w: 18,                //（可选项）数字类型；拉手图标的宽度；默认：18
    		h: 18                //（可选项）数字类型；拉手图标的高度；默认：同 w
    	}
}
```

##示例代码

```js
var groupList = api.require('groupList');
groupList.updateCellAt({
    groupIndex: 1,
    cellIndex: 2,
    cell: {
        icon: 'fs://creater.png',
        main: '张泉灵',
        sub: '活跃值：200',
        options: [{
            w: 76,
            bg: 'rgba(0,0,0,0)',
            title: '关注',
            align: 'center',
            marginB: 13,
            color: '#fff',
            size: 11
        }],
        handler: {
            url: 'fs://handler.png',
            marginR: 20,
            marginT: 25,
            w: 18,
            h: 18
        }
    }
});

```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setRefreshHeader**<div id="7"></div>

设置下拉刷新样式

setRefreshHeader({params} ,callback(ret, err))

##params

loadingImg：

- 类型：字符串类型
- 描述：（可选项）下拉刷新时显示的图标路径，支持：widget://、fs://
- 默认：未设置时不显示该图标

bgColor：

- 类型：字符串类型
- 描述：（可选项）下拉刷新视图的背景色，支持 rgb、rgba、#、img
- 默认：#f5f5f5

textColor：

- 类型：字符串类型
- 描述：（可选项）提示文字颜色，支持 rgb、rgba、#
- 默认：#8e8e8e

textDown：

- 类型;字符串类型
- 描述：（可选项）下拉过程中的提示文字
- 默认：'下拉可以刷新…'

textUp：

- 类型：字符串类型
- 描述：（可选项）下拉到一点位置时的提示文字
- 默认：'松开开始刷新…'

showTime：

- 类型：布尔类型
- 描述：（可选项）是否显示刷新时间
- 默认：true

##callback

返回触发刷新事件，通过 reloadData 停止下拉状态

##示例代码

```js
var groupList = api.require('groupList');
groupList.setRefreshHeader({
	loadingImg : 'widget://res/groupList_arrow.png',
	bgColor: '#F5F5F5',
	textColor: '#8E8E8E',
	textDown: '下拉可以刷新...',
	textUp: '松开开始刷新...',
	showTime : true
},function(ret, err){
    if(ret){
         alert( JSON.stringify( ret ) );
    }else{
         alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**show**<div id="8"></div>

显示已隐藏的 groupList 列表视图

show()

##示例代码

```js
var groupList = api.require('groupList');
groupList.show();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="9"></div>

隐藏 groupList 列表视图，并没有从内存里清除

hide()

示例代码

```js
var groupList = api.require('groupList');
groupList.hide();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

