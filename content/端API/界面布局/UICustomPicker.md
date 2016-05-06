/*
Title: UICustomPicker
Description: UICustomPicker
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<div class="outline">
[open](#m1)

[close](#m3)

[show](#m5)

[hide](#m4)

[setValue](#m2)
</div>

#**概述**

UICustomPicker 模块是一个自定义内容选择器；可自定义模块位置、内容取值范围、内容标签，设置选中内容；可用于实现固定取值范围的内容选择器，多项内容之间没有级联关系；同一个页面可以打开多个模块实例，以模块 id 区分。

![图片说明](/img/docImage/UICustomPicker.jpg)

<div id="m1"></div>
#**open**

打开自定义选择器

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
    h: 480  //（可选项）数字类型；模块的高度；默认：所属的 Window 或 Frame 的高度
}
```

styles：

- 类型：JSON 对象
- 描述：（可选项）模块各部分的样式
- 内部字段：

```js
{
    bg: 'rgba(0,0,0,0)',        //（可选项）字符串类型；选中内容区域的背景，支持 rgb，rgba，#，图片路径（本地路径，fs://、widget://）；默认：'rgba(0,0,0,0)'
    normalColor: '#959595',     //（可选项）字符串类型；未选中内容的字体颜色，支持 rgb，rgba，#；默认：'#959595'
    selectedColor: '#3685dd',   //（可选项）字符串类型；选中内容的字体颜色，支持 rgb，rgba，#；默认：'#3685dd'
    selectedSize: 36,           //（可选项）数字类型；选中内容的字体大小；默认：36.0
    tagColor: '#3685dd',        //（可选项）字符串类型；内容标签的字体颜色，支持 rgb，rgba，# ；默认：'#3685dd'
    tagSize: 12                 //（可选项）数字类型；内容标签的字体大小；默认：12
}
```

data：

- 类型：JSON 对象
- 描述：自定义选择器的标签和内容取值范围；若数组长度大于1，则显示多个选择器实例，彼此仍是一个整体，各个实例宽度 = 模块整体宽度（w）/ 实例个数
- 内部字段：

```js
[{
    tag: '时',          //（可选项）字符串类型；内容标签；不传或传空则不显示
    scope: '0-23'       //内容的取值范围
                        //支持字符串类型，如：'0-23' ，表示取值范围为0至23，中间符号为英文连字符'-'，只有整数范围可以如此传参
                        //支持数组类型，如：['一','二','三','四']，表示内容取值范围包含在数组之内
                        //支持数组类型，如：[{value:'一',id:1},{value:'二',id:2},{value:'三',id:3},{value:'四',id:4}]，表示内容取值包含在 JSON 对象组成的数组之内，其中 value 为必须传键值。其余可自定义，此 JSON 对象会在 callback 内回调给前端
}]
```

rows：

- 类型：数字
- 描述：（可选项）滚动内容时可见的内容行数，只接受大于1的奇整数。**安卓平台不支持此参数，可配合模块高度（h）设置选中字体大小（selectedSize），调整可见的内容行数。**
- 默认值：3

autoHide：

- 类型：布尔
- 描述：（可选项）选中内容时，上下选项是否自动隐藏
- 默认值：true

loop：

- 类型：布尔
- 描述：（可选项）是否循环滚动
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
    id: 0,                  //数字类型；模块的 id，用于区分模块的多个实例
    eventType: 'show',      //字符串类型；交互事件类型
                            //取值范围：
                            //show（模块打开成功）
                            //selected（选择器选中内容）
    data: ['12','30']       //数组类型；选择器选中的内容数组，内部元素与源数据保持一致
}
```

##示例代码

```js
var UICustomPicker = api.require('UICustomPicker');
UICustomPicker.open({
    rect: {
		x: 30,
		y: api.frameHeight / 2 - 170,
		w: api.frameWidth - 60,
		h: 340
    },
    styles: {
        bg: 'rgba(0,0,0,0)',
        normalColor: '#959595',
        selectedColor: '#3685dd',
        selectedSize: 36,
        tagColor: '#3685dd',
        tagSize: 10
    },
    data: [{
        tag: '时',
        scope: '0-23'
    }, {
        tag: '分',
        scope: ['a','b','c','d']
    }],
    rows: 3,
    fixedOn: api.frameName,
    fixed: true
}, function(ret, err){
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

<div id="m3"></div>
#**close**

关闭自定义选择器

close({params})

##params

id：

- 类型：数字
- 描述：模块的 id，用于区分模块的多个实例

##示例代码

```js
var UICustomPicker = api.require('UICustomPicker');
UICustomPicker.close({
    id: 0
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m5"></div>
#**show**

显示自定义选择器

show({params})

##params

id：

- 类型：数字
- 描述：模块的 id，用于区分模块的多个实例

##示例代码

```js
var UICustomPicker = api.require('UICustomPicker');
UICustomPicker.show({
    id: 0
});
```

##可用性

iOS系统

可提供的1.0.0及更高版本

<div id="m4"></div>
#**hide**

隐藏自定义选择器

hide({params})

##params

id：

- 类型：数字
- 描述：模块的 id，用于区分模块的多个实例

##示例代码

```js
var UICustomPicker = api.require('UICustomPicker');
UICustomPicker.hide({
    id: 0
});
```

##可用性

iOS系统

可提供的1.0.0及更高版本

<div id="m2"></div>
#**setValue**

设置自定义选择器当前选中的内容

setValue({params})

##params

id：

- 类型：数字
- 描述：模块 id，用于区分多个模块实例

data：

- 类型：数组
- 描述：设置选中内容的数组，数组某一项为空或不传，表示不改变对应列的值

##示例代码

```js
var UICustomPicker = api.require('UICustomPicker');
UICustomPicker.setValue({
    id: 0,
    data: ['12', '30']
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本