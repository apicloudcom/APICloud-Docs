/*
Title: SuperWebview开发指南Android
Description:SuperWebview开发指南Android
Sort: 13
*/


本文档面向所有使用该SDK的开发人员、测试人员、管理人员以及对此感兴趣的其他用户。阅读该文档要求用户熟悉Android应用开发，了解APICloud平台，如果能对HTML/CSS/JavaScript有一定了解则更好。


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

1. 本SDK要求最低Android系统版本为：2.3，Google API级别为9
2. 本SDK要求APP开启硬件加速，如关闭，会对渲染效率有一定的影响
3. 本SDK要求Android开发环境配置Android SDK（ADT）的最低版本为5.0，Google API级别为21
4. 本SDK依赖Google提供的最新版的兼容包，即最新版的android-support-v4.jar

#### 3.1.2 必须的权限：

使用SuperWebviewSDK的APP项目，必须在AndroidManifest中申请如下权限：

1, 访问网络

```js
<uses-permission android:name="android.permission.INTERNET" />
```

2, 写外部存储

```js
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
```

3, 获取运营商信息，用于支持提供运营商信息相关的接口

```js
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```


4, 访问wifi网络信息

```js
<uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
```

5, 读取手机当前的状态
 
```js
<uses-permission android:name="android.permission.READ_PHONE_STATE" />
```

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

lib目录下包含您在APICloud网站控制台编译的SDK包的所有资源，包括代码的jar包，so库，必须的资源文件，AndroidManifest.xml文件，在使用过程中需要将这些文件依次拷贝到您的APP项目中。lib目录下共包含libs、res、以及AndroidManifest.xml文件，可能还包含一个assets目录：

其中：

libs目录下为APICloud引擎及所勾选模块的jar和so库；

res目录下为APICloud引擎及所勾选的模块所需的资源文件，包括xml，图片等文件；

assets目录下为APICloud引擎及所勾选模块需要的assets类型资源文件；

AndroidManifest.xml文件包含了APICloud引擎及所勾选的模块所需的权限、Activity、Service等配置

####3.3.2 Docs目录

Docs目录下包含本“开发者使用指南”以及一份html格式的详细API帮助文档，在开发过程中可随时参考该文档，获取满足您APP业务所需的各种API。

####3.3.3 Samples目录

Samples目录下为使用本SDK的几个不同场景下的Demo，包含详细的代码注释。包含以下第四章中代码示例中的项目ProjectFirst。

##第四章 开始嵌入SDK到APP

以下操作过程中，假设您现有或者新建的APP项目名称为“ProjectFirst”。
解压下载得到的SDK包到本地，得到lib、Docs、Samples等文件夹

###4.1 添加SDK到APP工程

1. 将lib/libs目录下的so库和Jar包拷贝到ProjectFirst中对应的libs目录下及armeabi目录中

2. 将lib/res目录下的所有资源文件拷贝到ProjectFirst中对应的res同名目录中，注意values类型资源的合并

3. 将lib/AndroidManifest.xml文件中的所有permission、activity、provider、service、receiver等全部拷贝到ProjectFirst中对应的AndroidManifest中

4. 如果有lib/assets目录，则将lib/assets目录下的所有资源文件拷贝到ProjectFirst中对应的assets目录中

###4.2 开始使用API

####4.2.1 初始化SDK

SuperWebview SDK中的所有API必须在显式的调用初始化函数后才能使用，建议在您项目入口Application的onCreate函数中调用APICloud.initialize(Context)进行初始化。如果您的项目没有Application，可以新建一个类继承自Application，并在AndroidManifest中配置该类。比如MyApplication：

```js

package com.sdk.samples;

import android.app.Application;
import com.uzmap.pkg.openapi.APICloud;

public class MyApplication extends Application{

	@Override
	public void onCreate() {
		super.onCreate();
		APICloud.initialize(this);//初始化APICloud，SDK中所有的API均需要初始化后方可调用执行
	}
}
```

同时在AndroidManifest的application节点配置该类为其name属性：

```js
	
<application
		android:name="com.sdk.samples.MyApplication"
		android:icon="@drawable/ic_logo"
		android:label="@string/app_name">

```

####4.2.2 使用SuperWebview

