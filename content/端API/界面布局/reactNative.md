/*
Title: reactNative
Description: reactNative
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">方法</a></li>
</ul>
<div id="method-content">

<div class="outline">
[createModule](#createModule)
</div>

#**概述**
[react-native](http://facebook.github.io/react-native/),是facebook今年三月份正式对外公布的基于react.js的no dom开发框架.把 react-native 封装为 APICloud 平台的一个模块,用于扩展自己的应用功能! say goodbye to html!
代码已开源,参见: [react-native-for-APICloud](https://github.com/jskit2015/react-native-for-APICloud)


#**createModule**<div id="createModule"></div>

创建并显示一个 react-navite 模块

createModule(params);

##params

moduleName:

- 类型:   字符串.
- 默认值: 无.
- 描述:   必选项.模块名称.需在编译前的react-js文件中指定.必须要和传入的jsbundle文件对应.

jsbundle: 

- 类型：字符串
- 默认值: 无.
- 描述: 必选项.使用react-native bundle指令编译react-js后得到的文件.必须和moduleName对应使用.支持http:// ,fs://, widget://, cache:// 等文件协议.


##示例代码
```js
/* 创建并显示一个 react-navite 模块 */

var reactNative = api.require("reactNative");

reactNative.createModule({
    moduleName: "AwesomeProject", // 模块名称.需在编译前的react-js文件中指定.必须要和传入的jsbundle文件对应.
    jsbundle: "widget://res/main.jsbundle" /* 使用react-native bundle指令编译react-js后得到的文件.
    必须和moduleName对应使用.支持http:// ,fs://, widget://, cache:// 等协议. */
});
```
##补充说明

 无.

##可用性

iOS系统.

可提供的 1.0.0 及更高版本.