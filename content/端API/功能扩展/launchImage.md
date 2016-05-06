/*
Title: launchImage
Description: 获取APP的启动图，可用来做类似网易新闻客户端那种启动页广告。
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：开发者</p>

<div class="outline">
[get](#a1)

[clearCache](#a2)
</div>

#**概述**

launchImage 模块可以用来获取当前 APP 使用经过云编译打包后的启动图，并自动缓存。其目的是用来制作类似网易新闻客户端的那种带 Logo 的启动广告页。且可以自己开发服务端接口，后台更换启动广告。[开发思路和演示Demo请看此帖](http://community.apicloud.com/bbs/forum.php?mod=viewthread&tid=20729)

    
<div id="a1"></div>
#**get**

获取启动图

get({params}, callback(ret, err))

##params

isPortrait：

- 类型：布尔
- 描述：（可选项）是否为竖屏。
- 默认值：true（竖屏）

debug：

- 类型：布尔
- 描述：（可选项）调试模式。开启时，每次都会从底层获取启动图，方便调试；关闭时，如果有缓存，则直接返回图片地址。
- 默认值：false

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true      //布尔型；true||false，获取是否成功
    src: ''           //字符串类型；成功时返回启动图路径，失败返回空
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
    code: 1     //数字类型；
                //错误码：
                //1（获取失败）
    msg:        //字符串类型；错误信息
}
```

##示例代码

```js
var launchImage= api.require('launchImage');
launchImage.get({
    debug: false,
    isPortrait: true
}, function(ret, err){        
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```
##补充说明

IOS 机型需要在 控制台=>端设置=>启动页 中上传精准分辨率的启动页！

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="a2"></div>
#**clearCache**

清除缓存的启动图

clearCache({params}, callback(ret, err))

##params

reGet：

- 类型：布尔
- 描述：（可选项）清除缓存后是否立即重新获取。
- 默认值：false（不获取）

isPortrait：

- 类型：布尔
- 描述：（可选项）是否为竖屏。如果reGet为true，且APP是横屏应用，需要设置此项
- 默认值：true（竖屏）

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true      //布尔型；true||false，操作是否成功
    src: ''         //字符串类型；如果reGet为true，返回启动图路径，否则返回空
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
    code: 1     //数字类型；
                //错误码：
                //1（重新获取失败）
    msg:        //字符串类型；错误信息
}
```

##示例代码

```js
var launchImage= api.require('launchImage');
launchImage.clearCache({
    reGet: false,
    isPortrait: true
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