新建Activity类，继承自ExternalActivity（ExternalActivity的帮助说明请参考第五章重要API说明中的介绍，或者阅读API文档中的详细介绍）。假设ProjectFirst项目中某版块是通过使用Android标准API中的Webview加载远程服务器的Html5页面所实现，该版块所在Activity为WebPageModule类，则将该类改造为继承自ExternalActivity类即可，或者自行新建WebPageModule类继承自ExternalActivity：

```js

	package com.sdk.samples.apicloud;

import android.os.Bundle;
import com.uzmap.pkg.openapi.ExternalActivity;

/**
 * 
 * 您原项目中加载远程Html5页面的版块，现用SuperWebview替换<br>
 * 使用SuperWebview的Activity，需继承自ExternalActivity
 * @author dexing.li
 *
 */
public class WebPageModule extends ExternalActivity {

	@Override
	public void onCreate(Bundle savedInstanceState) {
		super.onCreate(savedInstanceState);
	}
}

```

同时，在AndroidManifest中配置WebPageModule：

```js

<activity android:name="com.sdk.samples.apicloud.WebPageModule" 
			android:screenOrientation="portrait" 
			android:windowSoftInputMode="adjustResize" 
			android:theme="@android:style/Theme.Translucent.NoTitleBar" 
			android:configChanges="orientation|locale|keyboardHidden|screenLayout|screenSize|smallestScreenSize|keyboard" />

```


此外，您可以通过重写ExternalActivity下的shouldOverrideUrlLoading，onPageStarted，onPageFinished等函数，实现SuperWebview与您项目原有业务的对接。


#### 4.2.3 Html5代码的编写和配置

在ProjectFirst项目的assets目录下新建名为widget的目录，并在该目录下新建名为config的xml文件，config.xml文件要求编码为无BOM头UTF-8编码，如图：

![目录结构](/img/superwebview_android/superwebview_android_4.2_3.png)


