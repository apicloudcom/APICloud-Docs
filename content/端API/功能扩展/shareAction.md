/*
Title: shareAction
Description: shareAction
*/
<div class="outline">
[share()](#m1)

</div>

#**概述**

shareAction 是一个调用系统分享功能的模块，通过该模块能够分享一些最常见的文本，图片信息等


<div id="m1"></div>

#**share**

打开分享对话框

share({params})

##params

text:

- 类型：字符串
- 描述：（可选项）要分享的文本信息

type：

- 类型：字符串
- 描述：（可选项）分享文件的类型 
- 默认值：text
- 取值范围：
    - text
    - image
    - audio
    - file

path:

- 类型：字符串
- 描述：（可选项）分享文件的路径，要求本地路径（fs://，widget://）。**Android 平台不支持 widget:// 路径**


##示例代码

```js
var sharedModule = api.require('shareAction');
sharedModule.share({
	text: '纯文本信息',
	type: 'text'
});
```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


