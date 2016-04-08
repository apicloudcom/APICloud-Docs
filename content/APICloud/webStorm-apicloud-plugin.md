/*
Title: 工具：WebStorm插件
Description: WebStorm APICloud 插件的安装和使用说明
Sort: 5
*/
<h2 style="margin-top:30px;">WebStorm APICloud 插件的安装和使用说明</h2>

[开源地址](#a0)

[当前支持环境](#a1)  

[首先下载插件](#a2)

[安装创建新应用插件](#a3)   

[安装创建APICloud文件插件](#a4)

[安装android真机同步](#a5)  

[安装Android本地打包](#a6)

[安装Android 日志输出插件](#a7)  

[安装ios真机同步](#a17) 

[安装ios本地打包](#a8)  

[插件的使用](#a9)  

[官方 Loader 真机同步](#a10)

[官方 Loader 如何更新](#a11)

[自定义 Loader 真机同步](#a12)

[本地打包应用](#a13)

[安装 APICloud 代码提示插件](#a14)

[代码提示功能](#a15)

[使用 subversion](#a16)

<div id="a0"></div>
<h2>开源地址：https://gitcafe.com/APICloud</h2>
  
<div id="a1"></div>

<h2>依赖环境</h2>
<ul>
    java
</ul>
<h2>当前支持环境</h2>
<ul>	
    <li>WebStorm</li>
    <li>Windows 或 Mac</li>
    <li>Android 和 ios手机</li>
</ul>

<div id="a2"></div>

##首先下载插件

1、通过APICloud官方网站下载webStorm-APICloud.zip文件。

2、把webStorm-APICloud.zip解压到WebStorm的工作空间中。

![图片说明](/img/docImage/webstorm-plugin/install.png)

##打开WebStorm 的 'External Tools'选项
Mac   
点击 状态栏中WebStorm ,在下拉菜单中，点击 Preferences 

![图片说明](/img/docImage/webstorm-plugin/mac_set.png)

![图片说明](/img/docImage/webstorm-plugin/mac_Tools.jpg)
Windows

![图片说明](/img/docImage/webstorm-plugin/window_file-set.png)

![图片说明](/img/docImage/webstorm-plugin/windows_Tools.jpg)


<div id="a3"></div>

##安装创建新应用插件

1.新建空白应用。在 'External Tools'选项中，点击 '+' 。在Create Tool中，填写如下内容：

name : 新建空白应用    
Program : java    
Parameters : -jar $ProjectFileDir$/webStorm-APICloud/webStorm_app.jar $ProjectFileDir$ $Prompt$ default

![图片说明](/img/docImage/webstorm-plugin/new_kong.png)

2.新建底部导航应用。在 'External Tools'选项中，点击 '+' 。在Create Tool中，填写如下内容：

name : 新建底部导航应用    
Program : java    
Parameters : -jar $ProjectFileDir$/webStorm-APICloud/webStorm_app.jar $ProjectFileDir$ $Prompt$ bottom

3.新建首页导航应用。在 'External Tools'选项中，点击 '+' 。在Create Tool中，填写如下内容：

name : 新建首页导航应用    
Program : java    
Parameters : -jar $ProjectFileDir$/webStorm-APICloud/webStorm_app.jar $ProjectFileDir$ $Prompt$ home

4.新建侧边导航应用。在 'External Tools'选项中，点击 '+' 。在Create Tool中，填写如下内容：

name : 新建侧边导航应用    
Program : java    
Parameters : -jar $ProjectFileDir$/webStorm-APICloud/webStorm_app.jar $ProjectFileDir$ $Prompt$ slide

<div id="a4"></div>

##安装创建APICloud文件插件

在 'External Tools'选项中，点击 '+' 。在Create Tool中，填写如下内容：

name : 创建APICloud文件    
Program : java    
Parameters : -jar $ProjectFileDir$/webStorm-APICloud/webStorm_app.jar $ProjectFileDir$ $Prompt$ new $FileDir$




<div id="a5"></div>

##安装android真机同步

在 'External Tools'选项中，点击 '+' 。在Create Tool中，填写如下内容：

name : android真机同步    
Program : java    
Parameters : -jar $ProjectFileDir$/webStorm-APICloud/webStorm_loader.jar $ProjectFileDir$/webStorm-APICloud/ $FileDir$/

![图片说明](/img/docImage/webstorm-plugin/Create_Tool.png)

<div id="a6"></div>

##安装Android本地打包

在 'External Tools'选项中，点击 '+' 。在Create Tool中，填写如下内容：

name : android本地打包    
Program : java    
Parameters : -jar $ProjectFileDir$/webStorm-APICloud/webStorm_pkg.jar $ProjectFileDir$/webStorm-APICloud $FileDir$ $ProjectFileDir$ android

![图片说明](/img/docImage/webstorm-plugin/Create_Tool_1.png)

<div id="a7"></div>

##安装Android 日志输出插件

在 'External Tools'选项中，点击 '+' 。在Create Tool中，填写如下内容：

name : Android 日志输出    
Program : java    
Parameters : -jar $ProjectFileDir$/webStorm-APICloud/webStorm_log.jar $ProjectFileDir$/webStorm-APICloud

<div id="a17"></div>

##安装ios真机同步

在 'External Tools'选项中，点击 '+' 。在Create Tool中，填写如下内容：

name : ios真机同步    
Program : java    
Parameters : -jar $ProjectFileDir$/webStorm-APICloud/webStorm_loader.jar $ProjectFileDir$/webStorm-APICloud/ $FileDir$ ios

![图片说明](/img/docImage/webstorm-plugin/ios_tongbu.png)

<div id="a8"></div>

##安装ios本地打包

在 'External Tools'选项中，点击 '+' 。在Create Tool中，填写如下内容：

name : ios本地打包    
Program : java    
Parameters : -jar $ProjectFileDir$/webStorm-APICloud/webStorm_pkg.jar $ProjectFileDir$/webStorm-APICloud $FileDir$ $ProjectFileDir$ ios

![图片说明](/img/docImage/webstorm-plugin/Create_Tool_2.png)


<div id="a9"></div>
##插件的使用

右键点击 工作空间（文件夹） -> 弹出菜中选择 'External Tools' -> 根据需要选择相应的插件。

![图片说明](/img/docImage/webstorm-plugin/use_tools.png)

如果有弹出的输入框，请输入对应的项目名称或者文件名称。

![图片说明](/img/docImage/webstorm-plugin/title.png)

##插件的快捷键设置
打开WebStorm 的 'Keymap' 中'External Tools'选项

![图片说明](/img/docImage/webstorm-plugin/keyboad.png)


选中要设置快捷键的插件，点击右键 -> Add Keyboard Shortcut。在第一个输入框中，输入快捷键。

![图片说明](/img/docImage/webstorm-plugin/shutcut.png)

<div id="a10"></div>
##官方 Loader 真机同步

###Android设备真机同步

1、启动Android模拟器，例如：[海马玩模拟器](http://droid4x.haimawan.com/)下载，或通过 USB 线连接 Android 手机，保证 'USB 调试' 已打开，等待手机与电脑连接成功

2、真机同步快捷键。在widget项目的任意编辑页面通过快捷键可直接进行真机同步。


###IOS设备真机同步

IOS设备在 MAC 系统和Windows 系统下真机同步需要的环境略有不同，Windows系统需要安装配置iTunes 和 iTools;MAC系统只需安装JDK即可。
1、Windows 下 IOS 真机同步安装 iTunes 和 iTools (MAC 下无需此步骤)。
下载地址分别为 [iTunes](http://www.apple.com/cn/itunes/download/) 下载。[iTools](http://www.itools.cn/) 下载。
安装成功后需要把相关目录放到系统环境变量中。环境变量设置如下：

注意：MAC系统无需此配置，只需要安装JDK即可。
右键我的电脑->属性 将弹出 "系统" 界面
![图片说明](/img/docImage/sublime-plugin/sync-system.png)
![图片说明](/img/docImage/sublime-plugin/sync-advanced-setup.png)
![图片说明](/img/docImage/sublime-plugin/sync-system-env.png)

Path 变量的设置 为iTools和iTunes安装位置，如 C:\ProgramData\ThinkSky\iTools\Driver\;C:\Program Files (x86)\Common Files\Apple\Apple Application Support\ 
![图片说明](/img/docImage/sublime-plugin/sync-path-content.png)

2、设置好相关环境后通过 USB 线连接 IOS 手机，等待手机与电脑连接成功

3、右键点击 APICloud 应用文件夹 -> External -> 'IOS真机同步..'

4、由于 IOS 不会自动启动应用，需要等待 WebStorm 提示同步成功代表同步完成。

![图片说明](/img/docImage/webstorm-plugin/end_ios_tongbu.png)

 **注意事项**：

**工作空间的全路径中，不要有空格。**

  

<div id="a11"></div>
##官方 Loader 如何更新

1、到文档的 [Download 页面](http://docs.apicloud.com/APICloud/download)下载最新的官方 AppLoader

2、替换已安装的真机同步插件里的官方 AppLoader（`\插件安装目录\webStorm-APICloud\appLoader\apicloud-loader\`），需要重命名为 'load.apk'。

3、IOS的官方loader替换已安装的真机同步插件里的官方 AppLoader（`\插件安装目录\webStorm-APICloud\appLoader\apicloud-loader-ios\`），需要重命名为 'load.ipa'。

<div id="a12"></div>
##自定义 Loader 真机同步

1、在 APICloud 云平台先创建一个应用，比如叫：moduleTest

2、用 WebStorm 在本地也创建一个应用（方法同[创建新应用](#create-app)），名字自定义，比如也叫：moduleTest

![图片说明](/img/docImage/webstorm-plugin/new_app.png)

3、打开本地创建的 moduleTest 应用的 `config.xml` 文件，把其中的 id 修改成云平台创建的应用 ID

![图片说明](/img/docImage/sublime-plugin/config.png)


4、进入 APICloud 云平台的[代码页面](http://www.apicloud.com/code) -> 点击'上传代码'按钮 -> 点击'选择zip'按钮 -> 选择moduleTest的压缩包 -> 等待上传成功

![图片说明](/img/docImage/sublime-plugin/upload-code.png)

5、在 APICloud 控制台中，配置好应用的端设置、证书、包名等，再进入 -> [模块页面](http://www.apicloud.com/module) -> 添加自己需要的模块

6、到 APICloud 平台 -> [模块页面](http://www.apicloud.com/module) -> 选择'自定义Loader'标签

![图片说明](/img/docImage/sublime-plugin/cust-loader.png)

7、点击自定义 Loader 编译按钮 -> 等待编译完成 -> 下载成功

![图片说明](/img/docImage/sublime-plugin/compile-loader.png)
![图片说明](/img/docImage/sublime-plugin/compile-succ.png)

8、Android 应用的真机同步： 找到 webStorm-APICloud 安装目录 -> `\安装目录\webStorm-APICloud\appLoader\custom-loader`

IOS 应用的真机同步： 找到 webStorm-APICloud 安装目录 -> `\安装目录\webStorm-APICloud\appLoader\custom-loader-ios`

新建一个文件夹，以云端应用 ID 命名，把刚下载的自定义 Loader 放入此目录，重命名为 '`load.apk`'

![图片说明](/img/docImage/webstorm-plugin/custom-loader.png)

9、新建一个 '`load.conf`' 文件（**version - 自定义 Loader 版本号，packagName - 应用包名**），格式如图：

![图片说明](/img/docImage/sublime-plugin/load.conf.png)

10、右键点击本地应用 moduleTest 文件夹 -> 弹出菜中选择 'External Tools' -> Android真机同步 或者 ios真机同步。

11、等待 Android 手机自动打开刚同步的应用，代表同步成功，IOS不会自动打开应用，需要手动打开同步完的应用

<div id="a13"></div>
##本地打包应用


右键点击应用文件夹 -> 弹出菜中选择 'External Tools' -> ...本地打包，打好的apk包在应用文件夹的同级目录，可以直接用于安装。


![图片说明](/img/docImage/webstorm-plugin/apk.png)

<div id="a14"></div>
##安装 APICloud 代码提示插件

1、点击顶部菜单 '`file`' ，选择 '`Import Settings`'。

![图片说明](/img/docImage/webstorm-plugin/install-plugin.png)

2、弹出的对话框输入插件路径，点击OK即可。

![图片说明](/img/docImage/webstorm-plugin/install-plugin1.png)

3、弹出的对话框如图选择'`Live templates`'，点击OK即可，等待重启 '`webstorm`'，即可使用。

![图片说明](/img/docImage/webstorm-plugin/install-plugin2.png)

<div id="a15"></div>
##代码提示功能

确保 APICloud 代码提示插件安装成功，无需额外配置即可使用，在 JS 文件或 `<script>` 标签内部可以触发提示。

* api 对象上面的属性及方法，在输入 `api.` 时触发提示，按 '↑ ↓方向键' 选择需要的 API，选中后按回车键完成代码补全。

![图片说明](/img/docImage/webstorm-plugin/api-obj.png)

* $api 对象上面的方法，在输入 `$api.` 时触发提示，按 '↑ ↓方向键' 选择需要的 API，选中后按回车键完成代码补全。

![图片说明](/img/docImage/webstorm-plugin/apijs.png)

* 模块代码提示：以 fs 模块为例，先输入 '`api.req`' 触发代码提示，require 相应的模块，然后输入'`模块名.`'时可以触发模块代码提示，按 '↑ ↓方向键' 选择需要的 API，选中后按回车键完成代码补全。

![图片说明](/img/docImage/webstorm-plugin/mod-tip.png)
![图片说明](/img/docImage/webstorm-plugin/mod-tip1.png)

注意：
如果想新增自定义的模块代码提示，可以参照[webStorm APICloud代码提示插件编写](/APICloud/技术专题/webStorm-apicloud-snippets)文档。

<div id="a16"></div>
##使用 subversion

![图片说明](/img/docImage/webstorm-plugin/svn_1.png)

![图片说明](/img/docImage/webstorm-plugin/svn_2.png)

![图片说明](/img/docImage/webstorm-plugin/svn_3.png)


![图片说明](/img/docImage/webstorm-plugin/svn_5.png)

![图片说明](/img/docImage/webstorm-plugin/svn_6.png)

选择svn项目名称的路径 ，如图

![图片说明](/img/docImage/webstorm-plugin/svn_7.png)

![图片说明](/img/docImage/webstorm-plugin/svn_8.png)

可能需要输入svn的账户和密码

选择按钮 No

![图片说明](/img/docImage/webstorm-plugin/svn_9.png)

![图片说明](/img/docImage/webstorm-plugin/svn_10.png)

