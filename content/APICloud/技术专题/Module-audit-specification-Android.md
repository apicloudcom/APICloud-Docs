/*
Title: 模块审核规范-Android
Description: 该文档旨在保证模块质量，以及避免APP因开发者提交不规范模块而引起的各种不可预测的问题。
以下条目中，凡提到“模块”的地方，均指moduleDemo这个模块，做为例子。
*/


##1）、最外层目录规范

模块包的**最外层目录必须为该模块的模块名**，如moduleDemo，然后使用zip压缩工具将该目录压缩成zip格式文件。如下图：
![图片说明](/img/docImage/module_standard/1.png)


【**】如果模块包不符合该规范，将导致该模块不被编译。

##2）、子目录或文件规范

Android模块包内部**最多只能包含以下4个目录或文件**，大致如图：
![图片说明](/img/docImage/module_standard/2.png)

如果开发者开发的某模块，包入了这个4个文件或目录以外的文件或目录，需要更改。

### 2.1  res_模块名 目录审核：

●该目录为可选目录。

1）、**该目录命名规范必须为“res_”开头，后面跟模块名**。例如“res_moduleDemo”。
凡是不符合这个规范的，需要更改。

2）、res_moduleDemo目录中内容审核：
res_moduleDemo的根路径下**最多仅允许包含res子目录和AndroidManifest.xml文件**，如图：
![图片说明](/img/docImage/module_standard/3.png)

如果包入了这2个文件或目录以外的文件或目录，需要更改。

### 2.2 res目录审核：

●该目录为可选目录。

该目录包含：anim、drawable 、drawable-xxxx、layout、layout-xxxx、values、values-xxxx、raw、menu等子目录。
这些子目录均为可选。

### 2.3 命名规范审核：

原则上需要对这些目录下的所有文件进行命名规范的审核。
建议的命名规范为：mo_模块名_资源类型_资源名.后缀名。
例如：mo_moduleDemo_anim_aa.xml、mo_moduleDemo_abc.png、mo_moduleDemo_values.xml等。
该审核为非强制，如果开发者模块资源命名不规范，可引导其按照《模块开发指南》中建议的命名规范对资源进行规范的命名。

【**】防止潜在的与他人模块资源冲突的问题。

资源冲突，通常在云编译的时候，编译失败的log中将带大量类似“error: Resource entry ebpay_text_red is already defined”的log，很大部分编译失败均由此原因引起。

### 2.4 引擎固有资源审核

**任意drawable、drawable-xxxx目录下不允许包含名为uz_icon.png和uz_splash_bg.png的图片资源。**如果有，全部删除。

【**】否则将导致使用该模块的app其应用图标和启动页变成默认的。

### 2.5 字符资源审核

**任意values、values-xxxx目录下的strings.xml文件中，<strong>不允许包含名为app_name的字段</strong>。**例如某模块的values目录下包含的strings.xml中有类似如下配置：
```
<resources>
    <string name="app_name">ModuleDemo</string>
</resources>
```
这是不允许的，需要修改。

【**】否则将导致使用该模块的app其应用名称变成该字段定义的。

### 2.6 主题资源审核

**任意values、values-xxxx目录下的styles.xml文件中，<strong>不允许包含名为AppTheme的字段</strong>。**例如某模块的values目录下包含的styles.xml中有类似如下配置：
```
<resources>
    <style name="AppTheme">
        <item name="android:windowNoTitle">true</item>
    </style>
</resources>
```
这是不允许的，需要修改。

【**】否则将导致引擎的相关主题设置被更改，引发一些不可预料的问题。

### 2.7 AndroidManifest.xml文件审核：

●该文件为可选文件。

AndroidManifest.xml为标准的xml格式文件，用于配置该模块所需的权限，用到的系统组件等。
一个全面的AndroidManifest.xml文件参考如下：
<?xml version="1.0" encoding="utf-8"?>
<manifest>

    <uses-permission android:name="android.permission.INTERNET" />

	<activity android:name="com.apicloud.moduleDemo.DemoActivity"/>

	<receiver android:name="com.apicloud.moduleDemo.DemoReceiver" />

	<service android:name="com.apicloud.moduleDemo.DemoService" />

	<provider android:name="com.apicloud.moduleDemo.DemoProvider" />

	<meta-data android:name="moduleDemo" />

