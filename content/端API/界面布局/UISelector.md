/*
Title: UISelector
Description: UISelector
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[set](#2)

[close](#3)

[hide](#4)

[show](#5)

</div>

#**概述**

UISelector 是自定义分级联动选择器模块，支持自定义选择器的大小、位置、内容及其级别（android暂仅最大支持3级）和数据源，可手动设置指定选中项，用于实现固定取值范围的内容选择器，多项内容之间有级联关系。本模块是 customSelector 模块的升级版，与  [UIlinkedPicker](http://docs.apicloud.com/端API/界面布局/UILinkedPicker) 相似（数据源格式不同）

![图片说明](/img/docImage/customSelector.jpg)

#**open**<div id="1"></div>

打开选择器

open({params}, callback(ret, err))

##params

rect：

- 类型：JSON对象
- 描述：（可选项）模块的位置及尺寸
- 内部字段：

```js
{
    x: 0,   //（可选项）数字类型；模块左上角的 x 坐标（相对于所属的 Window 或 Frame）；默认：0
    y: 0,   //（可选项）数字类型；模块左上角的 y 坐标（相对于所属的 Window 或 Frame）；默认：0
    w: 320, //（可选项）数字类型；模块的宽度；默认：所属的 Window 或 Frame 的宽度
    h: 480  //（可选项）数字类型；模块的高度；默认：w
}
```
styles：

- 类型：JSON对象
- 描述：（可选项）模块各部分的样式
- 内部字段：

```js
{
    bg: 'rgba(0,0,0,0)',     //（可选项）字符串类型；模块背景，支持 rgb、rgba、#，图片路径（本地路径，fs://，widget://）；默认：'rgba(0,0,0,0)'
	text:{                   //（可选项）JSON对象；字体样式；默认值见内部字段
	   size: 22,             //（可选项）数字类型；字体大小；默认值：22
	   selected: '#fff',     //（可选项）字符串类型；选中字体色，支持rgb、rgba、#；默认#fff
	   normal: '#000'        //（可选项）字符串类型；常态字体色；支持rgb、rgba、#；默认#000
	},
	item:{                   //（可选项）JSON对象；item 样式；默认值见内部字段
      w: 80,                 //（可选项）数字类型；背景视图的宽；默认值：单元格宽-20
      h: 45,                 //（可选项）数字类型；背景视图的高；默认值：单元格高-20
	  normal: '#87ceeb',     //（可选项）字符串类型；常态背景色，支持rgb、rgba、#；默认值：#87ceeb
	  selected: '#218868',   //（可选项）字符串类型；选中后的背景色，支持rgb、rgba、#；默认值：#218868
	  zoomIn: 1.2            //（可选项）数字类型；选中后放大倍数，；默认值：1.2
    }
}
```

data：

- 类型：数组对象/字符串
- 描述：选择器的数据源，若为字符串，则表示 json 文件的路径(支持 widget://，fs:// 协议)，文件格式同下文内部字段
- 内部字段：

```js
[{
      title:   		//字符串类型；父级目录的标题
      contents:		//数组类型；子级目录的内容组成的数组，内容可为字符串或 JSON 对象。若是字符串组成的数组，则表示该不包含子级目录；若本字段内容是 JSON 对象组成的数组，则表示该级包含子级目录，JSON 对象的内部字段依次递归嵌套；
       
}]
                    //举例如下：
                    //一级选择器：["A","B","C","D","E","F","G","H","I","J","K"]
                    //二级选择器： [{
				        "title":"A",
				        "contents":["10","20","30","40","50","60","70","80","90","100"]
				    },{
				        "title":"B",
				        "contents":["1d","2d","3d","4d","5d","6d","7d","8d","9d","10d"]
				    },{
				        "title":"C",
				        "contents":["1q","2q","3q","4q","5q","6q","7q","8q","9q","10q"]
				    }]
				    //三级选择器： [{
		            "title":"A",
		            "contents":[{
		                    "title": "a1", 
		                    "contents": ["10","20","30","40","50","60","70","80","90","100"] 
		                },{
		                    "title": "b1", 
		                    "contents": ["1","2","3","4","5","6","7","8","9","10"] 
		                }]
                  }]
```
rows：

- 类型：数字
- 描述：（可选项）滚动内容时可见的内容行数，只接受大于1的奇整数。
- 默认值：5

indexs：

- 类型：数组
- 描述：（可选项）各列默认选中项 item 的下标(不可超过本列 item 总数)组成的数组
- 默认值：[0,0...]//数组个数和级数对应

bounce：

- 类型：布尔
- 描述：（可选项）列表滑动到头是否弹动
- 默认值：true

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

fixed:
- 类型：布尔
- 描述：（可选项）模块是否随所属 Window 或 Frame 滚动
- 默认值：true（不随之滚动）

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
   eventType:'show',      //字符串类型；交互事件的类型；
                          //取值范围：
                          //show（模块打开成功）
                          //selected（选择器选中内容）
   selects:[{             //数组类型；从各级目录选取的内容信息组成的数组，若选择器是自定义的二级选择器，则本数组包含两个元素，若选择器是自定义的三级选择器，则此数组包含三个元素
       index: 1,          //数字类型；选取的数据在所在数组内的索引
       content: 'abc'     //字符串类型；选取的数据
   }]
}
```

##示例代码

```js
var UISelector = api.require('UISelector');
UISelector.open({
    rect: {
		x: 30,
		y: api.frameHeight / 2 - 170,
		w: api.frameWidth - 60,
		h: 340
    },
    styles:{
		    bg: 'rgba(0,0,0,0)',   
    	  text: {                  
    			   size: 14,             
    			   selected: '#fff',     
    			   normal: '#000'        
    	  },
    	  item: {                   
    		     w: 80,                
    		     h: 45,                
    			   normal: '#87ceeb',    
    			   selected: '#218868',  
    			   zoomIn: 1.2        
        }
    },
    rows: 5,
    indexs: [1,2,3],
    bounce: false,
    fixedOn: api.frameName,
    fixed: false,
    data: [{
        title: "A",
        contents: [{
            title: "a",
            contents: ["1", "2", "3", "4", "5", "6", "7", "8", "9", "10"]
        }]
    }, {
        title: "B",
        contents: ["a", "b", "c", "d", "e", "f", "g", "h", "i", "j"]
    }, {
        title: "C",
        contents: ["1a", "2b", "3c", "4d", "5e", "6f", "7g", "8h", "9i", "10j"]
    }, {
        title: "D",
        contents: ["1t", "2t", "3t", "4t", "5t", "6t", "7t", "8t", "9t", "10t"]
    }, {
        title: "E",
        contents: ["1a", "2a", "3a", "4a", "5a", "6a", "7a", "8a", "9a", "10a"]
    }, {
        title: "F",
        contents: ["1f", "2f", "3f", "4f", "5f", "6f", "7f", "8f", "9f", "10f"]
    }, {
        title: "G",
        contents: ["1!", "2!", "3!", "4!", "5!", "6!", "7!", "8!", "9!", "10!"]
    }, {
        title: "H",
        contents: ["1th", "2th", "3th", "4th", "5th", "6th", "7th", "8th", "9th", "10th"]
    }, {
        title: "I",
        contents: ["one", "two", "three", "four", "five", "six", "seven", "eight", "nine", "ten"]
    }, {
        title: "J",
        contents: ["壹", "貮", "叁", "肆", "伍", "陆", "柒", "捌", "玖", "拾"]
    }, {
        title: "K",
        contents: ["一", "二", "三", "四", "五", "六", "七", "八", "九", "十"]
    }]
},function( ret, err){
    if( ret ){
        alert(JSON.stringify(ret));
    }else{
        alert(JSON.stringify(err));
    }
});
```

##可用性

ios 系统，android 系统

可提供的1.0.0及更高版本


#**set**<div id="2"></div>

设置选择器的选中项

set({params})

##params

indexs：

- 类型：数组
- 描述：（可选项）各列默认选中项 item 的下标(不可超过本列 item 总数)组成的数组
- 默认值：[0,0...]//数组个数和级数对应

##示例代码

```js
var UISelector = api.require('UISelector');
UISelector.set({
	indexs:[2,3,6]
});
```

##可用性

ios 系统，android 系统

可提供的1.0.0及更高版本

#**close**<div id="3"></div>

关闭选择器

close()

##示例代码

```js
var UISelector = api.require('UISelector');
UISelector.close();
```

##可用性

ios 系统，android 系统

可提供的1.0.0及更高版本


#**hide**<div id="4"></div>

隐藏选择器

hide()

##示例代码

```js
var UISelector = api.require('UISelector');
UISelector.hide();
```

##补充说明

隐藏选择器，并没有从内存里清除

##可用性

ios 系统，android 系统

可提供的1.0.0及更高版本


#**show**<div id="5"></div>

显示已隐藏的选择器

show()

##示例代码

```js
var UISelector = api.require('UISelector');
UISelector.show();
```

##可用性

ios 系统，android 系统

可提供的1.0.0及更高版本


