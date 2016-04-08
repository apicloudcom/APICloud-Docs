/*
Title: geeTest
Description: geeTest
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>

<div id="method-content">

<div class="outline">

  [openGTView](#openGTView)

</div>

#概述
geeTest封装了极验验证的sdk，开发者必须配置开从*[极验验证官网](http://www.geetest.com)*申请的相应的参数即可将极验验证的验证模块集成到自己的app，安全，方便，快捷。让开发者摆脱冗长的集成流程。

**<mark>此模块必须配合极验提供的服务器部署代码，来完成二次验证。</mark>[查看服务器安装代码](http://www.geetest.com/install/)** 

####极验验证模块使用注意：
* 使用极验验证的用户，必须获取在极验验证官网申请的验证ID和KEY。*[了解更多](http://www.geetest.com/install/sections/idx-basic-introduction.html)*
* 可使用api_1和api_2作为验证启动参数，优先使用本组参数
* 亦可使用gt、challenge和success作为验证启动参数(该方案要求对极验的通讯流程了解清楚)

##openGTView <div id="openGTView"></div>
配置验证，并且开启验证

openGTView({params},callback(ret,err))

###param
api_1:

* 类型：字符串
* 默认值：无
* 描述：不可为空，由网站主集成极验的服务器sdk时提供的给网站主客户端的接口。该接口用于客户端向网站主服务端获取极验验证所需的验证信息。示例代码中提供的是仅供测试使用的链接，请不要在发布的项目里使用。用户必须根据我们提供的*[服务器部署代码](http://www.geetest.com/install/)*来部署服务器。

api_2:

* 类型：字符串
* 默认值：无
* 描述：不可为空，由网站主集成极验的服务器sdk时提供的给网站主客户端的接口。该接口为二次验证的链接，用于校验服务端获得的验证结果。示例代码中提供的是仅供测试使用的二次验证链接，请不要在发布的项目里使用。用户必须根据我们提供的*[服务器部署代码](http://www.geetest.com/install/)*来部署服务器。

blurType:

* 类型：字符串
* 默认值：不使用模糊背景
* 描述：可以为空，用于配置验证背景的效果。只在iOS8.0以上生效。

https:
* 类型：字符串('true'/'false')
* 默认值：false
* 描述：配置验证是否使用https协议(默认不适用)

gt:

* 类型：字符串
* 默认值：无
* 描述：如果不用api_1和api_2两个参数配置验证，则此参数就必须要配置。用于验证的ID参数。

challenge:

* 类型：字符串
* 默认值：无
* 描述：如果不用api_1和api_2两个参数配置验证，则此参数就必须要配置。用于验证的Challenge参数。

success:

* 类型：字符串('true'/'false')
* 默认值：'true'
* 描述：如果不用api_1和api_2两个参数配置验证，则此参数就必须要配置。用于验证的Success参数。

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
####err: msg: 错误消息列举
'-100':

调用openGTView时传入的参数错误

'-200':

极验验证服务异常，暂不可用

'-300':

用户主动关闭了验证

'-400':

二次验证结果为失败

其它:

验证内部异常

###示例代码
```
        var geeTest = api.require('geeTest');
        geeTest.openGTView({
                           api_1 : 'http://webapi.geetest.com/apis/start-mobile-captcha/',
                           api_2 : 'http://webapi.geetest.com/apis/mobile-server-validate/',
                        blurType : 'dark',
                           https : 'false'
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
                           
                           if (err.msg == '-100') {
                           api.alert({
                                     title: '验证信息错误',
                                     msg: 'Invalid config params. Check Your Server/Client Config.',
                                     buttons: ['确定']
                                     });
                           }else if (err.msg == '-200'){
                           api.alert({
                                     title: '验证不可用',
                                     msg: '极验服务不可用, 请使用备用验证',
                                     buttons: ['确定']
                                     });
                           }else if (err.msg == '-300'){
                           api.alert({
                                     title: '验证关闭',
                                     msg: '用户关闭了验证',
                                     buttons: ['确定']
                                     });
                           }else if (err.msg == '-400'){
                           api.alert({
                                     title: '验证结果',
                                     msg: '二次验证失败',
                                     buttons: ['确定']
                                     });
                           }else{
                           api.alert({
                                     title: '验证异常',
                                     msg: err.msg,
                                     buttons: ['确定']
                                     });
                           }
                                }
                            });

```
###补充说明
验证通过后要执行的方法在'/* Todo Your Code */'地方写入

###可用性
iOS系统 支持版本2.0.0