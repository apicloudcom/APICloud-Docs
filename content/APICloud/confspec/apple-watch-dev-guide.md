/*
Title: Apple Watch开发指南
Description: Apple Watch开发指南
Sort: 13
*/


[第一章 适配Apple Watch](#1)

[第二章 风格配置](#2)


#**第一章 适配Apple Watch**<div id="1"></div>

##1. 简介

通过APICloud平台，开发者只需简单几步即可使应用支持Apple Watch，轻松实现在Apple Watch上接收推送功能，同时也不用编写代码，只需简单的配置即可实现APICloud提供的不同类型的应用。

##2. 上传证书

若支持Apple Watch，需要在网站上传证书界面多上传一个.mobileprovision证书，该证书对应的包名为应用的包名加上.watchkitapp构成，例如应用包名为com.company.app，那么该证书对应的则为com.company.app.watchkitapp。

##3. 编译

在云编译界面，选择平台为iOS，然后点击右上角的向下箭头，在弹出菜单中选择Apple Watch可用，其它编译选项和应用之前的设置一致即可。


#**第二章 风格配置**<div id="2"></div>

##1. 目录结构

按照上面的步骤生成的Apple Watch应用使用了默认的配置，APICloud还提供了几种不同风格的界面。进行Apple Watch开发时，所有用到的相关资源文件都放在widget下面的res文件夹下面，其整个目录结构如下图所示：

![图片说明](/img/docImage/watch_dir.png)

其中style目录下面的各个文件夹分别对应不同的风格，里面放置各自风格的资源文件。

##2. style.json

style.json文件里面指定了当前使用哪一种风格界面，目前支持default、news、list等几种风格，例如下面的内容指定了默认风格：

```js
{
    "style":"default",
    "default":{
        "img":"default.png"
    }
}
```

- default

当style字段值为default时，在Apple Watch上面启动应用后会显示一张默认图，图片尺寸为312*340。

default内部字段：

```js
{
	"img":"default.png"			//显示的图片的文件名，文件需放置在default目录下面，默认为default.png
}
```

- news

当style字段值为news时，在Apple Watch上面会使用新闻类界面来展示。效果图如下：

![图片说明](/img/docImage/watch_news.PNG)

news内部字段：

```js
{
	"img_placeholder":"placeholder.png",	//（可选项）加载图片时的占位图文件名，默认为placeholder.png，尺寸为312*290
	"img_time":"icon_time.png",				//（可选项）时间图标文件名，默认为icon_time.png，尺寸为30*30
	"url":"http://xxx",						// 请求地址，通过该地址来获取数据
	"key_data":"data",						//（可选项）获取到JSON数据后进行解析，通过该字段获取列表数据，该字段对应的数据需为JSON数组，字段名默认为data
	"key_title":"title",					//（可选项）数组中的JSON对象，通过该字段获取标题，字段名默认为title
	"key_content":"content",				//（可选项）数组中的JSON对象，通过该字段获取内容，字段名默认为content
	"key_img":"img",						//（可选项）数组中的JSON对象，通过该字段获取图片，字段名默认为img
	"key_time":"time"						//（可选项）数组中的JSON对象，通过该字段获取时间，字段名默认为time
}
```

- list

当style字段值为list时，在Apple Watch上面会使用列表类界面来展示，并且可以点击进入详情页。

列表页效果：

![图片说明](/img/docImage/watch_list.PNG) 

详情页效果：   

![图片说明](/img/docImage/watch_list_detail.PNG)



list内部字段：

```js
{
	"img_placeholder":"placeholder.png",	//（可选项）加载图片时的占位图文件名，默认为placeholder.png，尺寸为312*166
	"url":"http://xxx",						//请求地址，通过该地址来获取数据
	"key_data":"data",						//（可选项）获取到JSON数据后进行解析，通过该字段获取列表数据，该字段对应的数据需为JSON数组，字段名默认为data
	"key_title":"title",					//（可选项）数组中的JSON对象，通过该字段获取标题，字段名默认为title
	"key_content":"content",				//（可选项）数组中的JSON对象，通过该字段获取内容，字段名默认为content
	"key_img":"img"							//（可选项）数组中的JSON对象，通过该字段获取图片，字段名默认为img
}
```