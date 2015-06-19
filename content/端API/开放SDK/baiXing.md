/*
Title: baiXing
Description: 百姓⺴移动端的SDK
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#basic-content">方法</a></li>
</ul>
<div id="basic-content">

<div class="outline">
[init](#a1)

[startActivity](#a2)
</div>

#**概述**

baixing模块封装了百姓网移动端的SDK,在百姓网开发者中心申请之后开发者即可在极短时间内进行百姓网SDK的集成。

暂仅支持安卓.

#**init**<div id="a1"></div>

模块进行初始化

init(params)

##params

### apiKey

- 类型：字符串
- 默认值: 无
- 描述: 百姓网分配的 apiKey,需到百姓SDK开发者网站申请

### apiSecret

- 类型：字符串
- 默认值: 无
- 描述: 百姓网分配的 apiSecret,需到百姓SDK开发者网站申请

##示例代码

```js
var baiXing = api.require("baiXing");

baiXing.init({
    apiKey:"ausdk_test",
    apiSecret:"cd864410365753c2ea6bf70c74a7e625"
});
```

##补充说明

无

##可用性

Android系统

可提供的1.0.0及更高版本


#**startActivity**<div id="a2"></div>

跳转到百姓Ad⻚面

startActivity(param);

##params

### title

- 类型：字符串
- 默认值: "⼆⼿汽车"
- 描述: 想要显示的⻚面标题

### city

- 类型：字符串
- 默认值: 无
- 描述: 城市中⽂名称或拼⾳

### queryId

- 类型：字符串
- 默认值: 上海
- 描述: 城市中⽂名称或拼⾳

### keywords

- 类型：字符串
- 默认值: 无
- 描述: 指定的查询关键字列表,关键字由”,”(英文逗号)分割,例:”xxxx, xx”

### showLocation

- 类型：布尔值
- 默认值: false
- 描述: true, 显⽰位置 按钮;false, 不显⽰。

### showPost

- 类型：字符串
- 默认值: 无
- 描述: true, 显⽰ 发布 按钮;false, 不显⽰。

##示例代码

```js
var baiXing = api.require("baiXing");
baiXing.init({
    apiKey:"ausdk_test",
    apiSecret:"cd864410365753c2ea6bf70c74a7e625"
});

var param = {
    title:"⼆手汽车",
    city:"上海",
    queryId:"aq2",
    keywords:"⼤大众",
    showLocation:true,
    showPost:true
};

baiXing.startActivity(param);
```

##补充说明

调⽤startActivity()前必须要调⽤init()函数对baixing模块进行初始化

##可用性

Android系统

可提供的1.0.0及更高版本