/*
Title: geeTest
Description: geeTest
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>

<div id="method-content">

<div class="outline">

  [openGTView](#openGTView)

</div>


#概述

geeTest封装了极验验证的sdk，开发者必须配置开从*[极验验证官网](http://www.geetest.com)*申请的相应的参数即可将极验验证的验证模块集成到自己的app，安全，方便，快捷。让开发者摆脱冗长的集成流程。

**<mark>此模块必须配合极验提供的服务器部署代码，来完成二次验证。</mark>[查看服务器安装代码](http://www.geetest.com/install/)** 

####极验验证模块使用注意：

* 使用极验验证的用户，必须获取在极验验证官网申请的验证ID和KEY。*[了解更多](http://www.geetest.com/)*

* 公钥ID：可以通过key.xml文件设置，也可通过config接口配置，亦可在时随参数一起传进来,但必须选择一种方式传入ID。如果将验证ID配置在key.xml文件里，将该key.xml文件放在widget下的res文件里，apicloud服务器云编译时会将此文件加密。geeTest的模块底层代码会自动读取该文件中的公钥。

####使用此模块之前需先配置config或key文件的字段，方法如下:

##config配置方式

名称：geeTest

参数：urlScheme, id ，custom_server_validate_url

描述：配置极验验证模块信息

```js
	  <feature name="geeTest">
        <param name="urlScheme" value="gt8cace00ade6ce17838da348ac4aa7ed2"/>
        <param name="id" value="8cace00ade6ce17838da348ac4aa7ed2"/>
        <param name="custom_server_validate_url" value="http://testcenter.geetest.com/gtweb/android_sdk_demo_server_validate/"/>
    </feature>
```
字段描述:

1. urlScheme：由'gt'字段与官网上获得的极验ID合并而成

2. id: 极验ID，极验平台获取

3. custom_ server_ validate_url：二次验证的链接，由用户自己提供。示例代码中提供的是仅供测试使用的二次验证链接。用户必须根据我们提供的*[服务器部署代码](http://www.geetest.com/install/)*来配套部署服务器。

* 注意config里的二次验证链接，在示例代码中使用的是geetest专门演示用二次验证链接，用户在自己使用模块的时候请务必在自己的服务器上做相应的配置。见上面高亮标记的说明文字以及链接。

###补充说明
<mark>“custom_ server_ validate_url”：示例代码中提供的是仅供测试使用的二次验证链接。用户必须在使用极验验证端SDK之前先根据我们提供的*[服务器部署代码](http://www.geetest.com/install/)*来配套部署服务器，然后在端config里填入自己部署的“custom_ server_ validate_url”。很重要，很重要，很重要。重要的事情要说三遍。</mark>

##key.xml配置方式
```js
<?xml version="1.0" encoding="UTF-8" ?>
<security>
    <item name="gt_id" value="***Your极验验证ID***"/>
</security>
```

###可用性
iOS系统 支持版本1.0.0

## openGTView <div id="openGTView"></div>
开启极验验证的方法

openGTView({params},callback(ret,err))

###param
gt_id:

* 类型：字符串
* 默认值：无
* 描述：可以为空，但必须在三种配置方法中至少选择一个，否者会有相应的错误提示

###callback(ret,err)
ret:

* 类型:json对象

内部字段:
```
{
    status:	//验证是否通过,BOOL类型
}
```

err:

* 类型:json对象

内部字段:
```
{
    msg:""		//验证失败返回的信息,字符串类型
}
```
###示例代码
```
        var geeTest = api.require('geeTest');
        geeTest.openGTView({
                            gt_id:'8cace00ade6ce17838da348ac4aa7ed2'
                              },
                              function(ret,err){
                              if (ret.status){
                           /* Todo Your Code */
                                api.alert({
                                          title: '验证结果',
                                          msg: '验证成功',
                                          buttons: ['确定']
                                          });
                              }else{
                                api.alert({
                                          title: '验证结果',
                                          msg: err.msg,
                                          buttons: ['确定']
                                          });
                                }
                              });
    }
```
###补充说明
示例代码中验证通过后后续的用户方法在/* Todo Your Code */对应的地方写入

###可用性
iOS系统 支持版本1.0.0