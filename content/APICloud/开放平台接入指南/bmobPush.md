/*
Title: Bmob平台接入
Description: Bmob平台接入
Sort: 11
*/

**[Bmob平台](http://www.bmob.cn/)** 为您的移动应用提供了一个完整的后端解决方案，开发者在使用 APICloud 提供的Bmob推送模块时，需要开发者自行到个推开放平台申请相应的AppID，并按照模块开发指南进行配置。

## 接入步骤 ##


###注册Bmob帐号###

首先请登录[Bmob首页：http://www.bmob.cn/](http://www.bmob.cn/)，或者在百度输入Bmob进行搜索

打开Bmob官网后，点击右上角的[“注册”](http://www.bmob.cn/site/register)，在跳转页面填入你的姓名、邮箱、设置密码，确认后到你的邮箱激活Bmob账户，你就可以用Bmob轻松开发应用了。


![注册界面](http://docs.bmob.cn/android/faststart/image/rumen_zhuce.png)

###网站后台创建应用###

登录账号进入bmob后台后，点击后台界面左上角“创建应用”，在弹出框输入你应用的名称，然后确认，你就拥有了一个等待开发的应用。

![创建应用](http://docs.bmob.cn/android/faststart/image/rumen_chuangjian.png)


###获取Appid###

选择你要开发的应用，点击该应用下方对应的“应用密钥”

![应用密钥](http://docs.bmob.cn/android/faststart/image/rumen_miyue_1.png)

在跳转页面，获取Application ID，此ID会在初始化BmobPush模块中使用到。

![AppId就在这里啦](http://docs.bmob.cn/android/faststart/image/rumen_miyue_2.png)

###**设置包名信息（**Android**)**###

注意：推送服务要设置包名才能使用

ApiCloud生成的Apk文件的包名在
[ApiCloud控制台](http://www.apicloud.com/console)-->左上角的[“概览”](http://www.apicloud.com/appoverview)-->查看包名

![获取包名信息](http://file.bmob.cn/M00/53/26/oYYBAFT5ajaABMpMAABOvkz3Rf4130.png)

![获取包名信息](http://file.bmob.cn/M00/53/28/oYYBAFT5amOALksQAAB2iQL_mGI521.png)

然后。。。

****填写到Bmob后台****

- 应用面板
- 消息推送
- 推送设置
- 填写包名
- 保存

![设置包名信息](http://docs.bmob.cn/android/developdoc/image/setting.jpg)



##测试推送消息##

- 应用面板
- 消息推送
- 编辑消息
- 推送内容
- 发送


![测试推送消息](http://docs.bmob.cn/android/developdoc/image/pushmsg.jpg)

##注意事项及其他##

在后台推送消息给Android和iOS两个平台的时候，有一些需要注意的：

- 由于Android和iOS的提送机制不同，iOS要经过APNS，Android的推送完全是走Bmob的长连接服务，为兼容这个问题，如果你选择发送格式为“json”格式时，需要添加APNS兼容头部（见下面json的aps部分），推送内容格式如下：

{
    "aps": {
    "sound": "cheering.caf", 
    "alert": "这个是通知栏上显示的内容", 
    "badge": 0 
    }, 
    "xx" : "json的key-value对，你可以根据情况添加更多的，客户端进行解析获取", 
}

其中，sound是iOS接收时的声音，badge是iOS通知栏的累计消息数。

- 如果你选择发送格式为“text”时，推送内容为“推送消息测试。。。。”，Bmob会自动添加aps部分发送给APNS，，相当于自动生成如下的json格式的推送内容：

{
    "aps": {
        "alert": "推送消息测试。。。。", 
    }
}

同时，也会发送给Android端，相当于自动生成如下的json格式的推送内容：

{
    "alert" : "推送消息测试。。。。", 
}

- 如果只是发送给Android端，大家可以自定义json格式的数据。
- 由于iOS的APNS的推送的大小是有限制的，默认最多256bytes，因此,如果你需要跨平台互通的话，需注意推送的内容不要太长。
- 想要更多了解Bmob的推送格式的朋友，如即时聊天，可以查看我们在[问答社区](http://wenda.codenow.cn//?/question/204)中的回答