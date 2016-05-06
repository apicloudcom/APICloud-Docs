/*
Title: slidingList
Description: slidingList
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：开发者</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[showList](#a1)

</div>

#**概述**

slidingList 封装了自定义列表，仿 iOS 滑动选择器，由底部弹出。 

#**showList**<div id="a1"></div>

仿IOS底部滑动选择器

showList(callback(ret, err))

##params
rightbtn：

- 类型：字符串
- 描述：右侧确定按钮

leftbtn：

- 类型：字符串
- 描述：左侧取消按钮

item_height：

- 类型：字符串
- 描述：每个item对应的高度，测试高度为130

item_num：

- 类型：字符串
- 描述：开启时显示的item的数量，测试数量为3

data：

- 类型：数组字符串
- 描述：需要显示的数据，数组长度最少为3个

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	select_item:“你点击了第一个按钮”,           //操作成功状态值 。当点击取消的时候 返回值为“取消”
	item_num : 1                              //操作成功返回选中item索引。
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
    select_item:''    // 当必填参数没有填或者必填参数传递错误的话会有相应的提示 比如 '数量少于三个' '缺少参数'
}
```

##示例代码

```js
var slidingList = api.require('slidingList');
slidingList.showList({
	rightbtn : '确定', 
	leftbtn : '取消',
	item_height : '130',
	item_num:'3',
	data : [{ content:'标题1'},{content:'标题2'},{content:'标题3'}]
}, function(ret, err){		
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

底部弹出层

##可用性

Android系统

可提供的1.0.0及更高版本

