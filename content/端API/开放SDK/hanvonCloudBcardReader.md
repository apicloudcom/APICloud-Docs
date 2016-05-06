/*
Title: hanvonCloudBcardReader
Description: hanvonCloudBcardReader
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：汉王云</p>

<div class="outline">
[recognitionBcard](#a1)

</div>

#**概述**

hanvonCloudBcardReader模块封装了汉王云名片识别的sdk，可通过选择相册中的名片读取名片信息。暂仅支持Android。


在集成此模块之前可先配置config文件，也可不配置config文件直接从前端js将androidkey传入模块原生代码。在config里添加如下字段：

 名称：HanvonCloudBcard

 参数：androidkey

 描述：androidkey即是从汉王云官网开发者中心 应用管理 Key管理中生成的android key

- 配置示例:

```xml
<feature name="hanvonCloudBcardReader "> <param name="androidkey" value="163114c8-31b5-4424-bb85-617f81cf54d9" /> </feature> 
```
- 字段描述:

  androidkey：申请获得的androidkey
    
<div id="a1"></div>
#**recognitionBcard**

识别名片

recognitionBcard(params,callback(ret, err))

##params

androidkey：

- 类型：字符串
- 描述：在汉王云官网申请的android key

lang：

- 类型：字符串
- 默认值：chns
- 描述：名片是语言，可为chns（中文简体）、chnt（中文繁体）、en（英文）

picpath：

- 类型：字符串
- 描述：名片的存放路径

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：
```js
{
	 status： //识别名片状态值 
	 result:  //json字符串。识别名片结果。
        {
                code：0,                        //识别返回码
		result：,                       //消息内容
		rotateAngle：null,              //消息内容
		name：[张三],                   //姓名
		title：[经理],                  //头衔
		tel：[01012345678],             //电话
		mobile：[15201111111],          //手机
		fax：[0101111111],              //传真
		email：[zhangsan@126.com],      //邮箱
		comp：[XX科技有限公司],         //公司
		dept：[销售部],                 //部门
		degree：[本科],                 //学历
		addr：[北京市海淀区],           //地址
		post：[100111],                 //邮编
		mbox：[],                       //信箱
		htel：[01022222222],            //家庭电话
		web：[],                        //网址
		im：[],                         //即时通讯号
		numOther：[QQ:123456],          //其他数字
		other：[销售经理，永争第一],    //其他文字
		extel：[],                      //分机号
         }
} 
```
err：

- 类型：JSON 对象
- 内部字段：
```js
{
  msg: //错误描述 
} 
```

##示例代码

```js
{
var recCard = api.require('hanvonCloudBcardReader');
 recCard.recognitionBcard({ 
androidkey: "163114c8-31b5-4424-bb85-617f81cf54d9", 
lang: "chns" 
picpath: "/storage/sdcard0/DCIM/Camera/IMG_20151021_143218.jpg"
},function(ret, err){ 
if(ret.status){
     api.alert({
	title: "识别结果",
	msg:ret.result
});
}else{
    api.alert({
	title: "识别结果",
	msg:err.msg
});
}
}); 
}
```

##可用性

Android系统

可提供的1.0.0及更高版本