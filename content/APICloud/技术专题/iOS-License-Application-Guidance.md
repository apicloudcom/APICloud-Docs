/*
Title: iOS证书及描述文件制作流程
Description: iOS证书申请教程
Sort: 12
*/

[说明](#0)

[创建App ID](#1)

[添加测试设备](#2)

[云编译p12证书制作](#3)

[云编译mobileprovision证书制作](#4)	

[云编译Apple Watch对应mobileprovision证书制作](#5)

[推送p12证书制作](#6)

 
#**说明**<div id="0"></div>

请确保您已经申请了苹果开发者账号（个人、公司账号99美元，企业账号299美元），否则无法进行以下操作。若未申请，可以去苹果开发网站进行申请，入口如下图：

![图片说明](/img/docImage/certificateRequest/3.png)

使用APICloud平台开发iOS应用需要用到几个证书，下面的图为各个证书使用的地方。接下来为各个证书的创建教程。

![图片说明](/img/docImage/certificateRequest/1.png)

![图片说明](/img/docImage/certificateRequest/2.png)
 
#**创建App ID**<div id="1"></div>

首先打开苹果开发网站，通过Member Center进入开发账户，如图：

![图片说明](/img/docImage/certificateRequest/231.png)
 
然后选择Certificates, Identifiers & Profiles，再点击Identifiers进入，如图：

![图片说明](/img/docImage/certificateRequest/232.png)

如图，在左侧菜单选择App IDs，然后点击右上角的添加图标，在接下来的页面里面填写App ID描述，在App ID Suffix栏选择Explicit App ID，这里填写的ID即是控制台上传证书页面需要填写的APP IDs，在App Services中选择服务功能，勾选上Push Notifications项，点击Continue进入下一步。
 
![图片说明](/img/docImage/certificateRequest/240.png)

![图片说明](/img/docImage/certificateRequest/241.png)

![图片说明](/img/docImage/certificateRequest/242.png)
 
在新页面中点击Submit，然后点击Done，创建App ID成功。


#**添加测试设备**<div id="2"></div>

个人或公司账号生成的App Store类型mobileprovision证书，应用在没有发布到App Store之前只能在越狱设备上安装，若要在非越狱手机上面安装，则需要把设备添加到Devices里，并且生成Ad Hoc类型mobileprovision证书。
 
首先获取UDID，打开iTunes，连接设备，如图，找到序列号，然后点击序列号，该栏会变成UDID，点击鼠标右键，拷贝UDID。

![图片说明](/img/docImage/certificateRequest/244.png)

![图片说明](/img/docImage/certificateRequest/245.png)

回到网站页面，如图选择左侧菜单Devices下面的All，在右侧页面点击右上角添加图标，进入下图所示页面：

![图片说明](/img/docImage/certificateRequest/243.png)
 
输入Name和获取的UDID，点击Continue进入下一页，下一页中点击Register，最后点击Done，添加设备完成。

#**云编译p12证书制作**<div id="3"></div>

##生成certSigningRequest文件

如图，打开应用程序->实用工具->钥匙串访问

![图片说明](/img/docImage/certificateRequest/227.png)
 
如图，选择从证书颁发机构请求证书

![图片说明](/img/docImage/certificateRequest/228.png)

接下来填写邮件地址，选择存储到磁盘，点击继续

![图片说明](/img/docImage/certificateRequest/229.png)
 
如图，保存文件到桌面。

![图片说明](/img/docImage/certificateRequest/230.png)

##制作p12证书
 
如图所示，点击左边的Production，在右边出来的页面的右上角选择添加

![图片说明](/img/docImage/certificateRequest/234.png)
 
如图，如果是个人或公司账号，选择App Store and Ad Hoc，如果是企业账号，则选择In-House and Ad Hoc，点击Continue进入下一步，在下一页中点击Continue。

![图片说明](/img/docImage/certificateRequest/235.png)
 
如图，选择Choose File选择之前生成的certSigningRequest文件，点击Generate

![图片说明](/img/docImage/certificateRequest/236.png)
 
如图所示，cer证书创建成功，点击Download将证书下载到本地，然后双击打开证书

![图片说明](/img/docImage/certificateRequest/237.png)
 
在钥匙串中找到安装的证书，若提示此证书是由未知颁发机构签名的，请下载Apple Worldwide Developer Relations Certification Authority证书进行安装，地址[http://developer.apple.com/certificationauthority/AppleWWDRCA.cer](http://developer.apple.com/certificationauthority/AppleWWDRCA.cer)，在左边选择“登录”和“我的证书”，找到证书，在证书上面点击鼠标右键，然后在菜单中选择导出证书，如图：

![图片说明](/img/docImage/certificateRequest/238.png)
 
在弹出页面中指定证书名，点击存储，然后输入证书密码（此密码在控制台上传证书页面输入），点击好，生成p12格式证书。

![图片说明](/img/docImage/certificateRequest/239.png)

#**云编译mobileprovision证书制作**<div id="4"></div>

##App Store类型证书

App Store证书只能用于发布应用到AppStore，不能安装在非越狱设备上面。如图，点击左侧菜单Distribution，然后点击右侧页面右上角的添加图标，最后选择App Store，点击Continue进入下一步

![图片说明](/img/docImage/certificateRequest/246.png)
 
如图，选择上面创建的App ID，点击Continue进入下一步

![图片说明](/img/docImage/certificateRequest/247.png)
 
如图，选择certificates，点击Continue进入下一步

![图片说明](/img/docImage/certificateRequest/248.png)
 
输入证书名称，点击Generate，进入下一步完成创建

![图片说明](/img/docImage/certificateRequest/249.png)
 
##Ad Hoc类型证书

对于个人和公司账号，Ad Hoc类型证书可以安装到指定的测试设备上面调试，进行这一步之前请先按照上面教程添加测试设备。如图，选择Ad Hoc，点击Continue进入下一步

![图片说明](/img/docImage/certificateRequest/250.png)
 
如图，选择App ID，点击Continue进入下一步

![图片说明](/img/docImage/certificateRequest/251.png)
 
如图，选择certificates，点击Continue进入下一步

![图片说明](/img/docImage/certificateRequest/252.png)
 
选择设备，然后点击Continue

![图片说明](/img/docImage/certificateRequest/253.png)
 
输入证书名称，点击Generate，进入下一步完成创建

![图片说明](/img/docImage/certificateRequest/254.png)
 
#**云编译Apple Watch对应mobileprovision证书制作**<div id="5"></div>

云编译时若要支持Apple Watch，那么需要另外再上传一个mobileprovision证书，该证书对应的App ID由你的应用的App ID加后缀watchkitapp构成，例如应用的App ID为com.yourcompany.app，那么Apple Watch证书对应的App ID则为com.yourcompany.app.watchkitapp。创建好App ID后再按照上面的mobileprovision证书制作流程制作Apple Watch对应证书。
 
#**推送p12证书制作**<div id="6"></div>

在左侧菜单选择Certificates下面的Production，进入到如下界面：

![图片说明](/img/docImage/certificateRequest/255.png)
 
点击右上角的添加图标，进入以下页面，选择如图所示内容，点击Continue进入下一步

![图片说明](/img/docImage/certificateRequest/256.png)
 
在App ID栏选择对应的App ID，点击Continue，在下一页中点击Continue

![图片说明](/img/docImage/certificateRequest/257.png)
 
选择之前生成的certSigningRequest文件，然后点击Generate进入下载界面

![图片说明](/img/docImage/certificateRequest/258.png)
 
点击Download下载证书到本地，双击安装到钥匙串中。如下图，在钥匙串中找到此证书，在该证书上面点击鼠标右键，选择导出，然后存储为.p12格式文件，输入证书密码。至此，创建服务端p12格式推送证书完毕。

![图片说明](/img/docImage/certificateRequest/259.png)