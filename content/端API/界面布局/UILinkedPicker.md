/*
Title: UILinkedPicker
Description: UILinkedPicker
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

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

UILinkedPicker 是自定义分级联动选择器模块，支持自定义选择器的大小、位置、内容及其级别（android暂仅最大支持3级）和数据源，可手动设置指定选中项，用于实现固定取值范围的内容选择器，多项内容之间有级联关系；**本模块和 UISelector 模块相似，与之相比数据源格式不同，本模块几点信息数据支持自定义**

![图片说明](/img/docImage/customSelector.jpg)

#**open**<div id="1"></div>

打开选择器

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
    h: 480  //（可选项）数字类型；模块的高度；默认：w
}
```
styles：

- 类型：JSON 对象
- 描述：（可选项）模块各部分的样式
- 内部字段：

```js
{
    bg: 'rgba(0,0,0,0)',     //（可选项）字符串类型；模块背景，支持 rgb、rgba、#，图片路径（本地路径，fs://、widget://）；默认：'rgba(0,0,0,0)'
	text:{                   //（可选项）JSON对象；字体样式；默认值见内部字段
	   size: 22,             //（可选项）数字类型；字体大小；默认值：22
	   selected: '#fff',     //（可选项）字符串类型；选中字体色，支持 rgb、rgba、#；默认#fff
	   normal: '#000'        //（可选项）字符串类型；常态字体色；支持 rgb、rgba、#；默认#000
	},
	item:{                   //（可选项）JSON对象；item 样式；默认值见内部字段
      w: 80,                 //（可选项）数字类型；背景视图的宽；默认值：单元格宽-20
      h: 45,                 //（可选项）数字类型；背景视图的高；默认值：单元格高-20
	  normal: '#87ceeb',     //（可选项）字符串类型；常态背景色，支持 rgb、rgba、#；默认值：#87ceeb
	  selected: '#218868',   //（可选项）字符串类型；选中后的背景色，支持 rgb、rgba、#；默认值：#218868
	  zoomIn: 1.2            //（可选项）数字类型；选中后放大倍数，；默认值：1.2
    }
}
```

data：

- 类型：数组对象/字符串
- 描述：选择器的数据源，若为字符串，则表示 json 文件的路径(支持 widget://、fs:// 协议)，文件格式同下文内部字段
- 内部字段：

```js
[{
      value:   		//JSON对象；结点信息，本数据字段内容可自定义，自定义的结点信息数据会在选中后返回给前端
      children:		//数组类型；结点子级目录的信息组成的数组，类型为 JSON 对象。若该对象内包含 children 字段数据，则表示该结点有子级目录；
       
}]
                    //举例如下：
                    //一级选择器：[{
                      'value':{
                        'id':1,
                        'name':'A'
                      }
                    },{
                      'value':{
                        'id':2,
                        'name':'B'
                      }
                    },{
                      'value':{
                        'id':3,
                        'name':'C'
                      }
                    },{
                      'value':{
                        'id':4,
                        'name':'D'
                      }
                    }]
                    //二级选择器： [{
                      'value':{
                        'id':10,
                        'name':'A'
                      },
                      'children':[{
	                      'value':{
	                        'id':11,
	                        'name':'10'
	                      }
	                    },{
	                      'value':{
	                        'id':12,
	                        'name':'11'
	                      }
	                    },{
	                      'value':{
	                        'id':13,
	                        'name':'12'
	                      }
	                    },{
	                      'value':{
	                        'id':14,
	                        'name':'13'
	                      }
	                    }]
                    },{
                      'value':{
                        'id':20,
                        'name':'B'
                      },
                      'children':[{
	                      'value':{
	                        'id':21,
	                        'name':'20'
	                      }
	                    },{
	                      'value':{
	                        'id':22,
	                        'name':'21'
	                      }
	                    },{
	                      'value':{
	                        'id':23,
	                        'name':'22'
	                      }
	                    },{
	                      'value':{
	                        'id':24,
	                        'name':'23'
	                      }
	                    }]
                    },{
                      'value':{
                        'id':30,
                        'name':'C'
                      },
                      'children':[{
	                      'value':{
	                        'id':31,
	                        'name':'30'
	                      }
	                    },{
	                      'value':{
	                        'id':32,
	                        'name':'31'
	                      }
	                    },{
	                      'value':{
	                        'id':33,
	                        'name':'32'
	                      }
	                    },{
	                      'value':{
	                        'id':34,
	                        'name':'33'
	                      }
	                    }]
                    },{
                      'value':{
                        'id':40,
                        'name':'D'
                      },
                      'children':[{
	                      'value':{
	                        'id':41,
	                        'name':'40'
	                      }
	                    },{
	                      'value':{
	                        'id':42,
	                        'name':'41'
	                      }
	                    },{
	                      'value':{
	                        'id':43,
	                        'name':'42'
	                      }
	                    },{
	                      'value':{
	                        'id':44,
	                        'name':'43'
	                      }
	                    }]
                    }]
				    //三级选择器：  [{
                      'value':{
                        'id':10,
                        'name':'A'
                      },
                      'children':[{
	                      'value':{
	                        'id':11,
	                        'name':'10'
	                      },
	                      'children':[{
		                         'value':{
		                            'id':111,
		                            'name':'301'
		                         }
		                      },{
		                         'value':{
		                            'id':112,
		                            'name':'302'
		                         }
		                   }]
	                    },{
	                      'value':{
	                        'id':12,
	                        'name':'11'
	                      },
	                      'children':[{
		                         'value':{
		                            'id':211,
		                            'name':'303'
		                         }
		                      },{
		                         'value':{
		                            'id':212,
		                            'name':'304'
		                         }
		                   }]
	                    },{
	                      'value':{
	                        'id':13,
	                        'name':'12'
	                      },
	                      'children':[{
		                         'value':{
		                            'id':311,
		                            'name':'331'
		                         }
		                      },{
		                         'value':{
		                            'id':312,
		                            'name':'332'
		                         }
		                   }]
	                    },{
	                      'value':{
	                        'id':14,
	                        'name':'13'
	                      },
	                      'children':[{
		                         'value':{
		                            'id':411,
		                            'name':'341'
		                         }
		                      },{
		                         'value':{
		                            'id':412,
		                            'name':'342'
		                         }
		                   }]
	                    }]
                    },{
                      'value':{
                        'id':20,
                        'name':'B'
                      },
                      'children':[{
	                      'value':{
	                        'id':21,
	                        'name':'20'
	                      },
	                      'children':[{
		                         'value':{
		                            'id':213,
		                            'name':'213'
		                         }
		                      },{
		                         'value':{
		                            'id':214,
		                            'name':'214'
		                         }
		                   }]
	                    },{
	                      'value':{
	                        'id':22,
	                        'name':'21'
	                      },
	                      'children':[{
		                         'value':{
		                            'id':221,
		                            'name':'221'
		                         }
		                      },{
		                         'value':{
		                            'id':222,
		                            'name':'222'
		                         }
		                   }]
	                    },{
	                      'value':{
	                        'id':23,
	                        'name':'22'
	                      },
	                      'children':[{
		                         'value':{
		                            'id':231,
		                            'name':'231'
		                         }
		                      },{
		                         'value':{
		                            'id':232,
		                            'name':'232'
		                         }
		                   }]
	                    },{
	                      'value':{
	                        'id':24,
	                        'name':'23'
	                      },
	                      'children':[{
		                         'value':{
		                            'id':241,
		                            'name':'241'
		                         }
		                      },{
		                         'value':{
		                            'id':242,
		                            'name':'242'
		                         }
		                   }]
	                    }]
                    },{
                      'value':{
                        'id':30,
                        'name':'C'
                      },
                      'children':[{
	                      'value':{
	                        'id':31,
	                        'name':'30'
	                      },
	                      'children':[{
		                         'value':{
		                            'id':311,
		                            'name':'311'
		                         }
		                      },{
		                         'value':{
		                            'id':312,
		                            'name':'312'
		                         }
		                   }]
	                    },{
	                      'value':{
	                        'id':32,
	                        'name':'31'
	                      },
	                      'children':[{
		                         'value':{
		                            'id':321,
		                            'name':'321'
		                         }
		                      },{
		                         'value':{
		                            'id':322,
		                            'name':'322'
		                         }
		                   }]
	                    },{
	                      'value':{
	                        'id':33,
	                        'name':'32'
	                      },
	                      'children':[{
		                         'value':{
		                            'id':331,
		                            'name':'331'
		                         }
		                      },{
		                         'value':{
		                            'id':331,
		                            'name':'332'
		                         }
		                   }]
	                    },{
	                      'value':{
	                        'id':34,
	                        'name':'33'
	                      },
	                      'children':[{
		                         'value':{
		                            'id':341,
		                            'name':'341'
		                         }
		                      },{
		                         'value':{
		                            'id':342,
		                            'name':'342'
		                         }
		                   }]
	                    }]
                    },{
                      'value':{
                        'id':40,
                        'name':'D'
                      },
                      'children':[{
	                      'value':{
	                        'id':41,
	                        'name':'40'
	                      },
	                      'children':[{
		                         'value':{
		                            'id':411,
		                            'name':'411'
		                         }
		                      },{
		                         'value':{
		                            'id':412,
		                            'name':'412'
		                         }
		                   }]
	                    },{
	                      'value':{
	                        'id':42,
	                        'name':'41'
	                      },
	                      'children':[{
		                         'value':{
		                            'id':421,
		                            'name':'421'
		                         }
		                      },{
		                         'value':{
		                            'id':422,
		                            'name':'422'
		                         }
		                   }]
	                    },{
	                      'value':{
	                        'id':43,
	                        'name':'42'
	                      },
	                      'children':[{
		                         'value':{
		                            'id':431,
		                            'name':'431'
		                         }
		                      },{
		                         'value':{
		                            'id':432,
		                            'name':'432'
		                         }
		                   }]
	                    },{
	                      'value':{
	                        'id':44,
	                        'name':'43'
	                      },
	                      'children':[{
		                         'value':{
		                            'id':441,
		                            'name':'441'
		                         }
		                      },{
		                         'value':{
		                            'id':442,
		                            'name':'442'
		                         }
		                   }]
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
- 默认值：[0,0...]		//数组个数和级数对应

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
- 描述：（可选项）模块是否随所属 window 或 frame 滚动
- 默认值：true（不随之滚动）

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
   eventType:'show',               //字符串类型；交互事件的类型；
                                   //取值范围：
                                   //show（模块打开成功）
                                   //selected（选择器选中内容）
   selects:[{                      //数组类型；从各级目录选取的内容信息组成的数组，若选择器是自定义的二级选择器，则本数组包含两个元素，若选择器是自定义的三级选择器，则此数组包含三个元素
       index: 1,                   //数字类型；选取的数据在所在数组内的索引
       value: {'id':1,'name':'北京'}//JSON对象；可自定义的结点的信息
   }]
}
```

##示例代码

```js
var UILinkedPicker = api.require('UILinkedPicker');
UILinkedPicker.open({
    rect:{
		x: 30,
		y: api.frameHeight / 2 - 170,
		w: api.frameWidth - 60,
		h: 340
    },
    styles:{
	    bg: 'rgba(0,0,0,0)',   
		text:{                  
		   size: 14,             
		   selected: '#fff',     
		   normal: '#000'        
		},
		item:{                   
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
        'value': {
          'id': 1,
          'name': 'A'
        }
      },{
        'value': {
          'id': 2,
          'name': 'B'
        }
      },{
        'value': {
          'id': 3,
          'name': 'C'
        }
      },{
        'value': {
          'id': 4,
          'name': 'D'
        }
      },{
        'value': {
          'id': 5,
          'name': 'E'
        }
      },{
        'value': {
          'id': 6,
          'name': 'F'
        }
      },{
        'value': {
          'id': 7,
          'name': 'G'
        }
      },{
        'value': {
          'id': 8,
          'name': 'H'
        }
      },{
        'value': {
          'id': 9,
          'name': 'I'
        }
      },{
        'value': {
          'id': 10,
          'name': 'J'
        }
    }]
}, function( ret, err ) {
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
var UILinkedPicker = api.require('UILinkedPicker');
UILinkedPicker.set({
	indexs: [2,3,6]
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**close**<div id="3"></div>

关闭选择器

close()

##示例代码

```js
var UILinkedPicker = api.require('UILinkedPicker');
UILinkedPicker.close();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**hide**<div id="4"></div>

隐藏选择器

hide()

##示例代码

```js
var UILinkedPicker = api.require('UILinkedPicker');
UILinkedPicker.hide();
```

##补充说明

隐藏选择器，并没有从内存里清除

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**show**<div id="5"></div>

显示已隐藏的选择器

show()

##示例代码

```js
var UILinkedPicker = api.require('UILinkedPicker');
UILinkedPicker.show();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本