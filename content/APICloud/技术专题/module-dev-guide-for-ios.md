/*
Title: 模块开发指南_iOS
Description: 模块开发指南_iOS
Sort: 4
*/


[第一章	模块开发介绍](#1)

[第二章	开发第一个模块](#2)

[第三章 其它SDK说明](#3)


#**第一章 模块开发介绍**<div id="1"></div>

##1. 简介

APICloud引擎通过系统Webkit浏览器，实现了HTML+CSS+Javascript开发语言和Objective-C/Java/C/C++等Native开发语言之间的桥接，极大的丰富和增强了标准Javascript的能力。令前端开发者通过JS即可调用移动设备的底层功能，如：电话、短信、定位、多媒体、跨域http请求等，并能将如百度地图、支付宝等第三方厂商的SDK很容易的集成到自己的App中来。

为满足广大开发者自定义扩展Native module的需求，APICloud推出模块扩展SDK，本SDK开放桥接机制，方便具有一定iOS基础的开发者自由开发定义Native扩展模块，丰富JS的能力，提升App的用户体验。

##2. 阅读对象

本文档面向所有使用该SDK的iOS开发人员、测试人员、合作伙伴以及对此感兴趣的其他用户。阅读该文档要求用户熟悉iOS应用开发，并且对Html、CSS、Javascript有一定了解。APICloud引擎强调传输数据的简洁和统一性，因此选择轻量级的JSON作为Javascript和Native语言之间通讯的数据载体，所以要求开发者同时要熟悉Objective-C和Javascript中JSON格式数据的操作。

##4. 开发环境

- Xcode6.0或更高版本
- Mac os x 10.9以上

##5. 下载SDK

前往 http://docs.apicloud.com/APICloud/download 下载最新版本的模块开发SDK，找到里面的ModulesDevProject_iOS.zip，这里面包含ModuleDemo、ModulesDevProject和说明文件，进行模块开发之前一定要先阅读read me.txt，了解各个目录里面的内容和功能。


#**第二章 开发第一个模块**<div id="2"></div>

##1. 创建静态库工程

打开Xcode，在菜单中选择File-New-Project...，在Framework & Library中选择Cocoa Touch Static Library，创建一个名为ModuleDemo的工程，引入必要的UZModule.h头文件到工程中，UZAppDelegate.h和UZAppUtils.h根据需要引入，头文件可以在下载的SDK包里面找到。

##2. 模块类实现

##2.1. 新建模块类

新建一个UZModuleDemo类，继承于UZModule类，其中UZModule类为模块的基类。模块开发过程中文件命名时提倡加前缀，以避免和其它模块冲突。

##2.2. 模块生命周期

当前端js中调用模块方法时，模块首先会被初始化，引擎会调用其 - (id)initWithUZWebView:(UZWebView *)webView 方法；

当模块所在的页面被销毁时，引擎会调用其 - (void)dispose 方法。

##2.3. 启动方法

如果模块需要在应用启动的时候就执行一些操作，那么首先得在module.json里面配置launchClassMethod，例如配置的方法为launch，然后在模块里面实现该方法，当应用启动时该方法就会被执行。

```js
+ (void)launch {
    //
}
```

##2.4. 方法调用

实现 - (void)showAlert:(NSDictionary *)paramDict 方法，用于显示一个对话框，该方法需要在module.json里面配置，然后在前端js里面才可以调用该方法。

如果前端调用该方法时传入了一个function，那么在这里可以通过cbId字段获取该function对应的id，然后在需要的时候把数据通过该function回调给js。

```js
- (void)showAlert:(NSDictionary *)paramDict {
    _cbId = [paramDict integerValueForKey:@"cbId" defaultValue:-1];
    NSString *message = [paramDict stringValueForKey:@"msg" defaultValue:nil];
    UIAlertView *alert = [[UIAlertView alloc] initWithTitle:nil message:message delegate:self cancelButtonTitle:@"取消" otherButtonTitles:@"确定", nil];
    [alert show];
}
```

##2.5. 回调

我们在这里实现UIAlertViewDelegate中的 - (void)alertView:(UIAlertView *)alertView didDismissWithButtonIndex:(NSInteger)buttonIndex 方法，将用户点击的按钮index回调给js端，代码如下：

```js
- (void)alertView:(UIAlertView *)alertView didDismissWithButtonIndex:(NSInteger)buttonIndex {
    if (_cbId >= 0) {
        NSDictionary *ret = @{@"index":@(buttonIndex)};
        [self sendResultEventWithCallbackId:_cbId dataDict:ret errDict:nil doDelete:YES];
    }
}
```

##2.6. 编译静态库

选择iOS Device模式，在工程target的Build Settings中找到Build Active Architecture Only选项，设置为No，同时将iOS Deployment Target设置为iOS 6.0，最终得到包含armv7和arm64架构的静态库。

##2.7. module.json配置

新建一个module.json文件，将以下内容添加进去。

name对应值为模块的名称，js中通过该名称来使用模块；

class对应值为模块的类名；

methods中配置的是实例方法，js中调用的就是这里的方法，多个方法以英文逗号隔开；

launchClassMethod为可选项配置，若配置，引擎将在应用启动的时候调用该方法，注意该方法需是类方法，没有参数。
```js
{
    "name":"moduleDemo",
    "class":"UZModuleDemo",
    "methods":["showAlert"],
    "launchClassMethod":"launch"
}
```

##2.8. 模块包制作

模块包根目录必须以该模块的JS对象名命名，这里为moduleDemo，模块包内包含res_moduleDemo、target文件夹以及module.json。

目录解释：

- res_moduleDemo目录：放置资源文件等，此文件夹会以Create folder references方式加入工程，读取资源文件时需要注意


- target目录：存放编译生成的静态库文件、第三方framework库、bundle束等，该目录下的文件最终会以Create groups方式加入到应用工程


- module.json文件：内容为JSON格式，定义了模块的类名称、JS对象名称、方法等;

将外层的moduleDemo文件夹压缩成为moduleDemo.zip。

##2.9. 云端上传自定义模块

登录到网站控制台，进入你的应用里面，在模块栏里面选择添加模块，输入模块信息并上传moduleDemo.zip文件然后保存。

保存成功后将会显示出该模块，此时模块并未被添加，点击模块右上角的加号添加模块，最后云编译的时候模块就会被编译进去

##2.10. 调试

如果每次都把模块上传到云端编译调试，未免太不方便，找到之前下载的SDK里面的ModulesDevProject文件夹，这是一个包含引擎和测试widget的调试工程，开发模块过程中可以把模块静态库工程中的源代码拖到工程里面进行断点调试，待调试没问题以后再去网站上传自定义模块进行测试。

打开工程，在Supporting Files下面的uz文件夹下面找到module.json文件，其内容为一数组，这里的moduleDemo只是其中的一个模块，一个应用可能需要用到多个模块。
```js
[
 {
    "name":"moduleDemo",
    "class":"UZModuleDemo",
    "methods":["showAlert"],
    "launchClassMethod":"launch"
 }
]
```
前端JS必须使用JSON格式数据作为JS与Native之间交换数据的传参，APICloud引擎会对JS传入的参数进行解析并封装，前端JS使用模块之前需要require模块对象。

找到widget目录下html目录里面的module-con.html，我们在这里面调用showAlert方法，如下：

```js
var param = {
    msg:"Hello App!"
};
var demo = api.require('moduleDemo');
demo.showAlert(param, callBack);

function callBack(ret, err){
    var msg;
    if (ret.index == 0){
        msg = "点击了第一个按钮";
    } else {
        msg = "点击了第二个按钮";
    }
    api.toast({
        msg:msg
    });
}
```

#**第三章 其它SDK说明**<div id="3"></div>

##1. 显示UI视图

对于需要添加UIView类视图的接口，需要提供fixedOn参数，让前端js传入frame的名字，然后将视图添加到该frame上面，同时还应该提供fixed参数，控制视图是否随着frame内容的移动而跟着移动。

UZModule类提供 - (BOOL)addSubview:(UIView *)view fixedOn:(NSString *)fixedOn fixed:(BOOL)fixed 方法，用于往指定的frame上面添加视图。

```js
- (void)show:(NSDictionary *)paramDict {
    NSString *fixedOn = [paramDict stringValueForKey:@"fixedOn" defaultValue:nil];
    BOOL fixed = [paramDict boolValueForKey:@"fixed" defaultValue:YES];
    [self addSubview:yourView fixedOn:fixedOn fixed:fixed];
}
```

同时UZModule提供属性controller，可通过该控制器对目标控制器进行push或者present操作。

##2. 文件路径转换

为消除iOS和Android平台系统间文件路径的差异，APICloud为前端js提供了fs://、widget://和cache://等虚拟文件路径协议，因此，模块在使用js端传入的路径时需要调用UZModule里面的 - (NSString *)getPathWithUZSchemeURL:(NSString *)url 方法来转换成正确的绝对路径。

```js
NSString *path = [paramDict stringValueForKey:@"path" defaultValue:nil];
if (path) {
    NSString *fullPath = [self getPathWithUZSchemeURL:path];
}
```

##3. 获取模块配置信息

部分模块可能要求开发者在config.xml里面配置信息，如第三方平台申请的key之类，配置如下：

```js
<feature name="moduleDemo">
    <param name="apiKey" value="123456" />
</feature>
```

那么在模块中通过UZModule中的 - (NSDictionary *)getFeatureByName:(NSString *)name方法获取配置信息。

```js
NSDictionary *feature = [self getFeatureByName:@"moduleDemo"];
NSString *apiKey = [feature stringValueForKey:@"apiKey" defaultValue:nil];
```

##4. 应用程序代理方法

一些功能需要通过应用程序代理方法才能实现，如获取推送信息、处理第三方应用回调等。

我们在UZAppDelegate中提供了 - (void)addAppHandle:(id <UIApplicationDelegate>)handle 方法，该方法的handle参数为实现了UIApplicationDelegate协议的对象，引擎会对应用程序代理方法做一次分发。

注意不需要时要调用 - (void)removeAppHandle:(id <UIApplicationDelegate>)handle方法移除对象，不然对象不会被释放回收。

如处理应用被第三方应用调起：

```js
- (id)initWithUZWebView:(UZWebView *)webView_ {
    if (self = [super initWithUZWebView:webView_]) {
        [theApp addAppHandle:self];
    }
    return self;
}

- (void)dispose {
    [theApp removeAppHandle:self];
}

#pragma mark - UIApplicationDelegate
- (BOOL)application:(UIApplication *)application handleOpenURL:(NSURL *)url {
    //处理应用被三方应用调起
    return YES;
}
```
