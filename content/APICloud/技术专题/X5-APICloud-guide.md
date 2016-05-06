/*
Title: 如何在APICloud平台使用腾讯X5引擎
Description: 如何在APICloud平台使用腾讯X5引擎
*/

#概述

目前APICloud与腾讯X5引擎已经达成全方位的深度合作，APICloud在多个产品线深度集成X5引擎，广大APICloud开发者们即日起可通过以下几方面在你的APP中使用X5引擎，享受X5引擎带来的种种优势。

腾讯X5引擎官网：http://x5.tencent.com ；
产品及优势介绍，可通过：http://x5.tencent.com/doc?id=1001 了解；

下面介绍如何在APICloud平台使用腾讯X5引擎：

#一、在SuperWebView中使用

SuperWebview是基于APICloud核心引擎的解决方案级SDK产品，提供给原生开发使用，原生应用集成SuperWebview SDK后，即可方便的通过SuperWebview来进行H5页面展示以及扩展API调用。SuperWebview详细介绍及使用流程见[《SuperWebview开发指南》](/APICloud/技术专题/SuperWebview-guide-for-android)。

在动态编译SuperWebview SDK时，针对Android平台，我们提供了基于APICloud核心引擎的版本和基于腾讯X5引擎的版本供开发者选择，如果开发者勾选了腾讯X5的版本，动态编译后的SDK中即搭载X5引擎。

####使用流程：

  1，登录APICloud官网：http://www.apicloud.com

  2，进入控制台创建 “Native” 应用

  3，创建成功后进入该应用的预览界面，点击左侧“动态生成”，进入SDK编译界面

  4，在平台选择处勾选“腾讯X5(Android)”，如下图：
    ![在平台选择处勾选“腾讯X5\(Android\)”](/img/x5/1.png)

  5，点击“编译SDK”按钮进行编译

  6，将编译完成后的SDK下载，集成至你的APP项目中使用

  7，集成该SDK后的APP在调用SuperWebview加载H5页面时，将使用X5引擎执行

#二、在WebApp中使用

APICloud提供对已有H5站点的“打包加壳”服务，通过在控制台创建“WebApp”项目，填写您的H5站点地址，进行启动界面，ICON图标等简单配置后，即可将您的H5站点一键编译生成Android和IOS两个平台的APP安装包，该APP上线后能够使用APICloud提供的如推送、版本更新等各项云服务。

在编译WebApp时，针对Android平台，我们提供了基于APICloud核心引擎的版本和基于腾讯X5引擎的版本供开发者选择，如果开发者勾选了腾讯X5的版本，则编译后的APP将使用X5引擎加载您的H5站点。因X5引擎兼容微信的缘故，该H5站点将拥有其在微信当中运行效果和体验。

####使用流程：

  1，登录APICloud官网：http://www.apicloud.com

  2，进入控制台创建 “Web” 应用

  3，创建成功后进入该应用的预览界面，分别进行 “端设置”、“证书”等配置

  4，点击左侧“云编译”，进入APP编译界面

  5，在平台选择处勾选“腾讯X5(Android)”，如下图：
    ![在平台选择处勾选“腾讯X5\(Android\)”](/img/x5/2.png)

  6，点击“云编译”按钮进行编译

  7，编译完成后的APP，将使用X5引擎加载运行

#三、在DeepEngine聚合API中使用

我们在聚合API中提供了名为“webBrowser”的内置浏览器功能模块，该模块内部集成了X5引擎，方便开发者在DeepEngine中使用X5引擎进行H5页面的展示。该模块通过可定制度高的“BrowserView”和独立Browser（类似于微信）两种方式提供API。详细API见[《webBrowser API文档》](/端API/功能扩展/webBrowser)

####使用流程：

  1，登录APICloud官网：http://www.apicloud.com

  2，进入控制台创建 “Native” 应用

  3，创建成功后进入该应用的预览界面，点击左侧“模块”，进入模块绑定界面

  4，搜索“webBrowser”模块，并勾选，如下图：
    ![搜索“webBrowser”模块，并勾选](/img/x5/3.png)

此后您编译的APP或者自定义loader中将包含搭载X5引擎的webBrowser模块，您可以在代码中通过：

api.require(“webBrowser”)的方式使用搭载X5引擎的模块，调用其API完成您的需求。
如：

打开一个X5View到当前Window：webBrowser.openView({param});

加载Url：webBrowser.loadUrl({param});

执行脚本：webBrowser.loadScript({param});

直接打开独立浏览器：webBrowser.open({param});

等等

#四、一些X5引擎相关的事项

X5引擎目前只提供Android版本。

X5引擎采用动态加载机制，即只有当设备和网络环境满足X5引擎的加载要求时，才会使用X5引擎，其他情况下，将使用系统自带Webkit。

####相关QA请参考X5官网：

常见问题：http://x5.tencent.com/doc?id=1002_1

CSS相关：http://x5.tencent.com/guide?id=2002

JS相关：http://x5.tencent.com/guide?id=2003

网络相关：http://x5.tencent.com/guide?id=2005

渲染相关：http://x5.tencent.com/guide?id=2006

音频视频相关：http://x5.tencent.com/guide?id=2009

腾讯移动产品论坛X5专区：http://bbs.mb.qq.com/forum-110-1.html