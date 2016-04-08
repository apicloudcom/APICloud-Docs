/*
Title: shortCut
Description: shortCut
*/
<div class="outline">
[showLaunch](#a1)

</div>

#**概述**

shortCut 是用来给软件添加一个快捷方式的工具，但是快捷方式只能选择内置的图标，设计了A~Z 26个字母供使用者选择。用户可选字段为快捷方式的名称以及使用26个字母当中的哪个字母。图片字母样式在模块预览图中。本模块暂仅支持安卓。


- 补充说明:

  
1. 经测试，由于有些手机在软件安装之后才会同意软件权限，所以导致在有些手机上面创建快捷方式会稍微慢一些，一般手机都是正常的。

2. 而针对慢的问题的测试结果是软件第一次安装，由于手机性能差导致权限提示步骤会慢一些，导致手机对软件创建快捷方式的授权也会
3. 慢半拍，这是正常现象。

    
<div id="a1"></div>
#**showLaunch**

为当前app添加快捷方式

showLaunch(param)

##params

launchname：

- 类型：字符串
- 描述：（必选项）为app添加快捷方式的名称。

num：

- 类型：字符串
- 描述：所用字母序号
- 取值范围：(必选项)1～26


##示例代码

```js
var shortCut = api.require('shortCut');
shortCut.showLaunch({
    launchname: 'Hello', 
    num: '10'
});
```

##可用性

Android系统

可提供的1.0.0及更高版本
