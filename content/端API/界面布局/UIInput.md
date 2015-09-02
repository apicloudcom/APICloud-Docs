/*
Title: UIInput
Description: UIInput
*/
<div class="outline">
[open](#m1)

[close](#m2)

[show](#m3)

[hide](#m4)

[value](#m9)

[insertValue](#m10)
</div>

#**概述**

UIInput 是一个输入框模块；输入框可自动获取焦点，并弹出键盘，可自定义输入框的位置及样式，监听输入框内容的变化；用于实现搜索框或其它输入框的 autofocus 及弹出键盘功能。

![UIInput](/img/docImage/UIInput.jpg)

<div id="m1"></div>

#**open**

打开输入框，**注意：调用 open 接口的元素，不能加 tapmode 属性**

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
    h: 40   //（可选项）数字类型；模块的高度；默认：40
}
```

styles：

- 类型：JSON对象
- 描述：（可选项）模块各部分的样式
- 内部字段：

```js
{
    bgColor: '#fff',        //（可选项）字符串类型；输入框的背景色，支持rgb、rgba、#；默认：'#fff'
    size: 14,               //（可选项）数字类型；输入框的文字大小；默认：14
    color: '#000',          //（可选项）字符串类型；输入框内的字体颜色，支持rgb、rgba、#；默认：'#000'
    placeholder: {
        color: '#ccc'       //（可选项）字符串类型；输入框占位文字的颜色；默认：'#ccc'
    }
}
```

maxRows：

- 类型：数字
- 描述：（可选项）输入框显示的最大行数，**注意：取值大于1（多行显示时），不触发 search 事件回调**
- 默认值：1

placeholder：

- 类型：字符串
- 描述：（可选项）输入框的占位提示文本

keyboardType:

- 类型：字符串
- 描述：（可选项）输入框获取焦点时，弹出的键盘类型；
- 默认值：'default'
- 取值范围：
    - default（默认键盘）
    - number（数字键盘）
    - search（搜索键盘）

fixedOn：

- 类型：字符串
- 描述：（可选项）模块所属 Frame 的名字，若不传则模块归属于当前 Window

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true,                  //布尔型；true||false
    eventType: 'show'              //字符串类型；交互事件类型，
                                   //取值范围：
                                   //show（模块打开成功）
                                   //change（输入框内容改变）
                                   //search（点击键盘的搜索按钮）
}
```

##示例代码

```js
var UIInput = api.require('UIInput');
UIInput.open({
	 rect: {
        x: 0,
        y: 0,
        w: api.winWidth,
        h: 40
    },
    styles: {
        bgColor: '#fff',
        size: 14,
        color: '#000',
        placeholder: {
            color: '#ccc'
        }
    },
    maxRows: 4,
    placeholder: '这是一个输入框',
    keyboardType: 'number',
    fixedOn: ''
}, function(ret){
    if(ret.status){
        alert(ret.eventType);
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m2"></div>

#**close**

关闭输入框

close()

##示例代码

```js
var UIInput = api.require('UIInput');
UIInput.close();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m3"></div>

#**show**

显示输入框

show()

##示例代码

```js
var UIInput = api.require('UIInput');
UIInput.show();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m4"></div>

#**hide**

隐藏输入框

hide()

##示例代码

```js
var UIInput = api.require('UIInput');
UIInput.hide();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m9"></div>

#**value**

获取或设置输入框的内容

value({params}, callback(ret, err))

##params

msg：

- 类型：字符串
- 描述：（可选项）输入框的内容，若不传则返回输入框的值

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true,        //布尔型；true||false
    msg: ''              //字符串类型；输入框当前内容文本
}
```

##示例代码

```js
var UIInput = api.require('UIInput');
//设置输入框的值
UIInput.value({
    msg: '设置输入框的值'
});

//获取输入框的值
UIInput.value(function(ret, err){
    if(ret.status){
      api.alert({msg: ret.msg});
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m10"></div>

#**insertValue**

向输入框的指定位置插入内容

insertValue({params})

##params

index：

- 类型：数字
- 描述：（可选项）插入内容的起始位置。**注意：中文，全角符号均占一个字符长度；索引从0开始，0表示插入到最前面，1表示插入到第一个字符后面，2表示插入到第二个字符后面，以此类推。**
- 默认值：当前输入框的值的长度

msg：

- 类型：字符串
- 描述：（可选项）要插入的内容
- 默认值：''

##示例代码

```js
var UIInput = api.require('UIInput');
UIInput.insertValue({
    index: 10,
    msg: '这里是插入的字符串'
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本