/*
Title: SuperWebview开发指南IOS
Description:SuperWebview开发指南IOS
Sort: 13
*/


本文档面向所有使用该SDK的开发人员、测试人员、管理人员以及对此感兴趣的其他用户。阅读该文档要求用户熟悉iOS应用开发，了解APICloud平台，如果能对HTML/CSS/JavaScript有一定了解则更好。


## 第一章 简介

SuperWebview是APICloud官方推出的另一项重量级API生态产品，以SDK方式提供，致力于提升和改善移动设备Webview体验差的整套解决方案。APP通过嵌入SuperWebview替代系统Webview，即可在Html5中使用APICloud平台现有的所有端API，以及包括增量更新、版本管理、数据云、推送云、统计分析、积木式模块化开发、所有已经聚合的开方平台服务等在内的云服务能力，增强用户体验，解决移动设备Webview使用过程中出现的兼容能力弱、加载速度慢、功能缺陷等任何问题，帮助开发者解决使用Webview过程中的所有痛点。

SuperWebview继承APICloud终端引擎的包括跨平台能力，模块扩展机制，生命周期管理，窗口系统，事件模型，APP级别的用户体验等在内的所有优秀能力，并且全面打通Html5与Android和IOS之间的交互，同步提供APICloud平台最新的API技术能力和服务，APICloud团队将保持对SuperWebview的持续更新和优化，兼容Html5的新特性，持续推出优质服务。

##第二章 架构设计

###2.1 架构设计

SuperWebview是APICloud终端引擎另一种形态下的开放API，提供“NativeView占主导，SuperWebview层叠辅助”的混合能力，旨在帮助企业或者个人开发者已有的Android和IOS项目提供基于Html5能力的快速业务扩展，无缝使用APICloud云端一体能力提供的优质技术服务，同时保证最优的用户体验。您可以将APP中的某个或多个模块使用SuperWebview进行实现，您甚至可以将SuperWebview SDK当作独立的APP快速开发框架在混合开发中使用。结合APICloud终端引擎的跨平台能力和各项云服务能力，解决诸如跨平台，增量更新，快速版本迭代等APP开发过程中常见的痛点。

SuperWebview整体API开放架构设计如下：

![架构设计](/img/superwebview_ios/superwebview_ios_2.1_01.png)


### 2.2 基本能力

SuperWebview在继承系统Webview接口能力的基础上，主要提供以下功能的接口：

1. API访问权限控制管理功能
2. Android/IOS与Html5之间事件/数据交互功能
3. Web与Native界面直接的混合布局和混合渲染功能
4. 加速数据加载、点击响应和滚动速度
5. 常用手势支持、界面切换动画
6. 访问资源控制管理功能
7. 执行Html5中指定Javascript脚本功能
8. 模块扩展功能，该功能继承自APICloud终端引擎的模块扩展能力
9. Android&IOS开发中常用的网络请求框架，缓存管理等工具接口
10. 统一的生命周期管理，窗口系统，用户体验

## 第三章 使用准备和流程

###3.1 运行环境

####3.1.1 软硬件环境及要求

1. 本SDK支持iOS7.0及以上系统，支持armv7、arm64处理器架构。
2. 本SDK要求使用xcode6及以上版本

#### 3.1.2 工程设置：

1. 找到项目工程的TARGETS -> Build Phases -> Link Binary With Libraries，添加SDK用到的必需的库libz.dylib、libicucore.dylib、libstdc++.dylib。若使用了模块可能还需要额外添加一些相应的库。
2. 找到项目工程的TARGETS -> Build Settings -> Other Linker Flags，添加-ObjC关键字。
3. 若是Xcode7，找到项目工程的TARGETS -> Build Settings -> Enable Bitcode，设置为NO。
4. 添加了模块用到的第三方framework到工程后，若编译时报ld: framework not found xxx之类的错误，那么找到项目工程的TARGETS -> Build Settings -> Framework Search Paths，添加一下framework库所在的目录路径。

###3.2 获取SuperWebview SDK

####3.2.1 创建和编译SDK

1, 登录APICloud官网：http://www.apicloud.com，注册成为APICloud开发者

2, 进入控制台，在“概览”界面新建APP项目，如截图：

![新建项目截图](/img/superwebview_ios/superwebview_ios_3.2_1.png)
![新建项目截图](/img/superwebview_ios/superwebview_ios_3.2_2.png)

3, 点击控制台左侧的“模块”选项卡，导航至模块选择界面，如截图：

![模块选择界面](/img/superwebview_ios/superwebview_ios_3.2_3.png)

勾选您的项目中将要用到的模块，如果不需要，则略过此步骤。

4, 点击控制台左侧的“SuperWebView”选项卡，导航至SDK编译界面，勾选您需要编译的平台，如截图：

![SDK编译界面](/img/superwebview_ios/superwebview_ios_3.2_4.png)

5, 点击“编译SDK”按钮，开始进行SDK的编译，等待片刻，编译完成后，页面中将展示SDK的下载链接，如截图：

