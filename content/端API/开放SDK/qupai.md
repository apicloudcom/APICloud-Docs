/*
Title: qupai
Description: qupai
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：开发者</p>

* [initQuPai](#1)

* [startQuPai](#2)

* [返回码](#3)

##**概述**

趣拍是杭州短趣和阿里巴巴联合提供的短视频拍摄SDK，为广大移动应用开发者提供免费、简单、快捷、稳定的接口，帮助开发者快速实现自有APP上的短视频应用开发。

其中包含短视频拍摄、水印、拍摄码率等的自定义设置，并自带美颜功能。

>使用须知

>>1. 使用前需要去阿里百川配置AlibabaSDK基础包和图片服务插件，[传送门](http://baichuan.taobao.com), 具体流程请参考[接入指南](https://github.com/bringmehome/Qupai)

>>2. 如果只是测试，可以直接在[GITHUB](https://github.com/bringmehome/Qupai)里下载自定义模块包，添加到自己的自定义模块中，不要生成android的证书！不要生成android的证书！不要生成android的证书！打包的时候使用测试版即可

>>3. 如果你已经生成了安卓证书，请从[阿里百川的顽兔平台](http://wantu.taobao.com/space/index.htm)获取到SDK(android_baichuan_media_sdk.zip), 操作方法,[传送门](http://baichuan.taobao.com/doc2/detail.htm?articleId=102765&docType=1&treeId=38)

>>4. 获取到SDK后解压得到文件"android_baichuan_media_sdk.zip\OneSDK\res\drawable\yw_1222.jpg"，并在[GITHUB](https://github.com/bringmehome/Qupai)里下载自定义模块包，替换"myqupai\res_myqupai\res\drawable"文件夹下的yw_1222.jpg文件，更新你的自定义模块

>>5. 使用中遇到任何问题，请联系作者邮箱（sin@feeling.life）,作者会在第一时间回复。

#**initQuPai**<div id="1"></div>

初始化趣拍

initQuPai(function(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    code : 0              //数字类型；返回码
    message:"success"     //字符串类型；正确返回
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
    code : 702            //数字类型；错误码
    message:              //字符串类型；错误描述
}
```

##示例代码

```js
var qupai = api.require('qupai');
qupai.initQuPai(function(ret, err){
    if(ret) {
        alert(JSON.stringify(ret));
    } else {
        alert("err = "+JSON.stringify(err));
    }
});
```

##可用性

Android系统

可提供的1.0.0及更高版本


#**startQuPai**<div id="2"></div>

打开拍摄视频的页面

startQuPai({params},function(ret, err)

##params

maxRecordTime：

- 类型：number
- 描述：最长拍摄时间，单位为秒

videoBitrate：

- 类型：number
- 描述：视频的码率，(1024 * 1000)的整数倍，如 2000 * 1024

waterMarkPath：

- 类型：字符串
- 描述：水印图片的路径，如 "assets://widget/image/logo.png"

waterMarkPostion：

- 类型：number
- 描述：水印的坐标，1 右上角， 2 右下角

##callback(ret, err)

ret：

- 类型：JSON 对象
- 描述：返回的文件路径，如视频文件名为sin_2016-02-17-12-03-42-142.mp4, 图片文件名为sin_2016-02-17-12-03-42-142.jpg
- 内部字段：

```js
{
    code : 0                    //字符串类型；返回码
    message:"file:/storage/emulated/0/Sins/sin_2016-02-17-12-03-42-142"    //字符串类型；文件路径
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
    code : 9002                //字符串类型；返回码
    message:"Canceled."        //字符串类型；错误描述
}
```

##示例代码

```js
var qupai = api.require('qupai'); 
var param = {
    maxRecordTime:6,
    videoBitrate:1024*1000,
    waterMarkPath:"assets://Qupai/watermark/logo.png",
    waterMarkPostion:1,
}; 
qupai.startQuPai(param,function(ret, err){
    if(ret)
        alert(JSON.stringify(ret));
    else
        alert("err = "+JSON.stringify(err));
});
```


##可用性

Android系统

可提供的1.0.0及更高版本


#**返回码**<div id="3"></div>

**返回码释义**

- 0 ：正确返回

- 1 ：请求参数错误

- 2 ：初始化失败

- 702： 没有找到图片文件，请确保图片文件 yw_1222.jpg 在 res\drawable 目录下

- 9001：链接服务器失败

- 9002：取消

- 9003：文件复制识别