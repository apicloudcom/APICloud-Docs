/*
Title: APICloud Studio
Description: APICloud Studio
Sort: 4
*/

**1.APICloud Studio有哪些功能，开发过程中可以进行js调试、查看运行log输出、真机同步以及本地打包吗？**<div id="5"></div>

APICloud Studio中包含：打开向导页面、创建移动应用、同步本地应用到云端资源库、从云端资源库下载应用到本地、使用云端svn同步功能、真机同步测试、运行PC模拟器、本地打包、云端编译、输出手机调试日志、在线文档、APICloud代码提示以及自动补全等功能

查看运行log：

- 首先通过一键真机同步测试功能将要调试的应用同步到android手机中的
- 开启APICloud Studio的日志输出功能按钮 

![图片说明](/img/docImage/167.png)

- APICloud Studio控制台会提示出开启监听…

![图片说明](/img/docImage/168.png)
 
如果开发人员自己输入了日志，或者js报错就会出现在APICloud Studio控制台中。（如何定义输出日志请参考文档）


真机同步

真机同步测试有2个入口：

- 首先在我的APP项目视图中选择一个需要真机测试的应用，然后在应用上右键选择一件真机同步测试。
- 在APICloud Studio 中找到按钮 ，点击后在弹出的窗口中选择需要真机测试的应用。运行即可。

![图片说明](/img/docImage/169.png)

- 启动同步app向导，当应用同步到手机后点击完成关闭向导。

![图片说明](/img/docImage/170.png)

- 在手机中测试应用。

本地打包

本地打包有2个入口：

- 在我的APP项目视图中选择一个需要打包的应用，然后在应用上右键选择生成快速安装包。

![图片说明](/img/docImage/171.png)
 
或者在APICloud Studio 中找到按钮 ，点击后在弹出的窗口中选择需要打包的应用。点击运行。

- 在弹出的窗口中选择需要生成测试包的类型(ios/android)，然后点击完成即可生成对应的快速安装包。

![图片说明](/img/docImage/172.png)
 
生成测试安装包后，APICloud Studio会自动帮您打开生成安装包对应的路径的文件夹。

**2.我已经下载了安卓手机助手或者ITunes,但还是提示需要下载手机助手**

- 安卓设备请先关闭ide关闭安卓手机助手.然后重启ide.
- 苹果设备需确认是否可以正常连接ITunes.然后在重新连接ide.

**3.我在真机同步过程中,ide无响应了**

遇到这种情况建议耐心等待一会儿,如果不行请关闭ide.重新尝试.

**4.我的安卓手机真机同步后,运行apploader后没有应用,界面一片空白**

- 如果安卓手机没有提供sd卡可能会出现上述,情况.请安装sd卡后重试.
- 某些手机可能存在权限问题,导入无法同步应用.

**5.我的iphone手机在真机同步时提示,无法连接服务等问题不能真机同步**

遇到上述情况建议手动安装我们提供的apploader.ipa然后重新尝试.

Apploader.ipa存放路径为“apicloud-studio\dropins\com.uzmap.ide.tools.ios_1.0.7\base”

A apploader.apk存放路径为“apicloud-studio\dropins\com.uzmap.ide.tools.android_1.0.7\base”

(注：路径中版本号会随当前apploader的版本变化)

IOS版Apploader为企业级应用，无需越狱即可通过第三方工具安装，如[itools](http://www.itools.cn/)等

除了上述问题,如果还有其他问题或不明白的问题,请联系我们的客服人员,或者加qq群（1群: 384318203    2群: 375521215)讨论.谢谢支持!

**6、为什么本地打包的安装包比云编译的包大很多啊？为什么本地一个hellp world安装包都10M了 ，云编译出来才0.7M?**

答：本地打包包含所有模块，而云编译只包含使用的模块


**7.请问 APICloud的开发环境，支持linux系统么？**

答：linux，mac暂时不支持，以后版本会支持。

**8.APICloud Studio，在mac下能用吗？**

答：暂时没有MAC版本的APICloud Studio，现在只能通过虚拟机的方式在MAC使用APICloud Studio。

**9.ide生成的快速测试包怎么在ios上不能安装？**
      
答：ide生成的快速测试包，只能安装在越狱设备上。

**10.Svn同步widget失败**

答：如果是ide创建的应用，先在ide中同步代码，然后在云端打包。