![SDK的下载链接](/img/superwebview_ios/superwebview_ios_3.2_5.png)

6, 点击其中的下载链接，下载对应平台的SDK包至本地，并解压

###3.3 SuperWebview SDK包简介

本SDK为一个压缩文件包，其中包含SDK包一份（lib）、示例代码工程一份（Samples）、文档包一份（Docs），可能还包含一份更新说明。基本目录结构如下：

![目录结构](/img/superwebview_ios/superwebview_ios_3.3_1.png)



####3.3.1 lib目录

lib目录下包含您在APICloud网站控制台编译的SDK包的所有资源，包括引擎和模块的库，以及使用到的资源文件，在使用过程中需要将这些文件及文件夹加到您的工程中。lib目录下共包含Engine、Modules目录，可能还有Info.plist文件。

其中：

Engine目录下为APICloud引擎及其头文件；

Modules目录下为所勾选的模块及其所需的资源文件；

Info.plist为一些模块如微信、qq等需要用到的配置信息，需要将其中的内容拷贝或合并到您工程的Info.plist里面

####3.3.2 Docs目录

Docs目录下包含本“开发者使用指南”以及一份html格式的详细API帮助文档，在开发过程中可随时参考该文档，获取满足您APP业务所需的各种API。

####3.3.3 Samples目录

Samples目录下为使用本SDK的几个不同场景下的Demo，包含详细的代码注释。包含以下第四章中代码示例中的项目ProjectFirst。

##第四章 开始嵌入SDK到APP

以下操作过程中，假设您现有或者新建的APP项目名称为“ProjectFirst”。
解压下载得到的SDK包到本地，得到lib、Docs、Samples等文件夹

###4.1 添加SDK到APP工程

1. 将lib/Engine目录下的库和头文件添加到ProjectFirst工程中，添加时选择Create groups选项。
2. 将lib/Modules目录下的所有文件添加到ProjectFirst工程中，添加时选择Create groups选项，再把该目录下的所有文件夹也添加到工程中，添加时务必选择Create folder references选项。
3. 找到项目工程的TARGETS ->Build Phases ->Link Binary With Libraries，添加SDK用到的必需的库libz.dylib、libicucore.dylib、libstdc++.dylib。
4. 找到项目工程的TARGETS->Build Settings->Other Linker Flags，添加-ObjC关键字。
5. 若是Xcode7，找到项目工程的TARGETS -> Build Settings->Enable Bitcode，设置为NO。

###4.2 开始使用API

####4.2.1 初始化SDK

SuperWebview SDK中的所有API必须在显式的调用初始化函数后才能使用，建议在您项目入口AppDelegate的- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions中进行初始化：

```js

-(BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    [[APIManager manager] initSDKWithLaunchOptions:launchOptions];
    
    ViewController *controller = [[ViewController alloc] init];
    UINavigationController *navi = [[UINavigationController alloc] initWithRootViewController:controller];
    self.window = [[UIWindow alloc] initWithFrame:[UIScreen mainScreen].bounds];
    self.window.rootViewController = navi;
    [self.window makeKeyAndVisible];
    return YES;
}
```

####4.2.2  Html5代码的编写和配置

我们采用widget的形式来管理html代码，每个APICloud应用都有一个widget网页包，在前面章节获取SDK的页面中也可以获取该应用的widget。这里我们Samples里面已经有了widget网页包，拷贝过来，将widget目录添加到工程中，添加时选择Create folder references选项。

![目录结构](/img/superwebview_ios/superwebview_ios_4.2_1.png)

