/*
Title: cityList
Description: cityList
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[close](#2)

[hide](#3)

[show](#4)
</div>

#**概述**

cityList是一个城市列表模块，自带了右边字母导航条，可快速滚动到目标城市选项。开发者可自定义城市列表的数据源，[本模块已有升级优化版](http://docs.apicloud.com/端API/界面布局/UICityList)

![图片说明](/img/docImage/cityList.jpg)

#**open**<div id="1"></div>

打开城市列表

open({params}, callback(ret, err))

##params

x：

- 类型：数字
- 默认值：0
- 描述：（可选项）城市列表视图左上角点坐标

y：

- 类型：数字
- 默认值：0
- 描述：（可选项）城市列表视图左上角点坐标

w：

- 类型：数字
- 默认值：当前屏幕的宽
- 描述：（可选项）视图的宽

h：

- 类型：数字
- 默认值：w+20
- 描述：（可选项）视图的高

currentCity：

- 类型：字符串
- 默认值：无
- 描述：（可选项）定位出来的用户当前所在城市
- 备注：若不传或传空则不显示

locationWay：

- 类型：字符串
- 默认值：GPS定位
- 描述：（可选项）显示获取用户当前位置的定位方式（UI上当前城市后面显示的字符串）

resource：

- 类型：字符串
- 默认值：无
- 描述：城市列表的数据源文件路径，支持https、http、widget、fs等网络、本地路径协议
- 备注：数据源文件必须为.json格式的文件。且数据格式如下所示，其中topCitys为热门城市，若不传topCitys则不显示热门城市。每个城市对象必须至少包含city、id、pinyin三个字段，其余可自定义添加。以城市为单位的json对象，会在callBack时按原格式返回
- json文件内部字段：

```js
{
    "topCitys":[{
                 "city": "北京",
                 "id": 110001,
                 "pinyin": "beijing"
               },{
                 "city": "天津",
                 "id": 120001,
                 "pinyin": "tianjin"
               }],
    "citys": [{
	              "id": 110001,
	              "city": "北京",
	              "pinyin": "beijing"
	          },{
	              "id": 120001,
	              "city": "天津",
	              "pinyin": "tianjin"
             }]
}
```
topCitys：

- 类型：字符串
- 默认值：热门城市
- 描述：（可选项）topCitys对应的标题

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

style：

- 类型：JSON 对象
- 默认值：见内部字段
- 描述：（可选项）城市列表样式设置
- 内部字段：

```js
{
     indector:       //（可选项）字母导航条设置，内部字段如下：{
                       bgColor:  //（可选项）字母导航条背景色，支持 rgb、rgba、#，默认#FFFFFF
                       tintColor://（可选项）字母导航条字母色，支持 rgb、rgba、#，默认#696969
                       }
     bg:             //（可选项）列表分组标题背景设置，支持 rgb、rgba、#，默认#E0E0E0
     itemBg:         //（可选项）列表单条选项背景色，支持 rgb、rgba、#，默认#ffffff
     titleColor:     //（可选项）section标题字体颜色，支持 rgb、rgba、#，默认#000000
     titleSize:      //（可选项）section标题字体大小，数字类型，默认12.0
     contentColor:   //（可选项）内容字体颜色，支持 rgb、rgba、#，默认#000000
     contentSize:    //（可选项）内容字体大小，数字类型，默认14.0
     localColor:     //（可选项）定位提示字体颜色，支持 rgb、rgba、#，默认#696969
     localSize:      //（可选项）定位提示字体大小，数字类型，默认12.0
     searchBar:      //（可选项）搜索条样式设置，内部字段如下：{
                        bg:         //（可选项）搜索条背景色，支持支持 rgb、rgba、#，默认#C2C2C2
                        placeholder://（可选项）搜索条占位提示文字，默认输入城市名或首字母查询
                        cancelColor://（可选项）右边取消字体颜色，支持 rgb、rgba、#，默认#E3E3E3；android上忽略此参数
                      }
}
```

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    eventType:   //回调事件类型，字符串类型，取值范围如下：
                    open： //打开模块视图成功
                    click: //用户点击列表
    cityInfo:    //返回用户选择的城市信息，json对象，同传入的数据源格式相同
}
```

##示例代码

```js
var cityList = api.require('cityList');
cityList.open({
	currentCity:'北京',
	resource:'widget://res/cityList.json'
},function(ret,err) {
	var cityInfo = ret.cityInfo;
});
```

##补充说明

打开城市列表

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**close**<div id="2"></div>

关闭城市列表

close()

##示例代码

    var cityList = api.require('cityList');
    cityList.close();

##补充说明

关闭城市列表

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**hide**<div id="3"></div>

隐藏城市列表

hide()

##示例代码

    var cityList = api.require('cityList');
    cityList.hide();

##补充说明

隐藏城市列表

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**show**<div id="4"></div>

显示已隐藏的城市列表

show()

##示例代码

    var cityList = api.require('cityList');
    cityList.show();

##补充说明

显示已隐藏的城市列表

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
