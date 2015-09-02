/*
Title: searchBar
Description: searchBar
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[setText](#2)

[close](#3)

[cleanHistory](#4)
</div>

#**概述**

searchBar定义了一个搜索界面的模板，开发者可自定义该模板的样式。可将搜索记录归档到本地。**UISearchBar 模块是 searchBar 模块的优化版，建议使用  UISearchBar 模块，此模块已停止更新。**

![图片说明](/img/docImage/searchBar.jpg)

#**open**<div id="1"></div>

打开搜索界面

open({params}, callback(ret, err)) 

##params

placeholder：

- 类型：字符串
- 默认值：请输入搜索关键字
- 描述：（可选项）搜索提示文本

bgImg：

- 类型：字符串
- 默认值：默认背景图片
- 描述：（可选项）搜索输入框背景图片

cancelColor：

- 类型：字符串
- 默认值： #D2691E
- 描述：（可选项）取消按钮的颜色，支持rgb，rgba，#

cancelSize：

- 类型：数字
- 默认值：16
- 描述：（可选项）取消按钮大小

textColor：

- 类型：字符串
- 默认值：#000000
- 描述：（可选项）搜索输入文本的字体颜色，支持rgb，rgba，#

textFielWidth：

- 类型：数字
- 默认值：当前屏幕宽度减70
- 描述：（可选项）搜索输入框宽度

textFieldHeight：

- 类型：数字
- 默认值：44
- 描述：（可选项）搜索输入框的高度

placeholder：

- 类型：字符串
- 默认值：请输入搜索关键字
- 描述：（可选项）搜索提示文本

recordCount：

- 类型：数字
- 默认值：10
- 描述：（可选项）搜索历史记录条数

barBgColor：

- 类型：字符串
- 默认值：#FFFFFF
- 描述：（可选项）导航条背景色，支持rgb，rgba，#

listBgColor：

- 类型：字符串
- 默认值：#FFFFFF
- 描述：（可选项）历史记录表背景色，支持rgb，rgba，#

listColor：

- 类型：字符串
- 默认值：#696969
- 描述：（可选项）搜索历史记录文本字体颜色，支持rgb，rgba，#

listSize：

- 类型：数字
- 默认值：16
- 描述：（可选项）搜索历史记录字体大小

cleanColor：

- 类型：字符串
- 默认值：#000000
- 描述：（可选项）清除历史记录字体颜色，支持rgb，rgba，#

cleanSize：

- 类型：数字
- 默认值：16
- 描述：（可选项）清除历史记录字体大小

<del>animation：</del>

- <del>类型：布尔</del>
- <del>默认值：true</del>
- <del>描述：（可选项）打开页面时是否有动画</del>

anim：

- 类型：布尔
- 默认值：true
- 描述：（可选项）打开页面时是否有动画

showRecord：

- 类型：布尔
- 默认值：true
- 描述：（可选项）是否显示录音按钮

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	isRecord:              //是否是点击录音按钮的click事件
	text：					//搜索的文本
}
```

##示例代码

```js
var obj = api.require('searchBar');
obj.open(function(ret,err){
	if(ret.isRecord){
		api.alert({msg:'点击了录音按钮'});
	}else{
		ret.text;
	}
});
```


##补充说明

打开搜索视图页面

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setText**<div id="2"></div>

设置搜索页面搜索框的文字

setText({params})

##params

text：

- 类型：字符串
- 默认值：无
- 描述：（可选项）搜索框内的文字
- 备注：若不传或传空则不显示

##示例代码

```js
var obj = api.require('searchBar');
obj.setText({
     text:'可以用来设置语音识别后的文本'
 });
```

##补充说明

设置搜索文本

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**close**<div id="3"></div>

关闭页面

close()

##示例代码

    var obj = api.require('searchBar');
    obj.close();

##补充说明

关闭搜索视图

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**cleanHistory**<div id="4"></div>

清空历史记录

cleanHistory()

##示例代码

    var obj = api.require('searchBar');
    obj. cleanHistory();

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
