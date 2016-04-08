/*
Title: 个推接入指南
Description: 个推接入指南
*/

# 个推开放API配置指南

开发者在使用 APICloud 提供的第三方开放平台-个推（pushGeTui）时，需要开发者自行到个推开放平台申请相应的AppID，并按照个推模块开发指南进行配置。

## 申请步骤

 - 访问个推开放平台，访问地址：[http://dev.getui.com/][1]


![enter description here][2]

 - 点击“我要注册”，填写相应的用户信息进行注册


![enter description here][3]

 - 登记推送应用


 ![enter description here][4]

 - 填写应用名称，填写Android应用包名。注意：APICloud应用包名命名为：com.apicloud.，为APICloud平台创建的应用ID。包名例如：com.apicloud.A6964151488804；上传iOS推送证书和填写密码。


 ![enter description here][5]

 - 查看新注册应用的应用配置


 ![enter description here][6]

 - 获取APPKEY/APPID/APPSECRET参数


 ![enter description here][7]

 - 根据pushGeTui模块集成接口文档中的流程将pushGeTui模块添加到APICloud应用中。


![enter description here][8]

 - 启动APICloud应用，初始化个推模块，推送通知测试


 ![enter description here][9]

 - 启动APICloud应用，初始化个推模块，推送透传消息测试


 ![enter description here][10]


  [1]: http://dev.getui.com/
  [2]: /img/docImage/apicloud_getui_1.png "apicloud_getui_1.png"
  [3]: /img/docImage/apicloud_getui_2.png "apicloud_getui_2.png"
  [4]: /img/docImage/apicloud_getui_3.png "apicloud_getui_3.png"
  [5]: /img/docImage/apicloud_getui_4.png "apicloud_getui_4.png"
  [6]: /img/docImage/apicloud_getui_5.png "apicloud_getui_5.png"
  [7]: /img/docImage/apicloud_getui_6.png "apicloud_getui_6.png"
  [8]: /img/docImage/apicloud_getui_7.png "apicloud_getui_7.png"
  [9]: /img/docImage/apicloud_getui_8.png "apicloud_getui_8.png"
  [10]: /img/docImage/apicloud_getui_9.png "apicloud_getui_9.png"