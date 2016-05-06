/*
Title: UICalendar
Description: UICalendar
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<div class="outline">
[open](#m1)

[setSpecialDates](#m55)

[cancelSpecialDates](#m56)

[close](#m4)

[show](#m6)

[hide](#m5)

[nextMonth](#m2)

[prevMonth](#m3)

[nextYear](#m8)

[prevYear](#m9)

[setDate](#m7)
</div>

#**概述**

UICalendar 是一个日历选择模块；可自定义日历的样式，添加特殊日期标注，切换月份，设置指定日期；用于实现常用的日期选择，日历展示功能。**UICalendar 模块是 calendar 模块的优化版。**

注：针对单日的样式优先级序列为：selected>setSpecialDate>specialDate>styles_specialDate>today

![图片说明](/img/docImage/UICalendar.jpg)

***该模块源码已开源，地址：https://github.com/apicloudcom/UICalendar***

#模块接口

<div id="m1"></div>

#**open**

打开日历

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
    h: 220  //（可选项）数字类型；模块的高度；默认：220
}
```

styles：

- 类型：JSON 对象
- 描述：（可选项）模块各部分的样式
- 内部字段：

```js
{
    bg: 'rgba(0,0,0,0)',            //（可选项）字符串类型；日历整体背景，支持 rgb、rgba、#、图片路径，要求本地路径（fs://、widget://）；默认：'rgba(0,0,0,0)'
    week: {                         //（可选项）JSON对象，星期的样式
        weekdayColor: '#3b3b3b',    //（可选项）字符串类型；平日文字的颜色，支持 rgb、rgba、#；默认：'#3b3b3b'
        weekendColor: '#a8d400',    //（可选项）字符串类型；周末文字的颜色，支持 rgb、rgba、#；默认：'#a8d400'
        size: 24                    //（可选项）数字类型；星期文字的大小；默认：24
    },
    date: {                         //（可选项）JSON对象，普通日期的样式
        color: '#3b3b3b',           //（可选项）字符串类型；普通日期文字的颜色；支持 rgb、rgba、#；默认：'#3b3b3b'
        selectedColor: '#fff',      //（可选项）字符串类型；普通日期选中后的文字颜色，支持 rgb、rgba、#；默认：'#fff'
        selectedBg: '#a8d500',      //（可选项）字符串类型；普通日期选中后的背景，支持 rgb、rgba、#，图片路径，要求本地路径（fs://、widget://）；默认：'#a8d500'
        size: 24                    //（可选项）数字类型；普通日期文字的大小；默认：24
    },
    today: {                        //（可选项）JSON对象，设备当前日期的样式
        color: '#a8d500',           //（可选项）字符串类型；当前日期的文字颜色，支持 rgb、rgba、#；默认：'#a8d500'
        bg: 'widget://'             //（可选项）字符串类型；当前日期的背景，支持 rgb、rgba、#，图片路径，要求本地路径（fs://、widget://）
    },
    specialDate: {                  //（可选项）JSON对象，需要标记的特殊日期的通用样式                  
        color: '#3b3b3b',           //（可选项）字符串类型；文字颜色，支持 rgb、rgba、#；默认：与普通日期文字颜色一致
        bg: 'widget://'             //（可选项）字符串类型；支持 rgb、rgba、#，图片路径，要求本地路径（fs://、widget://）；默认：与普通日期选中后的背景一致
    }
}
```

specialDate：

- 类型：数组
- 描述：（可选项）需要标记的特殊日期数组
- 内部字段：

```js
[{
    date: '2015-07-27'          //字符串类型；日期字符串，格式为：yyyy-MM-dd
    color: '#3b3b3b',           //（可选项）字符串类型；文字颜色，支持 rgb、rgba、#；默认：与 styles->specialDate->color 一致
    bg: 'widget://'             //（可选项）字符串类型；支持 rgb、rgba、#，图片路径，要求本地路径（fs://、widget://）；默认：与 styles->specialDate->bg 一致
}]
```

switchMode：

- 类型：字符串
- 描述：（可选项）月份的切换方式
- 默认值：'vertical'
- 取值范围：
    - vertical（上下切换）
    - horizontal（左右切换）
    - none（不支持通过手势切换月份）

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

fixed：

- 类型：布尔
- 描述：（可选项）模块是否随所属 window 或 frame 滚动
- 默认值：true（不随之滚动）

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    eventType: 'show',          //字符串类型；交互事件类型
                                //取值范围：
                                //show（日历显示）
                                //switch（水平或垂直切换月份）
                                //special（点击特殊日期）
                                //normal（点击普通日期）
	year: 2015,                 //数字类型；当前选择的年份
	month: 7,                   //数字类型；当前选择的月份
	day: 27                     //数字类型；当前选择的日期
}
```

##示例代码

```js
var UICalendar = api.require('UICalendar');
UICalendar.open({
    rect: {
		x: 30,
		y: api.frameHeight / 2 - 170,
		w: api.frameWidth - 60,
		h: 340
    },
    styles: {
        bg: 'rgba(0,0,0,0)',
        week: {
            weekdayColor: '#3b3b3b',
            weekendColor: '#a8d400',
            size: 12
        },
        date: {
            color: '#3b3b3b',
            selectedColor: '#fff',
            selectedBg: '#a8d500',
            size: 12
        },
        today: {
            color: 'rgb(230,46,37)',
            bg: ''
        },
        specialDate: {
            color: '#a8d500',
            bg: 'widget://image/a.png'
        }
    },
    specialDate: [{
        date: '2015-06-01'
    }],
    switchMode: 'vertical',
    fixedOn: api.frameName,
    fixed: false
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

<div id="m55"></div>
#**setSpecialDates**

设置特殊日期

setSpecialDates({params})

##params

specialDates：

- 类型：数组
- 描述：需要标记的特殊日期数组，格式为：yyyy-MM-dd
- 内部字段：

```js
[{
    date: '2015-07-27'          //字符串类型；日期字符串，格式为：yyyy-MM-dd
    color: '#3b3b3b',           //（可选项）字符串类型；文字颜色，支持 rgb、rgba、#；默认：与 styles->specialDate->color 一致
    bg: 'widget://'             //（可选项）字符串类型；支持 rgb、rgba、#，图片路径，要求本地路径（fs://、widget://）；默认：与 styles->specialDate->bg 一致
}]
```
##示例代码

```js
var UICalendar = api.require('UICalendar');
UICalendar.setSpecialDates({
    specialDates:[{
       date: '2015-12-07',
       color: '#abckde',
       bg: '#ff0000'
    },{
       date: '2015-12-08',
       color: '#abckde',
       bg: '#ff0000'
    }]
});
```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m56"></div>
#**cancelSpecialDates**

取消已设置的特殊日期状态

cancelSpecialDates({params})

##params

specialDates：

- 类型：数组
- 描述：需要取消的特殊日期组成的数组，格式为：yyyy-MM-dd

##示例代码

```js
var UICalendar = api.require('UICalendar');
UICalendar.cancelSpecialDates({
    specialDates:['2015-12-08','2015-12-07']
});
```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m4"></div>
#**close**

关闭日历

close()

##示例代码

```js
var UICalendar = api.require('UICalendar');
UICalendar.close();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m6"></div>
#**show**

显示日历

show()

##示例代码

```js
var UICalendar = api.require('UICalendar');
UICalendar.show();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m5"></div>
#**hide**

隐藏日历

hide()

##示例代码

```js
var UICalendar = api.require('UICalendar');
UICalendar.hide();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m2"></div>
#**nextMonth**

显示下个月

nextMonth(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	year: '2015',          //数字类型；当前显示的年份
	month: '8'             //数字类型；当前显示的月份
}
```

##示例代码

```js
var UICalendar = api.require('UICalendar');
UICalendar.nextMonth(function(ret, err){      
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
#**prevMonth**

显示上个月

prevMonth(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    year: '2015',          //数字类型；当前显示的年份
    month: '6'             //数字类型；当前显示的月份
}
```

##示例代码

```js
var UICalendar = api.require('UICalendar');
UICalendar.prevMonth(function(ret, err){      
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

<div id="m8"></div>
#**nextYear**

显示下一年

nextYear(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    year: '2016',          //数字类型；当前显示的年份
    month: '6'             //数字类型；当前显示的月份
}
```

##示例代码

```js
var UICalendar = api.require('UICalendar');
UICalendar.nextYear(function(ret, err){      
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

<div id="m9"></div>
#**prevYear**

显示上一年

prevYear(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    year: '2014',          //数字类型；当前显示的年份
    month: '6'             //数字类型；当前显示的月份
}
```

##示例代码

```js
var UICalendar = api.require('UICalendar');
UICalendar.prevYear(function(ret, err){      
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

<div id="m7"></div>
#**setDate**

设置选中日期

setDate({params}, callback(ret, err))

##params

date：

- 类型：字符串
- 描述：（可选项）选中日期，格式为：yyyy-MM-dd
- 默认值：当前日期

ignoreSelected：

- 类型：布尔
- 描述：（可选项）选中日期是否忽略选中日期样式（open -> styles -> date -> selectedColor、selectedBg）
- 默认值：false

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true        //布尔型；true||false
}
```

##示例代码

```js
var UICalendar = api.require('UICalendar');
UICalendar.setDate({
    date: '2015-08-08',
    ignoreSelected: false
}, function(ret, err){      
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本