</manifest>
结合上表中的代码，AndroidManifest.xml应该满足以下规范：

#### 2.7.1  根节点审核

<strong>根节点必须为 ```<manifest>``` </strong>。
#### 2.7.2 子节点审核

<manifest>节点下只能包含：

```<uses-permission>``` ```<activity>``` ```<receiver>``` ```<service>``` ```<provider>``` ```<meta-data>```

6个类型的子节点。如果包含其他节点，需要修改（比如很多开发者的模块直接将引擎的AndroidManifest.xml文件打包到模块包中，导致存在<application>、<supports-screens>等节点，这是错误的）。

该6个类型的节点，允许有子节点。

#### 2.7.3 <strong>不允许的节点</strong>

1）、<activity>类型的节点中，不允许包含名为：
	```<activity android:name="com.uzmap.pkg.EntranceActivity"/>``` 的节点。
该配置为引擎配置，不允许模块引用。如果包含，需要修改。
	
2）、<receiver>类型的节点中，不允许包含名为：
	```<receiver android:name="com.uzmap.pkg.uzapp.UPExtraBridge" />``` 的节点。
该配置为引擎配置，不允许模块引用。如果包含，需要修改。
	
3）、<service>类型的节点中，不允许包含名为：
	```<service android:name="com.uzmap.pkg.uzsocket.UPnsService" /> ```的节点。
该配置为引擎配置，不允许模块引用。如果包含，需要修改。
	
4）、<provider>类型的节点中，不允许包含名为：
	```<provider android:name="com.uzmap.pkg.uzapp.UProvider" /> ```的节点。
该配置为引擎配置，不允许模块引用。如果包含，需要修改。
	
5）、<meta-data>类型的节点中，不允许包含名为：
	```<meta-data android:name="uz_version" /> ```的节点。
该配置为引擎配置，不允许模块引用。如果包含，需要修改。


### 2.8 source 目录审核：

●**source目录为必须目录。**如果模块包中没有该目录，需要修改。

1）、该目录为模块的代码导出的JAR文件及其依赖的JAR所在目录，可存放多个JAR文件。

2）、该目录下均存放的.jar后缀名的文件，如moduleDemo.jar、baidu.jar、tencent.jar。

3）、该目录不允许包含子目录。如果包含子目录，需要修改。

4）、该目录下不允许存放名为<strong>android-support-v4.jar</strong>的文件。如果存在，需要修改。

	【**】开发者的android-support-v4.jar可能版本很低，导致使用该模块的app运行时发生崩溃。

5）、该目录下不允许存放名类似为<strong>apiEngine v1.1.0.jar</strong>的文件。即引擎文件。 如果存在，需要修改。

	【**】该文件为引擎文件，由服务器动态编译最新版本，模块中若包入，将直接导致使用该模块的app无法使用。

### 2.9 target 目录审核：

●该目录为可选目录。

1）、该目录为模块用到的so库其依赖的so库所在目录，可存放多个so文件。


2）、该目录允许包含子目录，如armeabi-v7a、arm64、x86、mips等，这些子目录均为可选。

如果包含了其中之一的子目录，那么该子目录下存放的so文件必须保持跟target目录下的so文件数量及名称一致。大致如图：


3）、该目录及其子目录下不允许存放名libsec.so的文件。如果存在，需要删除。

【**】该文件为引擎文件，由服务器动态编译最新版本，模块中若包入，将直接导致使用该模块的app无法使用。

### 2.10 module.json文件审核：

●该文件为必须文件。

该文件的结构为一个或者多个JSON对象，每个对象代表一个模块（平台允许一个模块包中同时存放多个模块的），如：

一个对象时的module.json配置：
```
{
	name:'moduleDemo',
	class:'com.apicloud.moduleDemo'
}
```

多个对象时的module.json配置，对象与对象之间以逗号隔开：

```
{
	name:'moduleDemo',
	class:'com.apicloud.moduleDemo'
},
{
	name:'moduleDemo1',
	class:'com.apicloud.moduleDemo1'
},
{
	name:'moduleDemo2',
	class:'com.apicloud.moduleDemo2'
}
```

同时需要检查一下module.json配置中，所有的字符是否均是半角的字符。

凡是不符合以上格式的，均须开发者做更改。

