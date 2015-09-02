/*
Title: UICityList
Description: UICityList
*/
<div class="outline">
[open](#m1)

[close](#m2)

[show](#m4)

[hide](#m3)
</div>

#**概述**

UICityList 模块是一个可定制数据源的城市列表；模块根据数据源自动生成字母索引，点击字母索引快速滚动至目标数据，支持数据源搜索；用于实现城市列表的展示，搜索，及导航功能。**UICityList 模块是 cityList 模块的优化版。**

![图片说明](/img/docImage/UICityList.jpg)

<div id="m1"></div>
#**open**

打开城市列表模块

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
    h: 480  //（可选项）数字类型；模块的高度；默认：所属的 Window 或 Frame 的高度
}
```

resource：

- 类型：字符串
- 描述：城市列表的数据源文件路径（支持 https、http、widget、fs 路径协议），数据源文件必须为`.json`文件。城市的JSON数据会在callback时按原格式返回
- `.json`文件内部字段：

```json
{
    "topCitys": [{   //（可选项）数组类型；热门城市，若不传则不显示热门城市            
        "city": "北京",
        "id": 110001,
        "pinyin":"beijing"//（可选项）字符串类型；本字段可不传，若不传模块内会生成该城市名的pinyin，以防止城市名中的多音字乱序问题
    },{
        "city": "天津",
        "id": 120001
    }],
    "citys": [{   //数组类型，数组元素是JSON对象；城市数据；至少包含 id、city 二个字段，其余可自定义添加
        "id": 110001,
        "city": "北京"
    },{
        "id": 120001,
        "city": "天津"
    }]
}
```

styles：

- 类型：JSON对象
- 描述：（可选项）城市列表样式设置
- 内部字段：

```js
{   
    searchBar: {                    //（可选项）JSON对象；顶部搜索条的样式
        bgColor: '#696969',         //（可选项）字符串类型；搜索条背景色，支持rgb、rgba、#；默认：'#696969'
        cancelColor: '#E3E3E3'      //（可选项）字符串类型；取消文字颜色，支持rgb、rgba、#，默认：'#E3E3E3'；在安卓平台上不显示取消按钮，所以，此参数只在iOS平台有效
    },
    location: {                     //（可选项）JSON对象；定位提示文字样式
        color: '#696969',           //（可选项）字符串类型；定位提示文字颜色，支持rgb、rgba、#，默认：'#696969'
        size: 12                    //（可选项）数字类型；定位提示文字大小，默认：12.0
    },
    sectionTitle: {                 //（可选项）JSON对象；标题的样式
        bgColor: '#eee',            //（可选项）字符串类型；标题的背景色，支持rgb、rgba、#；默认：'#EEEEEE'
        color: '#000',              //（可选项）字符串类型；标题文字颜色，支持rgb、rgba、#；默认：'#000000'
        size: 12,                   //（可选项）数字类型；标题文字大小；默认：12.0
        height: 25                  //（可选项）数字类型；区域标题的高度，默认：25.0
    },
    item: {                         //（可选项）JSON对象；列表项的样式
        bgColor: '#fff',            //（可选项）字符串类型；列表项的背景色，支持rgb、rgba、#；默认：'#FFFFFF'
        activeBgColor: '#696969',   //（可选项）字符串类型；列表项按下时的背景色，支持rgb、rgba、#；默认：'#696969'
        color: '#000',              //（可选项）字符串类型；列表项的文字颜色，支持rgb、rgba、#，默认：'#000000'
        size: 14,                 //（可选项）数字类型；列表项的文字大小，默认：14.0
        height: 40                  //（可选项）数字类型；列表项的高度，默认：40.0
    },
    indicator: {                    //（可选项）JSON对象；右侧字母导航条样式
        bgColor: '#fff',            //（可选项）字符串类型；字母导航条背景色，支持rgb、rgba、#，默认：'#FFFFFF'
        color: '#696969'            //（可选项）字符串类型；字母导航条字母颜色，支持rgb、rgba、#，默认：'#696969'
    }
}
```

currentCity：

- 类型：字符串
- 描述：（可选项）显示当前所在城市，若传空或不传则当前城市行不显示（ currentCity 和 locationWay 均不显示）

locationWay：

- 类型：字符串
- 描述：（可选项）显示定位方式（紧跟在当前城市后面）
- 默认值：'GPS定位'

hotTitle：

- 类型：字符串
- 描述：（可选项）热门城市对应的标题
- 默认值：'热门城市'

placeholder：

- 类型：字符串
- 描述：（可选项）顶部搜索条占位提示文字
- 默认值：'输入城市名或首字母查询'

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    eventType: 'show',      //字符串类型；交互事件类型
                            //取值范围：
                            //show（模块打开成功）
                            //selected（用户选择城市）
    cityInfo: {             //JSON对象；用户选择的城市信息，同传入的数据源格式相同
        "id": 110001,
        "city": "北京",
        "pinyin":"beijing"
    }            
}
```

##示例代码

```js
var obj = api.require('UICityList');
obj.open({
    rect: {
        x: 0,
        y: 0,
        w: 320,
        h: 480
    },
    resource: 'widget://res/UICityList.json',
    styles: {
        searchBar: {
            bgColor: '#696969',
            cancelColor: '#E3E3E3'
        },
        location: {
            color: '#696969',
            size: 12
        },
        sectionTitle: {
            bgColor: '#eee', 
            color: '#000',
            size: 12
        },
        item: {
            bgColor: '#fff',
            activeBgColor: '#696969',
            color: '#000',
            size: 14,
            height: 40
        },
        indicator: {
            bgColor: '#fff',
            color: '#696969'
        }
    },
    currentCity: '北京',
    locationWay: 'GPS',
    hotTitle: '热门城市',
    placeholder: '输入城市名或首字母查询'
}, function(ret, err) {
    if(ret.eventType == 'selected'){
        alert(JSON.stringify(ret.cityInfo));
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m2"></div>
#**close**

关闭城市列表

close()

##示例代码

```js
var obj = api.require('UICityList');
obj.close();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m4"></div>
#**show**

显示城市列表

show()

##示例代码

```js
var obj = api.require('UICityList');
obj.show();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m3"></div>
#**hide**

隐藏城市列表

hide()

##示例代码

```js
var obj = api.require('UICityList');
obj.hide();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

