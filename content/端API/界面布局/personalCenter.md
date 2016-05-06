/*
Title: personalCenter
Description: personalCenter
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[open](#1)

[updateValue](#2)

[close](#3)

[setSelect](#4)

[show](#5)

[hide](#6)
</div>

#**概述**

personalCenter 是一个带有图片模糊效果的个人信息展示中心，开发者只需配置相关接口参数即可实现一个原生效果的个人展示中心

![图片说明](/img/docImage/personalCenter.jpg)

#**open**<div id="1"></div>

打开个人中心

open({params}, callback(ret, err))

##params

y ：

- 类型：数字
- 描述：（可选项）个人中心视图上边距屏幕位置
- 默认值：0

h ：

- 类型：数字
- 描述：（可选项）视图的高，不可小于220
- 默认值：220

imgPath：

- 类型：字符串
- 描述：头像图片的路径（如果为网络路径,图片会被缓存到本地），支持http，https，widget，file，fs协议

placeholderImg：

- 类型：字符串
- 描述：（可选项）头像占位图片的路径，支持仅widget，file，fs本地协议

userName ：

- 类型：字符串
- 描述：（可选项）用户名

userNameSize ：

- 类型：数字类型
- 描述：（可选项）用户名字体大小
- 默认值：13

userColor：

- 类型：字符串
- 描述：（可选项）用户名和积分字体颜色
- 默认值：#FFFFFF

subTitle ：

- 类型：字符串
- 描述：（可选项）用户名下边的小标题

subTitleSize ：

- 类型：字符串
- 描述：（可选项）用户名下边的小标题字体大小
- 默认值：13

subTitleColor：

- 类型：字符串
- 描述：（可选项）用户名下边的小标题字体颜色
- 默认值：#FFFFFF

showLeftBtn：

- 类型：布尔值
- 描述：（可选项）是否显示左上交修改按钮
- 默认值：true

showRightBtn：

- 类型：布尔值
- 描述：（可选项）是否显示右上角设置按钮
- 默认值：true

modButton：

- 类型：JSON 对象
- 描述：（可选项）修改按钮参数
- 备注：若不传则不显示修改按钮
- 内部字段：

```js
{
	bgImg:      	//字符串类型；按钮背景图片，要求本地路径（widget://、fs://）
	lightImg:     	//（可选项）字符串类型；按钮点击效果图路径，要求本地路径（widget://、fs://）
}
```

btnArray：

- 类型：数组
- 默认值：默认按钮
- 描述：（可选项）下边按钮的参数信息
- 内部字段：

```js
[{
    bgImg:                   //字符串类型；按钮背景图片，要求本地路径（widget://、fs://）
    selectedImg:             //（可选项）字符串类型；按钮点击图片，要求本地路径（widget://、fs://）
    lightImg:                //（可选项）字符串类型；按钮选中后图片，要求本地路径（widget://、fs://）
    title:                   //（可选项）字符串类型；按钮上的标题
    count:                   //（可选项）字符串类型；按钮上的数据
    titleColor:              //（可选项）字符串类型；按钮上的标题颜色，支持 rgb、rgba、#；默认：#AAAAAA
    titleLightColor:         //（可选项）字符串类型；按钮选中标题的颜色，支持 rgb、rgba、#；默认：#A4D3EE
    countColor:              //（可选项）字符串类型；按钮上数字颜色，支持 rgb、rgba、#；默认：#FFFFFF
    countLightColor:         //（可选项）字符串类型；按钮上数字选中颜色，支持 rgb、rgba、#；默认：#A4D3EE
}]
```

clearBtn：

- 类型：布尔值
- 描述：（可选项）是否将个人中心下边按钮清除
- 默认值：false

fixedOn：

- 类型：字符串类型
- 描述：（可选项）模块视图添加到指定 frame 的名字（只指 frame，传 window 无效）
- 默认：模块依附于当前 window

fixed:

- 类型：布尔
- 描述：（可选项）模块是否随所属 window 或 frame 滚动
- 默认值：true（不随之滚动）

##callback(ret, err)

ret:

- 类型：JSON 对象
- 内部字段：

```js
{
    click:          // 所点击的按钮的索引
                    // 如果存在修改按钮，则其index是按钮数组总下标加一
                    // 若存在左上角按钮，则其index是按钮数组总下标加二
                    // 若存在右上角按钮，则其inidex是按钮数组总下标加三
}
```

##示例代码

```js
var personalCenter = api.require('personalCenter');

var btnArray = [
    {
        'bgImg': 'widget://res/personalCenter/personal_btn_nor.png',
        'selectedImg': 'widget://res/personalCenter/personal_btn_sele.png',
        'lightImg': 'widget://res/personalCenter/personal_btn_light.png',
        'title': '好友',
        'count': '5'
    },
    {
        'bgImg': 'widget://res/personalCenter/personal_btn_nor.png',
        'selectedImg': 'widget://res/personalCenter/personal_btn_sele.png',
        'lightImg': 'widget://res/personalCenter/personal_btn_light.png',
        'title': '回贴',
        'count': '240'
    },
    {
        'bgImg': 'widget://res/personalCenter/personal_btn_nor.png',
        'selectedImg': 'widget://res/personalCenter/personal_btn_sele.png',
        'lightImg': 'widget://res/personalCenter/personal_btn_light.png',
        'title': '主题',
        'count': '27'
    }
];

var count = 382;

var y = 44;


personalCenter.open({
    'y': y,
    'imgPath': 'widget://res/personalCenter/d7d1d308fe165b984c09728e7118e9f1.jpg',
    'placeholderImg': 'widget://res/common/placeHolder.png',
    'userName': 'APICloud',
    'count': count,
    'modButton': {
        'bgImg': 'widget://res/personalCenter/mod_normal.png',
        'lightImg': 'widget://res/personalCenter/mod_click.png'
    },
	fixedOn: api.frameName,
    'btnArray': btnArray
},function(ret,err){
    /* 头像修改按钮. */
    if(btnArray.length === ret.click){
        api.confirm({
            title: '聊天盒子',
            msg: '您想要从哪里选取图片 ?',
            buttons:['优雅自拍', '相册收藏', '取消']
        },function(ret,err){
            var sourceType = 'album';

            if(3 == ret.buttonIndex){ // 取消
                return;
            }

            if(1 == ret.buttonIndex){ // 打开相机
                sourceType = 'camera';
            }

            api.getPicture({
                sourceType: sourceType,
                encodingType: 'png',
                mediaValue: 'pic'
            }, function(ret, err){
                if (ret) {
                    personalCenter.updateValue({
                        imgPath: ret.data,
                        count:count
                    });

                }
            });

        });

        return;
    }

    var msg;

    /* 修改按钮. */
    if(btnArray.length + 1 == ret.click){
        msg = '您没有修改权限!';
    }

    if(btnArray.length + 2 == ret.click){
        msg = '您没有设置权限!'
    }

    if(btnArray.length == ret.click){
        btn = btnArray[ret.click];
        msg = btn.title + ' 数量为 ' + btn.count
    }

    api.toast({
        msg: msg,
        duration: 1000,
        location: 'top'
    });
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**updateValue**<div id="2"></div>