关于widget目录的详细介绍，请登录APICloud网站参考[《Widget包结构说明》](http://docs.apicloud.com/APICloud/%E6%8A%80%E6%9C%AF%E4%B8%93%E9%A2%98/widget-package-structure-manual)文档。

关于config.xml文件的详细说明及配置，请登录APICloud网站参考[《APICloud应用配置说明》](http://docs.apicloud.com/APICloud/%E6%8A%80%E6%9C%AF%E4%B8%93%E9%A2%98/app-config-manual)文档。

关于Html代码的编写，也可通过下载APICloud开发工具进行项目的创建，编码，调试，开发完成后直接将整个项目的代码替换掉之前的widget。

####4.2.3 启动SuperWebview

这里我们在ViewController的视图中添加一个button，在button的点击事件中来启动，其中widget://为一个相对路径，表示widget的根目录，开发者也可以直接使用文件的绝对路径。至于选择APIWindowContainer还是APIWidgetContainer则取决于您当前项目的实际情况，APIWindowContainer是一个UIViewcontroller对象，而APIWidgetContainer是一个UINavigationController对象：


```js

- (IBAction)openSuperWebView:(UIButton *)button {
    button.highlighted = NO;
    
    // 这里的widget://表示widget的根目录路径
    NSString *url = @"widget://index.html";
    APIWindowContainer *windowContainer = [APIWindowContainer windowContainerWithUrl:url name:@"root" userInfo:nil];
    [windowContainer startLoad];
    [self.navigationController pushViewController:windowContainer animated:YES];
    self.windowContainer = windowContainer;
}

```

接下来Html页面的加载，渲染，逻辑执行等，SuperWebview会自动帮您完成。
通过SuperWebview提供的APICloud终端引擎的能力，您基于Html的页面，可以无缝使用APICloud云端一体能力中提供的所有API，达到原生APP级别的用户体验。

接下来您可以通过结合第五章中的重要API说明以及SuperWebview的API文档来拓展您APP的各种场景下使用SuperWebview的能力。

##第五章 重要API功能

本章节提供SuperWebview SDK中几个重要API的示例说明，详细API文档请参考附件中的API文档包。

###5.1在html页面中执行脚本

创建一个APIWindowContainer或者APIWidgetContainer对象后，可以在原生和html页面需要交互的时候通过execScript:window:frame: 方法在指定的页面中执行脚本:

```js

- (void)execScript {
    NSString *script = @"alert('在main页面执行脚本测试');";
    [self.windowContainer execScript:script window:@"root" frame:@"sudoku"];
}

```

###5.2 事件机制

原生和前端html数据交互还可以使用事件机制，两者之间可以相互监听和发送事件。APIEventCenter类提供了事件处理。

1）、发送一个事件给html页面，html页面里面通过api.addEventListener方法来监听指定的事件：

```js 

- (void)sendEvent {
    [[APIEventCenter defaultCenter] sendEventWithName:@"showAlert" userInfo:@{@"msg":@"成功发送事件给js"}];
}

```

2）、接收html页面里面发出的事件，html页面里面通过api.sendEvent方法发送事件：

```js

//注册监听
[[APIEventCenter defaultCenter] addEventListener:self selector:@selector(handleEvent:) name:@"abc"];

//监听方法
- (void)handleEvent:(APIEvent *)event {
    NSString *msg = [NSString stringWithFormat:@"收到来自Html5的%@事件，传入的参数为:%@", event.name, event.userInfo];
    UIAlertView *alert = [[UIAlertView alloc] initWithTitle:@"" message:msg delegate:nil cancelButtonTitle:@"确定" otherButtonTitles:nil, nil];
    [alert show];
}


```

3）、移除指定事件或者全部事件的监听：

```js

//移除指定事件监听
[[APIEventCenter defaultCenter] removeEventListener:self name:@"abc"];

//移除所有事件监听
[[APIEventCenter defaultCenter] removeEventListener:self];

```

##第六章 其他

###6.1  一些开放源码

即将开放


##第七章 高级功能

###7.1增量更新（云修复）

注意：使用云修复功能的SuperWebview，您widget的config.xml中必须开启“云修复功能”，即config.xml中必须显式的配置：<preference name="smartUpdate" value="true"/>为true

具体的使用流程：

1）、在左侧控制台选择“云修复”，进入云修复页面，在下拉列表中选择“原生应用”，如截图：

![云修复](/img/superwebview_ios/superwebview_ios_7.1_1.png)

2）、选择“原生应用”后，点击输入框提示需要“手动输入版本号”，如截图：

![云修复](/img/superwebview_ios/superwebview_ios_7.1_2.png)

3）、点击“手动输入版本号”，如下图所示.
其中，IOS要求输入您应用的版本号（即Info.plist文件中的CFBundleShortVersionString字段值）；
Android要求输入您应用的versionCode（即AndroidManifest.xml文件中的“android:versionCode”字段值）；

![云修复](/img/superwebview_ios/superwebview_ios_7.1_3.png)

![云修复](/img/superwebview_ios/superwebview_ios_7.1_4.png)

4）、以ios版本为例：输入版本号之后，需要选择相对应的版本进行云修复操作，如截图：


![云修复](/img/superwebview_ios/superwebview_ios_7.1_5.png)

选择‘1.1.0’作为修复版本，如截图：

![云修复](/img/superwebview_ios/superwebview_ios_7.1_6.png)

5）、APICloud现支持两种云修复方式：提示修复、静默修复。
更新包上传方式分为：输入修复内容的http更新地址或直接上传更新压缩包；
压缩包格式要求为：根目录名称必须为widget，子目录结构保持与APICloudStudio中项目目录一致，并只保留更新的文件，然后将widget目录压缩成.zip包即可：

![云修复](/img/superwebview_ios/superwebview_ios_7.1_7.png)

![云修复](/img/superwebview_ios/superwebview_ios_7.1_8.png)

![云修复](/img/superwebview_ios/superwebview_ios_7.1_9.png)

下面以提示修复为例，选择‘提示修复’中‘上传更新文件’如截图：


![云修复](/img/superwebview_ios/superwebview_ios_7.1_10.png)

上传完成之后，点击右侧‘更新’，成功之后会生成一条记录，如截图：

![云修复](/img/superwebview_ios/superwebview_ios_7.1_11.png)

##第八章 联系我们

如果以上信息无法帮助您解决在开发中遇到的具体问题，请通过以下方式联系我们：

Email：

Tel：

WebSite：http://community.apicloud.com/bbs/
