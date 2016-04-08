/*
Title: 工具：Sublime插件
Description: Sublime APICloud 插件的安装和使用说明
Sort: 5
*/
<h2 style="margin-top:30px;">Sublime APICloud 插件的安装和使用说明</h2>

[开源地址](#a0)

[当前支持环境](#a1)  

[首先安装 Package Control](#a2)

[安装真机同步插件](#a3) 

[安装 APICloud 代码提示插件](#a4)  

[安装本地打包插件](#a11)  

[创建新应用](#a5)

[创建APICloud文件](#a5_0)  

[压缩 Widget 包，用于代码上传](#a6)  

[官方 Loader 真机同步](#a7)

[官方 Loader 如何更新](#a10)  

[自定义 Loader 真机同步](#a8)  

[本地打包应用](#a12)  

[使用SVN](#a13)  

[回显Android调试日志](#a14)  

[代码提示功能](#a9)  


<div id="a0"></div>
<h2>开源地址：https://gitcafe.com/APICloud</h2>


<div id="a1"></div>
<h2>当前支持环境</h2>

<ul>
    <li>Sublime Text 3</li>
    <li>Windows 或 Mac</li>
    <li>Android 手机</li>
	<li>Ios 手机</li>
</ul>

<div id="a2"></div>
##首先安装 Package Control

1、通过快捷键 <code>ctrl+`</code> 或者 <code>View > Show Console</code> 菜单打开控制台

2、粘贴下面的代码后，回车安装

3、参考资料[Package Control 安装](https://packagecontrol.io/installation)

```python
import urllib.request,os,hashlib; h = '2915d1851351e5ee549c20394736b442' + '8bc59f460fa1548d1514676163dafc88'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
```

<div id="a3"></div>
##安装真机同步插件

1、快捷键 '`Ctrl + Shift + P`' （Mac 为：'`Command + Shift + P`'）（或顶部菜单 -> Tools -> Command Palette），输入 'install'，选择 '`Package Control:Install Package`'

![图片说明](/img/docImage/sublime-plugin/install-plugin.png)

2、弹出的插件搜索框输入 'apicloud'，选择 'APICloudLoader'，回车等待安装完毕，重启 Sublime Text，即可使用。

![图片说明](/img/docImage/sublime-plugin/install-plugin1.png)

<div id="a4"></div>
##安装 APICloud 代码提示插件

1、快捷键 '`Ctrl + Shift + P`' （Mac 为：'`Command + Shift + P`'）（或顶部菜单 -> Tools -> Command Palette），输入 'install'，选择 '`Package Control:Install Package`'

![图片说明](/img/docImage/sublime-plugin/install-plugin.png)

2、弹出的插件搜索框输入 'apicloud'，选择 'APICloudSnippets'，回车等待安装完毕，重启 Sublime Text，即可使用。

![图片说明](/img/docImage/sublime-plugin/install-plugin1.png)

<div id="a11"></div>
##安装本地打包插件

1、快捷键 '`Ctrl + Shift + P`' （Mac 为：'`Command + Shift + P`'）（或顶部菜单 -> Tools -> Command Palette），输入 'install'，选择 '`Package Control:Install Package`'

![图片说明](/img/docImage/sublime-plugin/install-plugin.png)

2、弹出的插件搜索框输入 'apicloud'，选择 'APICloudPackage'，回车等待安装完毕，重启 Sublime Text，即可使用。

![图片说明](/img/docImage/sublime-plugin/api-pkg.png)

<div id="a5"></div>
<div id="create-app"></div>
##创建新应用

1、在任意目录新建一个项目文件夹，名字自定义，比如叫 'workspace'

2、把 'workspace' 文件夹拖至 Sublime Text 开发工具，Sublime Text 左侧出现了一个新的项目文件夹

3、右键点击 'workspace' 文件夹 -> 弹出菜单顶部选择 '新建APICloud项目' -> 根据需要选择相应的应用框架

![图片说明](/img/docImage/sublime-plugin/new-project.png)

4、底部弹出一个输入框 -> 填入 APICloud 项目名称 -> 点击回车键

![图片说明](/img/docImage/sublime-plugin/app-name.png)

5、新项目创建成功

![图片说明](/img/docImage/sublime-plugin/new-app.png)

<div id="a5_0"></div>
##创建APICloud文件
点击此菜单项将在新建文件中生成默认的html相关模板内容。


<div id="a6"></div>
##压缩 Widget 包，用于代码上传

1、打开本地应用文件夹的 `config.xml` 文件，把其中的 id 修改成云平台创建的应用 ID

![图片说明](/img/docImage/sublime-plugin/config.png)

2、右键点击应用项目文件夹 -> 选择 '压缩Widget包'，压缩后的 zip 包位于同级目录，压缩后的 zip 包可直接用于 APICloud 平台的[代码上传](http://www.apicloud.com/code)功能。

![图片说明](/img/docImage/sublime-plugin/upload-code.png)

<div id="a7"></div>
##官方 Loader 真机同步
###Android设备真机同步

1、启动Android模拟器，例如：[海马玩模拟器](http://droid4x.haimawan.com/)下载，或通过 USB 线连接 Android 手机，保证 'USB 调试' 已打开，等待手机与电脑连接成功

2、右键点击 APICloud 应用文件夹 -> 弹出菜单顶部选择 'Android真机同步..'

![图片说明](/img/docImage/sublime-plugin/sync-android.png)

3、等待 Android 手机自动打开刚同步的应用，代表同步成功

![图片说明](/img/docImage/sublime-plugin/async-success.png)

4、真机同步快捷键。在widget项目的任意编辑页面通过快捷键可直接进行真机同步。默认快捷键windows: ctrl+r；mac: command+r。也支持用户修改，修改位置：插件安装目录\Sublime-APICloud-Loader\  下文件 Default (Windows).sublime-keymap(针对windows系统)或 Default (OSX).sublime-keymap(针对mac系统)。


 **注意事项**：

**Mac 系统用户请确保插件包中 tools 目录（Mac 系统：`/Users/用户名/Library/Application Support/Sublime Text 3/Packages/APICloudLoader/tools`）下的 adb 命令有执行权限，可通过  `ls -al adb` 查看该命令是否有执行权限。 通过 `chmod +x adb` 为adb添加执行权限。**

###IOS设备真机同步

IOS设备在 MAC 系统和Windows 系统下真机同步需要的环境略有不同，Windows系统需要安装配置iTunes 和 iTools, 同时下载 32位JRE环境到插件包中;MAC系统只需安装 **JDK 1.7** 即可。

1、Windows 下 IOS 真机同步安装 iTunes 和 iTools (MAC 下无需此步骤)。
下载地址分别为 [iTunes](http://www.apple.com/cn/itunes/download/) 下载。[iTools](http://www.itools.cn/) 下载。
安装成功后需要把相关目录放到系统环境变量中。环境变量设置如下：

注意：MAC系统无需此配置，只需要安装JDK即可。
右键我的电脑->属性 将弹出 "系统" 界面
![图片说明](/img/docImage/sublime-plugin/sync-system.png)
![图片说明](/img/docImage/sublime-plugin/sync-advanced-setup.png)
![图片说明](/img/docImage/sublime-plugin/sync-system-env.png)

Path 变量的设置 为iTools和iTunes安装位置 **(如果此时已开启Sublime，需要重启Sublime)**，如 C:\ProgramData\ThinkSky\iTools\Driver\;C:\Program Files (x86)\Common Files\Apple\Apple Application Support\ 
![图片说明](/img/docImage/sublime-plugin/sync-path-content.png)

2、IOS 真机同步通过Java实现同步功能，Windows环境需要从官网下载32位JRE环境并保存到package中 tools 目录下并解压。JRE可以通过[JRE官网下载](http://7xo3nl.com2.z0.glb.qiniucdn.com/jre.zip)获得。
MAC系统可直接安装JDK即可。
![图片说明](/img/docImage/sublime-plugin/sync-jre.png)

3、设置好相关环境后通过 USB 线连接 IOS 手机，等待手机与电脑连接成功

4、右键点击 APICloud 应用文件夹 -> 弹出菜单顶部选择 'IOS真机同步..'

![图片说明](/img/docImage/sublime-plugin/sync-ios.png)

5、由于 IOS 不会自动启动应用，需要等待 Sublime 提示同步完成代表同步完成(鉴于Windows系统会回显同步过程，对于无设备连接时，回显界面会停留在"start listening..." 然后退出，此时Sublime也会显示同步完成；Mac系统由于没有回显，会正常提示"未发现连接的设备")。

![图片说明](/img/docImage/sublime-plugin/sync-ios-success.png)

6、IOS真机同步快捷键。在widget项目的任意编辑页面通过快捷键可直接进行真机同步。默认快捷键windows: ctrl+alt+r；mac: command+alt+r。也支持用户修改，修改位置：插件安装目录\Sublime-APICloud-Loader\  下文件 Default (Windows).sublime-keymap(针对windows系统)或 Default (OSX).sublime-keymap(针对mac系统)。

<div id="a10"></div>
##官方 Loader 如何更新

1、到文档的 [Download 页面](http://docs.apicloud.com/APICloud/download)下载最新的官方 AppLoader

2、Android的官方loader替换已安装的真机同步插件里的官方 AppLoader（`\插件安装目录\Sublime-APICloud-Loader\appLoader\apicloud-loader\`），需要重命名为 'load.apk'。

3、IOS的官方loader替换已安装的真机同步插件里的官方 AppLoader（`\插件安装目录\Sublime-APICloud-Loader\appLoader\apicloud-loader-ios\`），需要重命名为 'load.ipa'。

<div id="a8"></div>
##自定义 Loader 真机同步

1、在 APICloud 云平台先创建一个应用，比如叫：moduleTest

2、用 Sublime Text 在本地也创建一个应用（方法同[创建新应用](#create-app)），名字自定义，比如也叫：moduleTest

![图片说明](/img/docImage/sublime-plugin/moduleTest.png)

3、打开本地创建的 moduleTest 应用的 `config.xml` 文件，把其中的 id 修改成云平台创建的应用 ID

![图片说明](/img/docImage/sublime-plugin/config.png)

4、右键点击本地应用 moduleTest 文件夹 -> 弹出菜单顶部选择'压缩Widget包..'

![图片说明](/img/docImage/sublime-plugin/zip.png)

5、进入 APICloud 云平台的[代码页面](http://www.apicloud.com/code) -> 点击'上传代码'按钮 -> 点击'选择zip'按钮 -> 选择刚才的压缩包 -> 等待上传成功

![图片说明](/img/docImage/sublime-plugin/upload-code.png)

6、在 APICloud 控制台中，配置好应用的端设置、证书、包名等，再进入 -> [模块页面](http://www.apicloud.com/module) -> 添加自己需要的模块
真机同步快捷键
7、到 APICloud 平台 -> [模块页面](http://www.apicloud.com/module) -> 选择'自定义Loader'标签

![图片说明](/img/docImage/sublime-plugin/cust-loader.png)

8、点击自定义 Loader 编译按钮 -> 等待编译完成 -> 下载成功

![图片说明](/img/docImage/sublime-plugin/compile-loader.png)
![图片说明](/img/docImage/sublime-plugin/compile-succ.png)

9、Android 应用的真机同步： 找到 Sublime Text 安装目录 -> `D:\安装目录\Data\Packages\APICloudLoader\appLoader\custom-loader`（Mac 系统为：`/Users/用户名/Library/Application Support/Sublime Text 3/Packages/APICloudLoader/appLoader/custom-loader`）
IOS 应用的真机同步： 找到 Sublime Text 安装目录 -> `D:\安装目录\Data\Packages\APICloudLoader\appLoader\custom-loader-ios`（Mac 系统为：`/Users/用户名/Library/Application Support/Sublime Text 3/Packages/APICloudLoader/appLoader/custom-loader-ios`）

10、新建一个文件夹，以云端应用 ID 命名，把刚下载的自定义 Loader 放入此目录，Android 应用重命名为 '`load.apk`,IOS 应用则为load.ipa'。

![图片说明](/img/docImage/sublime-plugin/custom-loader.png)

11、获取应用包名。如图：

![图片说明](/img/docImage/sublime-plugin/apiclouder-loader-pkgname.png)

12、新建一个 '`load.conf`' 文件（**version - 自定义 Loader 版本号，packageName - 应用包名**），格式如图：

**注意：IOS平台的自定义loader，如果没有上传自己的IOS证书，则所有app项目的自定义loader统一包名为“com.apicloud.customloader”**

![图片说明](/img/docImage/sublime-plugin/load.conf.png)

13、右键点击本地应用 moduleTest 文件夹 -> 弹出菜单顶部选择'Android真机同步..' 或 'IOS真机同步..'

14、等待真机同步完成， Android 手机自动打开刚同步的应用，代表同步成功，IOS不会自动打开应用，需要手动打开同步完的应用。

<div id="a12"></div>
##本地打包应用

**注意事项：**

**Mac 系统用户请确保插件包中 `tools` 目录（Mac 系统：`/Users/用户名/Library/Application Support/Sublime Text 3/Packages/APICloudLoader/tools/mac`）下的 aapt,apktool,zipalign 命令有执行权限，可通过 `ls -al aapt` 查看某个命令(如aapt)是否有执行权限。 通过 `chmod +x aapt` 为aapt添加执行权限，其他命令权限修改与其相同。**

右键点击应用文件夹 -> 弹出菜单选择 '本地打包...' -> 等待打包完成，打好的apk包在应用文件夹的同级目录，可以直接用于安装。

![图片说明](/img/docImage/sublime-plugin/local-pkg.png)

![图片说明](/img/docImage/sublime-plugin/pkg-succ.png)

<div id="a13"></div>
##使用 SVN
###Windows下使用 SVN
1、Windows下 SVN 插件推荐使用官方提供的插件。可在[官方Sublime-TortoiseSVN插件](http://7xo3nl.com2.z0.glb.qiniucdn.com/TortoiseSVN.zip)进行下载。下载压缩包解压到 \插件安装目录 ( 顶部菜单 -> Preferences -> Browse Packages )。确保文件名为 TortoiseSVN ，如图所示：

![图片说明](/img/docImage/sublime-plugin/svn-folder-name.png)

2、请确保系统安装了 TortoiseSVN 客户端，[TortoiseSVN 客户端下载](http://tortoisesvn.net/downloads.html)。

![图片说明](/img/docImage/sublime-plugin/svn-tortoise-icon.png)

3、打开ST3 ，在ST3菜单中 Preferences -> Package Setting -> TortoiseSVN -> Settings Defalut 打开TortoiseSVN的配置文件，配置tortoiseproc_path为系统TortoiseSVN客户端的可执行程序。如"tortoiseproc_path": "C:\\Program Files\\TortoiseSVN\\bin\\TortoiseProc.exe"

![图片说明](/img/docImage/sublime-plugin/svn-mainmenu-setting.png)

![图片说明](/img/docImage/sublime-plugin/svn-setting.png)


4、通过右键目录进行相关 SVN 操作，插件会自动弹出 TortoiseSVN 的客户端界面。

![图片说明](/img/docImage/sublime-plugin/svn-sidebar-menu.png)

###Mac下使用 SVN
对于Mac系统(Windows也支持)可安装下边的第三方插件。

1、首先安装 SVN 插件

快捷键 '`Ctrl + Shift + P`' （Mac 为：'`Command + Shift + P`'）（或顶部菜单 -> Tools -> Command Palette），输入 'install'，选择 '`Package Control:Install Package`'

2、弹出的插件搜索框输入 'SVN'，选择第一项，回车等待安装完毕，重启 Sublime Text，即可使用。

![图片说明](/img/docImage/sublime-plugin/svn-plugin.png)

3、右键选择任一空文件夹，弹出菜单选择 'SVN' -> 'Checkout...'，底部弹出的输入框，按规定格式输入用户名，密码及 SVN 地址，输入完毕按回车，等待项目检出完毕。

![图片说明](/img/docImage/sublime-plugin/svn-checkout.png)

![图片说明](/img/docImage/sublime-plugin/svn-address.png)

格式为：**svn://用户名:密码@svn地址**

APICloud 平台的 SVN 分支密码在[代码页面](http://apicloud.com/code)获取：

![图片说明](/img/docImage/sublime-plugin/svn-branch.png)

正确的例子：`svn://jinlong.zhang@app3c.com:96e79218965eb72c92a549dd5a330112@svn3.apicloud.com/A6997434778733/tempTest`

4、右键点击刚检出项目里的文件，弹出菜单 -> 'SVN'，可以看到更多的 SVN 功能：'更新'、'提交'、或'比较'等等。

![图片说明](/img/docImage/sublime-plugin/svn-function.png)

Mac版本常见问题：

1、Mac版本的Sublime Text运行SVN插件需要使用相关的svn命令，所以要在Mac上安装Xcode。
2、如果已经安装了Xcode但是还是找不到svn命令，可以通过xcode-select --switch XcodePath来指定Xcode路径。

<div id="a9"></div>
##代码提示功能

确保 APICloud 代码提示插件安装成功，无需额外配置即可使用，在 JS 文件或 `<script>` 标签内部可以触发提示。

* api 对象上面的属性及方法，在输入 `api-` 时触发提示，按 '↑ ↓方向键' 选择需要的 API，选中后按回车键完成代码补全。

![图片说明](/img/docImage/sublime-plugin/api-obj.png)

* $api 对象上面的方法，在输入 `apijs-` 时触发提示，按 '↑ ↓方向键' 选择需要的 API，选中后按回车键完成代码补全。

![图片说明](/img/docImage/sublime-plugin/apijs.png)

* 模块代码提示：以 fs 模块为例，先输入 '`api-req`' 触发代码提示，require 相应的模块，然后输入'`模块名-`'时可以触发模块代码提示，按 '↑ ↓方向键' 选择需要的 API，选中后按回车键完成代码补全。

![图片说明](/img/docImage/sublime-plugin/mod-tip.png)
![图片说明](/img/docImage/sublime-plugin/mod-tip1.png)

* 如果想新增自定义的模块代码提示，可以参照[Sublime APICloud 语法提示](/APICloud/技术专题/sublime-apicloud-snippets)文档，把新建的 '`.sublime-snippet`' 文件放入插件目录（`顶部菜单 -> Preferences -> Browse Packages -> User -> 自己命名的新建文件夹中`）。

<div id="a14"></div>
##回显Android调试日志

1、首先安装 ADBView 插件

快捷键 '`Ctrl + Shift + P`' （Mac 为：'`Command + Shift + P`'）（或顶部菜单 -> Tools -> Command Palette），输入 'install'，选择 '`Package Control:Install Package`'

2、弹出的插件搜索框输入 'ADBView'，选择第一项，回车等待安装完毕，

![图片说明](/img/docImage/sublime-plugin/adbview-plugin.png)

3、在ST3菜单中 Preferences -> Package Setting -> ADBView-> Settings Users 打开ADBView的配置文件，配置"adb_args": ["logcat", "-v", "time","-s" ,"app3c"]； 配置"adb_command"中adb.exe(Mac系统为adb)所在路径。(adb.exe可在官方loader的插架包中找到，Windows系统：插件安装目录\Sublime-APICloud-Loader\tools; Mac 系统：/Users/用户名/Library/Application Support/Sublime Text 3/Packages/APICloudLoader/tools)。配置好后ADBView即可使用。
![图片说明](/img/docImage/sublime-plugin/adbview-setting.png)

4、连接移动设备，通过快捷键ctrl+alt+d即可打开当前回显日志窗口。
![图片说明](/img/docImage/sublime-plugin/adbview-log.png)


<div id="a9"></div>
##代码提示功能

确保 APICloud 代码提示插件安装成功，无需额外配置即可使用，在 JS 文件或 `<script>` 标签内部可以触发提示。

* api 对象上面的属性及方法，在输入 `api-` 时触发提示，按 '↑ ↓方向键' 选择需要的 API，选中后按回车键完成代码补全。

![图片说明](/img/docImage/sublime-plugin/api-obj.png)

* $api 对象上面的方法，在输入 `apijs-` 时触发提示，按 '↑ ↓方向键' 选择需要的 API，选中后按回车键完成代码补全。

![图片说明](/img/docImage/sublime-plugin/apijs.png)

* 模块代码提示：以 fs 模块为例，先输入 '`api-req`' 触发代码提示，require 相应的模块，然后输入'`模块名-`'时可以触发模块代码提示，按 '↑ ↓方向键' 选择需要的 API，选中后按回车键完成代码补全。

![图片说明](/img/docImage/sublime-plugin/mod-tip.png)
![图片说明](/img/docImage/sublime-plugin/mod-tip1.png)

* 如果想新增自定义的模块代码提示，可以参照[Sublime APICloud 语法提示](/APICloud/技术专题/sublime-apicloud-snippets)文档，把新建的 '`.sublime-snippet`' 文件放入插件目录（`顶部菜单 -> Preferences -> Browse Packages -> User -> 自己命名的新建文件夹中`）。