刷新个人中心显示数据

updateValue({params})

##params

userName ：

- 类型：字符串
- 描述：（可选项）用户名
- 备注：若不传则不刷新

subTile ：

- 类型：字符串
- 描述：(可选项)用户名下的小标题
- 备注：若不传则不刷新

imgPath：

- 类型：字符串
- 描述：(可选项)头像地址，若为不传则不刷新

btnArray：

- 类型：数组
- 描述：（可选项）下边按钮显示的数据，不传则不刷新
- 内部字段:

```js
[{
      count:’123’       //字符串类型；按钮上的数据大小
}]
```

##示例代码

```js
var personalCenter = api.require('personalCenter');
personalCenter.updateValue({
	imgPath: 'widget://res/filterMe.png',
	userName: '柚子科技',
	count: '2014',
	btnArray: [{
		count: '123'
	},{
	    count: '123'
	},{
		count: '123'
	}]
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**close**<div id="3"></div>

关闭个人中心

close()

##示例代码

```js
var personalCenter = api.require('personalCenter');
personalCenter.close();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setSelect**<div id="4"></div>

设置选中按钮

setSelect()

##示例代码

```js
var personalCenter = api.require('personalCenter');
personalCenter.setSelect({
	index:1
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**show**<div id="5"></div>

显示个人中心

show()

##示例代码

```js
var personalCenter = api.require('personalCenter');
personalCenter.show();
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**hide**<div id="6"></div>

隐藏个人中心

hide()

##示例代码

```js
var personalCenter = api.require('personalCenter');
personalCenter.hide();
```

##补充说明

隐藏个人中心，并没有从内存里清除

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
