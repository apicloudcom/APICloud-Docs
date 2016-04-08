/*
Title: CChelper移动应用远程协助平台接入
Description: CChelper移动应用远程协助平台接入
Sort: 11
*/

开发者在使用APICLoud提供的第三方开放平台-CChelper彩虹SDK小通时，需要开发者自行到CChelper彩虹SDK小通开放平台注册账号并申请相应的appKey，并按照CChelper模块开发指南进行配置。支持Android和iOS系统。

##注册管理员账号

如果你还没有注册管理员账户，请先注册账号；如果有管理员账号的，则可以直接登录。注册登录地址：[http://www.cutecomm.com/appsdk/login](____)，点击该链接可以进入到如下注册登录界面：

![图片说明](http://www.cutecomm.com:9090/images/apicloud/login.png)

如果想注册管理员，请点击页面中的立即注册，进入到注册界面：

![图片说明](http://www.cutecomm.com:9090/images/apicloud/register.png)
 
##登录管理系统平台

在登录界面，可以通过注册的邮箱或者账号登录管理系统：

![图片说明](http://www.cutecomm.com:9090/images/apicloud/manager_sys.png)
 
##创建应用（获取AppKey）

点击“创建应用”，填写需要集成彩虹SDK小通的应用的相关信息，提交之后，如果成功，系统会自动生成一个对应的AppKey；该AppKey非常重要，否则无法使用CChelper的相关功能，并且AppKey要与Android应用的包名（iOS为Bundle Id）对应：

![图片说明](http://www.cutecomm.com:9090/images/apicloud/create_app.png)

###应用包名
如果是Android应用，则对应的应用包名；iOS应用则对应的是应用的Bundle Id。请注意一定要填写正确，否则无法正常使用CChelper服务。可以通过APICloud的后台，查看应用对应Android的包名和iOS Bundle Id：

![图片说明](http://www.cutecomm.com:9090/images/apicloud/apicloud_app.png)

一般情况，Android包名和iOS包名不一致，所以需要分别在CChelper彩虹SDK小通管理系统中，分别创建应用，并使用不同的AppKey。
因此，在应用中需要通过APICloud的api.systemType
获取系统类型，如ios、android，取值范围详见系统类型常量，字符串类型

示例代码

`var systemType = api.systemType;  // 比如: ios`

根据不同的系统，传递不同的AppKey，可以解决该问题。

###应用状态
应用状态分为启用和禁用两种状态，默认是启动状态。

###服务客服
可以选择，该应用对应的服务客服，如果没有客服，需要进入到管理后台的客服信息模块，申请免费客服（正常可以申请一个免费客服），也可以联系我们开通更多的客服；系统自动生成客服后，为了安全需要用户修改客服信息；具体可以客服章节。

###AppKey
创建应用，提交成功后，系统会自动生成一个AppKey：

![图片说明](http://www.cutecomm.com:9090/images/apicloud/appkey.png)

##客服信息
进行彩虹SDK小通版本的后台管理系统的客服信息模块，首次注册的用户，都可以申请免费客服，如需添加更多客服，请咨询我们：

![图片说明](http://www.cutecomm.com:9090/images/apicloud/free_kefu.png)

申请免费客服，自动生成如下账号：

![图片说明](http://www.cutecomm.com:9090/images/apicloud/free_kefu_init.png)

注意：客服的初始化信息都是由系统自动生成，建议用户为了安全对初始化客服信息进行及时修改。

##分配客服
可以通过两种方式来分配客服：

- 当创建应用的时候，可以选择服务客服
- 编辑客服信息时，可以对其服务的应用进行编辑
![图片说明](http://www.cutecomm.com:9090/images/apicloud/select_app.png)

##Windows 客服端

支持Win7、Win8以上的Windows版本，包括32位和64位系统。

注意：需要安装.Net Framework 4.0及以上的版本。

可以访问领通科技官网的彩虹SDK小通下载中心，下载客服端应用，访问地址：[http://www.cutecomm.com/Home/Index/download_xiaotong.html](____)
 
##登陆客服端

启动客服端，使用客服账号和密码进行登录。

 
##cchelperModule模块添加到APICloud应用

根据cchelperModule模块集成接口文档中的流程将此模块集成APICloud应用中。

![图片说明](http://www.cutecomm.com:9090/images/apicloud/109.png)

##启动CChelper服务
在应用中调用cchelperModule模块的启动接口，就可以启动CChelper服务了。