关于widget目录的详细介绍，请登录APICloud网站参考[《Widget包结构说明》](http://docs.apicloud.com/APICloud/%E6%8A%80%E6%9C%AF%E4%B8%93%E9%A2%98/widget-package-structure-manual)文档。

关于config.xml文件的详细说明及配置，请登录APICloud网站参考[《APICloud应用配置说明》](http://docs.apicloud.com/APICloud/%E6%8A%80%E6%9C%AF%E4%B8%93%E9%A2%98/app-config-manual)文档。

配置完成后，开始编写第一张Html页面，例如index.html，并将其在config.xml中配置为content字段，即声明该Html为SuperWebview的默认入口Html页：

```js
<?xml version="1.0" encoding="UTF-8"?>
<widget id="A0000000000000" version="0.0.1"> 
  <name>ProjectFirst</name>  
  <content src="index.html"/>  
  <access origin="*"/> 
</widget>


```


index.html的详细代码请阅读Samples中的代码，其他Html代码的编写，按照您的产品设计进行即可。

关于Html代码的编写，也可通过下载[APICloud开发工具](http://www.apicloud.com/dev)进行项目的创建，编码，调试，开发完成后直接将整个项目的代码拷贝到ProjectFirst中的assets/widget目录下即可。使用APICloud开发工具开发，可为配合第七章高级功能中的某些操作提供基础。

####4.2.4 启动SuperWebview

在ProjectFirst中任意界面中，通过响应某可点击界面元素的点击事件，启动WebPageModule这个Activity即可：


```js

	@Override
	public void onClick(View v) {
		//实现由之前的加载远程webapp的体验，转向由SuperWebview提供的原生APP体验
		if(v == mButtonWeb){
			Intent intent = new Intent(getContext(), WebPageModule.class);
	       getContext().startActivity(intent);
		}
	}

```

启动完Activity后，接下来Html页面的加载，渲染，逻辑执行等，SuperWebview会自动帮您完成。
通过SuperWebview提供的APICloud终端引擎的能力，您基于Html的页面，可以无缝使用APICloud云端一体能力中提供的所有API，达到原生APP级别的用户体验

接下来您可以通过结合第五章中的重要API说明以及SuperWebview的API文档来拓展您APP的各种场景下使用SuperWebview的能力。

##第五章 重要API功能

本章节提供SuperWebview SDK中几个重要API的简单帮助说明，详细API文档请参考附件中的API文档包。
本SDK开放的API主要位于“com.uzmap.pkg.openapi.*”以及“com.uzmap.pkg.uzkit.*”路径下。

“com.uzmap.pkg.openapi.*”中主要包含提供SuperWebview SDK能力的Activity等UI组件相关的类，主要包括4个重要的开放类：APICloud，ExternalActivity，Html5EventListener，WebViewProvider

“com.uzmap.pkg.uzkit.*”中主要包含一些工具类，如HTTP网络请求，Html5相关工具函数，缓存处理工具等。

###5.1 openapi相关API类简介

<table>
<tr><td width="16%">类</td><td>描述及函数原型</td></tr>
<tr><td>APICloud</td><td> 提供了所有使用SuperWebview的静态方法，在使用本SDK下的所有函数前，必须调用APICloud.initialize(Context)函数初始化终端引擎</td></tr>
<tr><td>ExternalActivity</td><td> SuperWebview开放的基本UI组件Activity，您项目中任何使用SuperWebview能力的Activity必须继承自该Activity。该类继承自系统Activity，主要包括以下开放API：
</br>
1. evaluateJavascript(String) 
向某个window或者frame执行一段JS脚本
</br>
2. addHtml5EventListener(Html5EventListener) 
设置一个Html5事件监听器，监听来自Html5页面广播出来的事件
</br>
3. removeHtml5EventListener(Html5EventListener) 
移除一个Html5事件监听器
</br>
4. removeAllHtml5EventListener() 
移除所有Html5事件监听器
</br>
5. sendEventToHtml5(eventName, extra) 
发送一个事件并广播给当前所有已加载的Html5页面，如果其中有页面监听了该事件，它将收到广播
</br>
6. onProgressChanged(WebViewProvider, progress) 
当Html5页面的加载进度发生变化时，引擎将通过该接口回调给应用
</br>
7. onPageStarted(WebViewProvider, url, pageIcon) 
当某个Html5页面开始加载时，引擎将通过该接口回调给应用
</br>
8. onPageFinished(WebViewProvider, url) 
当某个Html5页面加载结束时，引擎将通过该接口回调给应用
</br>
9. shouldOverrideUrlLoading(WebViewProvider, url) 
当引擎内部某个webview即将请求加载一个url时，将通过该接口通知应用，如果应用拦截并自行处理，引擎将不再处理该请求。
</br>
10. onReceivedTitle(WebViewProvider, title) 
当引擎内部某个webview收到Html5页面标题时，将通过该接口回调给应用
</br>
11. shouldForbiddenAccess(host, module, api)
当某host地址的html页面即将访问某api时，将通过该接口通知应用，应用可以决定是否拦截，控制其不允许访问
</br>
12. 如果启动ExternalActivity实现的子类Activity时，Intent中传入了“startUrl”字段，那么该Activity将自动以该startUrl配置的URL作为首页加载入口。默认情况下使用widget/config.xml中的content字段配置作为入口</td></tr>
<tr><td>Html5EventListener</td><td>Html5页面事件监听器，该监听允许您监听来自Html5页面通过api.sendEvent发出的自定义事件广播，实现原生应用与Html5之间的数据交互及解耦。
可通过ExternalActivity.addHtml5EventListener(Html5EventListener)进行注册监听
Html5事件将通过Html5EventListener.onReceive(WebViewProvider, Object)回调</td></tr>
<tr><td>WebViewProvider</td><td>APICloud终端引擎中SuperWebview的代理类，内部包含一个APIWebview的实例。该类以代理的形式开放了webview的诸多API，如：
</br>
1. getName() 
获取webview所在frame的name，与api.openFrame时传入的name对应，主window所在frame的name为固定值“main”
</br>
2. getWinName() 
获取webview所在window的name，与api.openWin时传入的name对应，根window的name为固定值“root”
</br>
3. evaluateJavascript(script) 
向该webview执行一段js脚本
</br>
4. loadUrl(url) 
请求该webview加载一条url
</br>
5. stopLoading() 
要求当前webview停止加载
</br>
6. reload() 
要求webview重新加载当前页面
</br>
7. goBack() 
要求当前webview回退历史记录
</br>
8. goForward() 
要求当前webview前进历史记录</td></tr>
<tr>
		<td></td>
		<td></td>
	</tr>
</table>

###5.2 uzkit相关API类简介

<table>
	<tr>
		<td width="20%">类</td>
		<td>描述及函数原型</td>
	</tr>
<tr>
		<td>UZUtility</td>
		<td>静态工具函数库，提供与Html5处理相关，APP相关的工具函数</td>
	</tr>
<tr>
		<td>request.APICloudHttpClient</td>
		<td>APICloud终端引擎全局标准HTTP请求处理类，包含：
</br>
request(Request) 插入一个http请求
</br>
cancelRequests(Object) 取消某个http请求
</br>
download(HttpDownload) 插入一个http下载请求
</br>
cancelDownload(Object) 取消某个http下载请求
</br>
disPlayImage(ImageOption, ImageView) 请求显示远程服务器上的某张图片资源到ImageView
….
</br>
等诸多HTTP数据请求相关的函数，非常方便客户端向服务器发起数据请求</td>
	</tr>
<tr>
		<td>request.Request</td>
		<td>所有类型HTTP请求的超类</td>
	</tr>
<tr>
		<td>request.HttpGet</td>
		<td>HTTP的GET请求类。通过APICloudHttpClient.request(HttpGet)发起</td>
	</tr>
<tr>
		<td>request.HttpPost</td>
		<td>HTTP的POST请求类。通过APICloudHttpClient.request(HttpPost)发起</td>
	</tr>
<tr>
		<td>request.HttpDownload</td>
		<td>HTTP的GET请求类，通常为请求下载非文本类型数据的大文件。
         通过APICloudHttpClient.download(HttpDownload)发起</td>
	</tr>
<tr>
		<td>request.HttpDelete</td>
		<td>HTTP的DELETE请求类。通过APICloudHttpClient.request(HttpDelete)发起</td>
	</tr>
<tr>
		<td>request.HttpPut</td>
		<td>HTTP的PUT请求类。通过APICloudHttpClient.request(HttpPut)发起</td>
	</tr>
<tr>
		<td>request.HttpHead</td>
		<td>HTTP的HEAD请求类。通过APICloudHttpClient.request(HttpHead)发起</td>
	</tr>
<tr>
		<td>request.HttpOptions</td>
		<td>HTTP的OPTIONS请求类。通过APICloudHttpClient.request(HttpOptions)发起</td>
	</tr>
<tr>
		<td>request.HttpPatch</td>
		<td>HTTP的PATCH请求类。通过APICloudHttpClient.request(HttpPatch)发起</td>
	</tr>
<tr>
		<td>request.HttpTrace</td>
		<td>HTTP的TRACE请求类。通过APICloudHttpClient.request(HttpTrace)发起</td>
	</tr>
<tr>
		<td>request.HttpParams</td>
		<td>发起POST/PUT/PATCH请求时用于配置提交的数据</td>
	</tr>
<tr>
		<td>request.RequestCallback</td>
		<td>HTTP请求的回调，通过request.setCallback(callback)使用</td>
	</tr>
<tr>
		<td>request.HttpResult</td>
		<td>HTTP请求的结果，通过RequestCallback.onFinish(HttpResult)回调</td>
	</tr>
<tr>
		<td></td>
		<td></td>
	</tr>
</table>


##第六章 其他

###6.1 关于代码混淆：

如果开发者在发布版本时需要混淆自己的代码，请在混淆文件（一般默认为Android工程下proguard-project.txt或者proguard.cfg文件）中添加如下说明：

```js
	
-libraryjars libs/apiEngine {verion}.jar
-dontwarn  com.uzmap.pkg.*
-keep class  com.uzmap.pkg.** { *;}

```


其中，{version}为引擎jar包对应的版本



###6.2 SDK固有资源说明及替换

原则上，SuperWebviewSDK中包含的任何XML、图片等资源文件，均需要原封不动的拷贝到您的项目中，如果熟悉APICloud平台的开发者，则可在此基础上替换或者更改这些资源，实现UI效果的自由定制。



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
