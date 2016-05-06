/*
Title: getWebUrl
Description: getWebUrl
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：开发者</p>

<div class="outline">
[addListener](#a1)

</div>

#**概述**

获取当前页面窗口的Url和Title。**可以配合api.execScript和setInterval来获取Frame窗口的链接与标题**

    
<div id="a1"></div>
#**addListener**

获取当前页链接的Url和标题Title

addListener(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    url: 'http://www.apicloud.com',        //字符串类型；获取到的Url
    title:'APICloud跨平台APP技术专家'      //字符串类型；获取到的Url
}
```
err：

- 类型：JSON 对象
- 内部字段：

```js
{
    code: 0     //数字类型；错误码
}
```
##获取当前窗口 示例代码

```js
var getWebUrl = api.require('getWebUrl');
getWebUrl.addListener(function( ret, err){
    if(ret.url){
        alert(ret.url);
        alert(ret.title);
	}else{
        alert(err.code);
	}
});
```

##获取 Frame 窗口 示例代码

```js
//一下代码全部卸载Win窗口上
setInterval('getWebUrl()', 2000);    //每隔2秒获取Frame的Url与Title
//用api.execScript在Frame执行getWebUrl，并把结果返回给Win
function getWebUrl() {
    var js = 'var getWebUrl = api.require('getWebUrl');getWebUrl.addListener(function(ret, err){if(ret.url){api.execScript({name: 'golink',script:'initPage(\''+ret.url+'\',\''+ret.title+'\')' })}});'
    api.execScript({
        name: 'golink',
        frameName: 'content',
        script: js
    });
}
function initPage( url, title) {
    //获取链接和标题后的处理
}
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
