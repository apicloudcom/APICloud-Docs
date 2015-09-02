/*
Title: UISearchBar
Description: UISearchBar
*/
<div class="outline">
[open](#m1)

[close](#m3)

[setText](#m2)

[clearHistory](#m4)
</div>

#**概述**

UISearchBar 是一个独立的搜索页面，可以返回搜索文本，监听录音按钮事件，保存、清除搜索记录。**UISearchBar 模块是 searchBar 模块的优化版。**

![图片说明](/img/docImage/searchBar.jpg)

<div id="m1"></div>
#**open**

打开搜索页面

open({params}, callback(ret))

##params

placeholder：

- 类型：字符串
- 描述：（可选项）搜索框的占位提示文本
- 默认值：'请输入搜索关键字'

historyCount：

- 类型：数字
- 描述：（可选项）历史记录条数
- 默认值：10

showRecordBtn：

- 类型：布尔
- 描述：（可选项）是否显示录音按钮
- 默认值：true

texts：

- 类型：JSON对象
- 描述：（可选项）模块各部分的文本
- 内部字段：

```js
{
    cancelText: '取消',           //（可选项）字符串类型；取消按钮的文本；默认：'取消'  
    clearText: '清除搜索记录'     //（可选项）字符串类型；清除按钮的文本；默认：'清除搜索记录'
}
```

styles：

- 类型：JSON对象
- 描述：（可选项）模块各部分的样式
- 内部字段：

```js
{
    navBar: {                               //（可选项）JSON对象；搜索框所在的导航条样式
        bgColor: '#FFFFFF',                 //（可选项）字符串类型；搜索框所在的导航条背景色，支持rgb，rgba，#；默认：'#FFFFFF'
        borderColor: '#ccc'                 //（可选项）字符串类型；搜索框所在的导航条边框颜色，支持rgb，rgba，#；默认：'#CCCCCC'
    },
    searchBox: {                            //（可选项）JSON对象；搜索框样式
        bgImg: '',                          //（可选项）字符串类型；搜索框的背景图片，要求本地路径（fs://，widget://）；默认：自带背景图片
        color: '#000',                      //（可选项）字符串类型；搜索框输入文本的颜色，支持rgb，rgba，#；默认：'#000000'
        height: 44                          //（可选项）数字类型；搜索框的高度；默认：44
    },
    cancel: {                               //（可选项）JSON对象；取消按钮的样式
        bg: 'rgba(0,0,0,0)',                //（可选项）字符串类型；取消按钮的背景，支持rgb，rgba，#，图片路径（本地路径，支持fs://，widget://）；默认：'rgba(0,0,0,0)'
        color: '#D2691E',                   //（可选项）字符串类型；取消按钮的字体颜色，支持rgb，rgba，#；默认：'#D2691E'
        size: 16                            //（可选项）数字类型；取消按钮的字体大小；默认：16
    },
    list: {                                 //（可选项）JSON对象；历史记录列表的样式
        color: '#696969',                   //（可选项）字符串类型；历史记录列表的文本颜色，支持rgb，rgba，#；默认：'#696969'
        bgColor: '#FFFFFF',                 //（可选项）字符串类型；历史记录列表的背景色，支持rgb，rgba，#；默认：'#FFFFFF'
        activeBgColor: '#eee',              //（可选项）字符串类型；历史记录列表按下时的背景色，支持rgb，rgba，#；默认：'#EEEEEE'
        borderColor: '#eee',                //（可选项）字符串类型；历史记录列表的边框颜色，支持rgb，rgba，#；默认：'#EEEEEE'
        size: 16                            //（可选项）数字类型；历史记录列表的字体大小；默认：16
    },
    clear: {                                //（可选项）JSON对象；清除历史记录按钮的样式
        color: '#000000',                   //（可选项）字符串类型；清除按钮的字体颜色，支持rgb，rgba，#；默认：'#000000'
        bgColor: '#fff',                    //（可选项）字符串类型；清除按钮的背景色，支持rgb，rgba，#；默认：'#FFFFFF'
        activeBgColor: '#eee',              //（可选项）字符串类型；清除按钮按下时的背景色，支持rgb，rgba，#；默认：'#EEEEEE'
        borderColor: '#ccc',                //（可选项）字符串类型；清除按钮的下边框颜色，支持rgb，rgba，#；默认：'#CCCCCC'
        size: 16                            //（可选项）数字类型；清除按钮的字体大小；默认：16
    }
}
```

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	eventType: 'record',        //字符串类型；交互事件类型
                                //取值范围：
                                //record（用户点击录音按钮）
                                //search（用户点击搜索按钮）
                                //history（用户点击历史记录）
	text: ''                    //字符串类型；返回用户要搜索的文本
}
```

##示例代码

```js
var obj = api.require('UISearchBar');
obj.open({
    placeholder: '请输入搜索关键字',
    historyCount: 10,
    showRecordBtn: true,
    texts: {
        cancelText: '取消',
        clearText: '清除搜索记录'
    },
    styles: {
        navBar: {
            bgColor: '#FFFFFF',
            borderColor: '#ccc'
        },
        searchBox: {
            bgImg: '',
            color: '#000',
            height: 44
        },
        cancel: {
            bg: 'rgba(0,0,0,0)',
            color: '#D2691E',
            size: 16
        },
        list: {
            color: '#696969',
            bgColor: '#FFFFFF',
            borderColor: '#eee',
            size: 16
        },
        clear: {
            color: '#000000',
            borderColor: '#ccc',
            size: 16
        }
    }
}, function(ret){
	if(ret.eventType == 'record'){
		api.alert({msg: '点击了录音按钮'});
	} else if(ret.eventType == 'search') {
		api.alert({msg: '点击了搜索按钮'});
	} else if(ret.eventType == 'history') {
		api.alert({msg: '点击了历史记录'});
	} else {
		alert(ret.text);
	}
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m3"></div>
#**close**

关闭搜索页面

close()

##示例代码

```js
var obj = api.require('UISearchBar');
obj.close();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m2"></div>
#**setText**

设置搜索框的文字

setText({params})

##params

text：

- 类型：字符串
- 描述：（可选项）搜索框内的文字，若不传或传空则清空搜索框内容

##示例代码

```js
var obj = api.require('UISearchBar');
obj.setText({
    text: '设置语音识别的文本'
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m4"></div>
#**clearHistory**

清空搜索历史记录

clearHistory()

##示例代码

```js
var obj = api.require('UISearchBar');
obj.clearHistory();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
