/*
Title: 模块审核规范-IOS
Description: 该文档旨在提高审核效率，保证模块质量，以及避免APP因开发者提交不规范模块而引起的各种莫名其妙的问题。
以下条目中，凡提到“模块”的地方，均指moduleDemo这个模块，做为例子。
*/


##1）、最外层目录审核

<strong>模块包的最外层目录必须为该模块的模块名</strong>，如moduleDemo，然后使用zip压缩工具将该目录压缩成zip格式文件。如下图：
![图片说明](/img/docImage/module_standard/ios1.png)

【**】如果模块包不符合该规范，将导致该模块不被编译。
##2）、子目录或文件审核

<strong>iOS模块包内部最多只能包含以下3项</strong>，其中target和module.json为必需的，res目录可选，大致如图：
![图片说明](/img/docImage/module_standard/ios2.png)


###2.1、res_模块名 目录审核：

该目录为可选目录，<strong>该目录命名规范必须为“res_”开头，后面跟模块名。</strong>例如“res_moduleDemo”。


###2.2、target 目录审核：

<strong>该目录为必需目录。</strong>

1）、该目录存放模块库（也可以是如.swift这种源文件）及模块用到的其它第三方库、资源文件等。如果有<strong>.framework</strong>和<strong>.bundle</strong>文件（在mac下面显示成文件、windows下面为文件夹），**要检查其里面是否有<strong>Info.plist</strong>文件，如果有，需要删掉**，否则将导致应用上传不了AppStore。

2）、该目录允许包含子目录，但**不能包含<strong>widget、uz、UZEngine、UZModules</strong>等目录**。

3）、该目录下**不能包含引擎库<strong>libUZEngine.a</strong>和<strong>Info.plist</strong>文件。**


##3）、module.json文件审核：

该文件的结构为一个或者多个JSON对象，每个对象代表一个模块（平台允许一个模块包中同时存放多个模块的），如：
一个对象时的module.json配置：

```
{
	"name":"moduleDemo",
	"class":"UZModuleDemo",
	"methods":["method1", "method2"]
}
```

多个对象时的module.json配置，对象与对象之间以逗号隔开：

```
{
	"name":"moduleDemo1",
	"class":"UZModuleDemo1",
	"methods":["method1", "method2"]
},
{
	"name":"moduleDemo2",
	"class":"UZModuleDemo2",
	"methods":["method1", "method2"]
}
```

同时需要检查一下module.json配置中，所有的字符是否均是半角的字符。

凡是不符合以上格式的，均须开发者做更改。

