/*
Title: UIChatBox
Description: UIChatBox
*/
<div class="outline">
[open](#m1)

[close](#m2)

[show](#m3)

[hide](#m4)

[popupBoard](#m55)

[closeBoard](#m66)

[popupKeyboard](#m5)

[closeKeyboard](#m6)

[value](#m9)

[insertValue](#m10)

[addEventListener](#m11)

[setPlaceholder](#m13)

[reloadExtraBoard](#m14)
</div>

#**概述**

UIChatBox 模块是一个集成表情的聊天输入框，可自定义表情集、及附加功能，监听输入框的高度及位置变化，还可监听录音按钮的相关事件；常用于实现聊天、评论的表情输入及文本输入功能。此模块始终定位在 Window 窗口最底部，其生命周期与所在 Window 窗口一致。**UIChatBox 模块是 chatBox 模块的优化版。**

![UIChatBox](/img/docImage/chatBox.jpg)


## [实例widget下载地址](http://docs.apicloud.com/img/demo_widget/UIChatBox.rar)

<div id="m1"></div>

#**open**

打开聊天输入框

open({parmas}, callback(ret, err))

##params

placeholder：

- 类型：字符串
- 描述：（可选项）输入框的占位提示文本

autoFocus：

- 类型：布尔
- 描述：（可选项）输入框是否自动获取焦点，并弹出键盘
- 默认值：false

maxRows：

- 类型：数字
- 描述：（可选项）输入框显示的最大行数（高度自适应）
- 默认值：4

emotionPath：

- 类型：字符串
- 描述：自定义表情文件夹（表情图片所在的文件夹，须同时包含一个与该文件夹同名的`.json`配置文件）的路径（本地路径，fs://，widget://）。**`.json`文件内的 name 值必须与表情文件夹内表情图片名对应。**另附：[表情文件夹资源示例](/res/emotion.zip)
- `.json`配置文件格式如下：

```json
[
    {"name": "Expression_1", "text": "[微笑]"},
    {"name": "Expression_2", "text": "[撇嘴]"}
]
```

- `.json`配置文件所在目录：

![emotionPath](/img/emotionPath.png)

texts：

- 类型：JSON对象
- 描述：（可选项）聊天输入框模块可配置的文本
- 内部字段：

```js
{
    recordBtn: {                        //（可选项）JSON对象；录音按钮文字内容
        normalTitle: '按住 说话',       //（可选项）字符串类型；按钮常态的标题，默认：'按住 说话'
        activeTitle: '松开 结束'        //（可选项）字符串类型；按钮按下时的标题，默认：'松开 结束'
    },
    sendBtn: {                        //（可选项）JSON对象；发送按钮文字内容，在 IOS 平台上对键盘内按钮无效
        title: '发送'                  //（可选项）字符串类型；按钮常态的标题，默认：'发送'
    }
}
```

styles：

- 类型：JSON对象
- 描述：（可选项）模块各部分的样式集合
- 内部字段：

```js
{
    inputBar: {                         //（可选项）JSON对象；输入区域（输入框及两侧按钮）整体样式      
        borderColor: '#d9d9d9',         //（可选项）字符串类型；输入框区域上下边框的颜色，支持rgb，rgba，#；默认：'#d9d9d9'
        bgColor: '#f2f2f2'              //（可选项）字符串类型；输入框区域的整体背景色，支持rgb，rgba，#；默认：'#f2f2f2' 
    },
    inputBox: {                         //（可选项）JSON对象；输入框样式
        borderColor: '#B3B3B3',         //（可选项）字符串类型；输入框的边框颜色，支持rgb，rgba，#；默认：'#B3B3B3'
        bgColor: '#FFFFFF'              //（可选项）字符串类型；输入框的背景色，支持rgb，rgba，#；默认：'#FFFFFF'
    },
    emotionBtn: {                       //JSON对象；表情按钮样式
        normalImg: 'widget://'          //字符串类型；表情按钮常态的背景图片（本地路径，fs://，widget://）；默认：笑脸小图标
    },
    extrasBtn: {                        //（可选项）JSON对象；附加功能按钮样式，不传则不显示附加功能按钮
        normalImg: 'widget://'          //（可选项）字符串类型；附加功能按钮常态的背景图片（本地路径，fs://，widget://）
    },
    keyboardBtn: {                      //JSON对象；键盘按钮样式
        normalImg: 'widget://'          //字符串类型；键盘按钮常态的背景图片（本地路径，fs://，widget://）；默认：键盘小图标
    },
    speechBtn: {                        //（可选项）JSON对象；输入框左侧按钮样式，不传则不显示左边的语音按钮
        normalImg: 'widget://'          //字符串类型；左侧按钮常态的背景图片（本地路径，fs://，widget://）
    },
    recordBtn: {                        //JSON对象；“按住 录音”按钮的样式
        normalBg: '#c4c4c4',            //（可选项）字符串类型；按钮常态的背景，支持rgb，rgba，#，图片路径（本地路径，fs://，widget://）；默认：'#c4c4c4'
        activeBg: '#999999',            //（可选项）字符串类型；按钮按下时的背景，支持rgb，rgba，#，图片路径（本地路径，fs://，widget://）；默认：'#999999'；normalBg 和 activeBg 必须保持一致，同为颜色值，或同为图片路径
        color: '#000',                  //（可选项）字符串类型；按钮标题文字的颜色，支持rgb，rgba，#，默认：'#000000'
        size: 14                        //（可选项）数字类型；按钮标题文字的大小，默认：14
    },
    indicator: {                        //（可选项）JSON对象；表情和附加功能面板的小圆点指示器样式，若不传则不显示该指示器
        target: 'both',                 //（可选项）字符串类型；配置指示器的显示区域；默认：'both'
                                        //取值范围：
                                        //both（表情和附加功能面板皆显示）
                                        //emotionPanel（表情面板显示）
                                        //extrasPanel（附加功能面板显示）
        color: '#c4c4c4',               //（可选项）字符串类型；指示器颜色；支持rgb、rgba、#；默认：'#c4c4c4'
        activeColor: '#9e9e9e'          //（可选项）字符串类型；当前指示器颜色；支持rgb、rgba、#；默认：'#9e9e9e'
    },
    sendBtn: {                         //（可选项）JSON对象；发送按钮样式，本参数对 IOS 平台上的键盘内发送按钮无效
        bg: '#4cc518',                 //（可选项）字符串类型；发送按钮背景颜色，支持rgb、rgba、#、img；默认：#4cc518
        titleColor: '#ffffff',          //（可选项）字符串类型；发送按钮标题颜色；默认：#ffffff
        activeBg: '#46a91e',            //（可选项）字符串类型；发送按钮背景颜色，支持rgb、rgba、#、img；默认：无
        titleSize: 13                    //（可选项）数字类型；发送按钮标题字体大小；默认：13
    }
}
```

extras：

- 类型：JSON对象
- 描述：（可选项）点击附加功能按钮，打开的附加功能面板的按钮样式，配合 extrasBtn 一起使用，若 extrasBtn 参数内 normalImg 属性不传则此参数可不传

```js
{
    titleSize: 10,                  //（可选项）数字类型；标题文字大小，默认：10
    titleColor: '#a3a3a3',          //（可选项）字符串类型；标题文字颜色，支持rgb、rgba、#；默认：'#a3a3a3'
    btns: [{                        //数组类型；附加功能按钮的样式
        title: '图片',              //（可选项）字符串类型；附加功能按钮的标题内容                  
        normalImg: '',              //（可选项）字符串类型；按钮常态的背景图片（本地路径，fs://，widget://）
        activeImg: ''               //（可选项）字符串类型；按钮按下时的背景图片（本地路径，fs://，widget://）   
    }]
}
```

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    eventType: 'show',  //字符串类型；回调的事件类型，
                        //取值范围：
                        //show（该模块打开成功）
                        //send（用户点击发送按钮）
                        //clickExtras（用户点击附加功能面板内的按钮）
    index: 0,           //数字类型；当 eventType 为 clickExtras 时，此参数为用户点击附加功能按钮的索引，否则为 undefined
    msg: ''             //字符串类型；当 eventType 为 send 时，此参数返回输入框的内容，否则返回 undefined
}
```
##示例代码

```js
var UIChatBox = api.require('UIChatBox');
UIChatBox.open({
    placeholder: '',
    maxRows: 4,
    emotionPath: 'widget://res/img/emotion',
    texts: {
        recordBtn: {
            normalTitle: '按住 说话',
            activeTitle: '松开 结束'
        },
        sendBtn:{
	        title:"send"
        }
    },
    styles: {
        inputBar: {
            borderColor: '#d9d9d9',
            bgColor: '#f2f2f2'
        },
        inputBox: {
            borderColor: '#B3B3B3',
            bgColor: '#FFFFFF'
        },
        emotionBtn: {
            normalImg: 'widget://res/img/chatBox_face1.png'
        },
        extrasBtn: {
            normalImg: 'widget://res/img/chatBox_add1.png'
        },
        keyboardBtn: {
            normalImg: 'widget://res/img/chatBox_key1.png'
        },
        speechBtn: {
            normalImg: 'widget://res/img/chatBox_key1.png'
        },
        recordBtn: {
            normalBg: '#c4c4c4',
            activeBg: '#999999',
            color: '#000',
            size: 14
        },
        indicator: {
            target: 'both',
            color: '#c4c4c4',
            activeColor: '#9e9e9e'
        },
        sendBtn: {
            titleColor: '#4cc518',
            bg: '#999999' ,
            activeBg: '#46a91e',
            titleSize: 14
        }
    },
    extras: {
        titleSize: 10,
        titleColor: '#a3a3a3',
        btns: [{
            title: '图片',
            normalImg: 'widget://res/img/chatBox_album1.png',
            activeImg: 'widget://res/img/chatBox_album2.png'
        },{
            title: '拍照',
            normalImg: 'widget://res/img/chatBox_cam1.png',
            activeImg: 'widget://res/img/chatBox_cam2.png'
        }]
    }
}, function( ret, err ){
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

<div id="m2"></div>

#**close**

关闭聊天输入框

close()

##示例代码

```js
var UIChatBox = api.require('UIChatBox');
UIChatBox.close();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m3"></div>

#**show**

显示聊天输入框

show()

##示例代码

```js
var UIChatBox = api.require('UIChatBox');
UIChatBox.show();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m4"></div>

#**hide**

隐藏聊天输入框

hide()

##示例代码

```js
var UIChatBox = api.require('UIChatBox');
UIChatBox.hide();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m5"></div>

#**popupKeyboard**

弹出键盘

popupKeyboard()

##示例代码

```js
var UIChatBox = api.require('UIChatBox');
UIChatBox.popupKeyboard();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m6"></div>

#**closeKeyboard**

收起键盘

closeKeyboard()

##示例代码

```js
var UIChatBox = api.require('UIChatBox');
UIChatBox.closeKeyboard();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m55"></div>

#**popupBoard**

弹出表情、附加功能面板

popupBoard({params})

##params

target:

- 类型：字符串
- 描述：操作的面板类型，取值范围如下：
	- emotion：表情面板
	- extras：附加功能面板
- 默认值：emotion
	

##示例代码

```js
var UIChatBox = api.require('UIChatBox');
UIChatBox.popupBoard({
  target:'extras'
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m66"></div>

#**closeBoard**

收起表情、附加功能面板

closeBoard()

##示例代码

```js
var UIChatBox = api.require('UIChatBox');
UIChatBox.closeBoard();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m9"></div>

#**value**

获取或设置聊天输入框的内容

value({params}, callback(ret, err))

##params

msg：

- 类型：字符串
- 描述：（可选项）聊天输入框的内容，若不传则返回输入框的值

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
var UIChatBox = api.require('UIChatBox');
//设置输入框的值
UIChatBox.value({
    msg: '设置输入框的值'
});

//获取输入框的值
UIChatBox.value(function(ret, err){
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

<div id="m10"></div>

#**insertValue**

向聊天输入框的指定位置插入内容

insertValue({params})

##params

index：

- 类型：数字
- 描述：（可选项）待插入内容的起始位置。**注意：中文，全角符号均占一个字符长度；索引从0开始，0表示插入到最前面，1表示插入到第一个字符后面，2表示插入到第二个字符后面，以此类推。**
- 默认值：当前输入框的值的长度

msg：

- 类型：字符串
- 描述：（可选项）要插入的内容
- 默认值：''

##示例代码

```js
var UIChatBox = api.require('UIChatBox');
UIChatBox.insertValue({
    index: 10,
    msg: '这里是插入的字符串'
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m11"></div>

#**addEventListener**

事件监听

addEventListener({params}, callback(ret, err))

##params

target：

- 类型：字符串
- 描述：事件的目标对象
- 取值范围：
    * recordBtn（录音按钮，open 接口的 speechBtn 参数必须传值，否则事件监听无效）
    * inputBar（输入区域，输入框及两侧按钮区域）

name：

- 类型：字符串
- 描述：监听的事件类型
- 取值范围：
    - 适用于 recordBtn 对象
        - press（按下录音按钮）
        - press_cancel（松开录音按钮）
        - move_out（按下录音按钮后，从按钮移出）
        - move_out_cancel（按下录音按钮后，从按钮移出并松开按钮）
        - move_in（move_out 事件后，重新移入按钮区域）
    - 适用于 inputBar 对象
        - move（输入框所在区域弹动事件）
        - change（输入框所在区域高度改变）
        - showRecord（用户点击左侧语音按钮）
        - showEmotion（用户点击表情按钮）
        - showExtras（用户点击右侧附加功能按钮，如果 open 时传了 extras 参数才会有此回调）
        - valueChanged（输入框内容改变事件）

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    inputBarHeight: 60,    //数字类型；输入框及左右按钮整体区域的高度，仅当监听 inputBar 的 move 和 change 事件时本参数有值
    panelHeight: 300 ,     //数字类型；输入框下边缘距离屏幕底部的高度，仅当监听 inputBar 的 move 和 change 事件时本参数有值
    value: ''              //字符串类型；输入框当前内容，仅当 target 为 inputBar name 为 valueChanged 时有值
}
```

##示例代码

```js
//监听 recordBtn 按钮
var UIChatBox = api.require('UIChatBox');
UIChatBox.addEventListener({
    target: 'recordBtn',
    name: 'press'
}, function( ret, err ){
    if( ret ){
         alert( JSON.stringify( ret ) );
    }else{
         alert( JSON.stringify( err ) );
    }
});

//监听 inputBar 
var UIChatBox = api.require('UIChatBox');
UIChatBox.addEventListener({
    target: 'inputBar',
    name: 'move'
}, function( ret, err ){
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

<div id="m13"></div>

#**setPlaceholder**

重设聊天输入框的占位提示文本

setPlaceholder({params})

##params

placeholder：

- 类型：字符串
- 描述：（可选项）占位提示文本，若不传或传空则表示清空占位提示内容

##示例代码

```js
var UIChatBox = api.require('UIChatBox');
UIChatBox.setPlaceholder({
    placeholder: '修改了占位提示内容'
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**reloadExtraBoard**

重新加载（刷新）附加功能面板，**open时必须添加附加功能按钮及其面板参数**

reloadExtraBoard(params)

##params

extras：

- 类型：JSON对象
- 描述：（可选项）点击附加功能按钮，打开的附加功能面板的按钮样式，配合 extrasBtn 一起使用，若 extrasBtn 参数内 normalImg 属性不传则此参数可不传

```js
{
    titleSize: 10,                  //（可选项）数字类型；标题文字大小，默认：10
    titleColor: '#a3a3a3',          //（可选项）字符串类型；标题文字颜色，支持rgb、rgba、#；默认：'#a3a3a3'
    btns: [{                        //数组类型；附加功能按钮的样式
        title: '图片',               //（可选项）字符串类型；附加功能按钮的标题内容                  
        normalImg: '',              //（可选项）字符串类型；按钮常态的背景图片（本地路径，fs://，widget://）
        activeImg: ''               //（可选项）字符串类型；按钮按下时的背景图片（本地路径，fs://，widget://）   
    }]
}
```
##示例代码

```js
var UIChatBox = api.require('UIChatBox');
UIChatBox.reloadExtraBoard({
    extras: {
        titleSize: 10,
        titleColor: '#a3a3a3',
        btns: [{
            title: '图片',
            normalImg: 'widget://res/img/chatBox_album1.png',
            activeImg: 'widget://res/img/chatBox_album2.png'
        },{
            title: '拍照',
            normalImg: 'widget://res/img/chatBox_cam1.png',
            activeImg: 'widget://res/img/chatBox_cam2.png'
        },{
            title: '拍照',
            normalImg: 'widget://res/img/chatBox_cam1.png',
            activeImg: 'widget://res/img/chatBox_cam2.png'
        },{
            title: '拍照',
            normalImg: 'widget://res/img/chatBox_cam1.png',
            activeImg: 'widget://res/img/chatBox_cam2.png'
        },{
            title: '拍照',
            normalImg: 'widget://res/img/chatBox_cam1.png',
            activeImg: 'widget://res/img/chatBox_cam2.png'
        },{
            title: '拍照',
            normalImg: 'widget://res/img/chatBox_cam1.png',
            activeImg: 'widget://res/img/chatBox_cam2.png'
        },{
            title: '拍照',
            normalImg: 'widget://res/img/chatBox_cam1.png',
            activeImg: 'widget://res/img/chatBox_cam2.png'
        },{
            title: '拍照',
            normalImg: 'widget://res/img/chatBox_cam1.png',
            activeImg: 'widget://res/img/chatBox_cam2.png'
        },{
            title: '拍照',
            normalImg: 'widget://res/img/chatBox_cam1.png',
            activeImg: 'widget://res/img/chatBox_cam2.png'
        }]
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本