/*
Title: ksi
Description: ksi
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：爱立示</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>

<div id="method-content">

<div class="outline">

[sign](#sign)

[verify](#verify)

</div>

## 概述

请到爱立示官网“关于我们”页面，扫描“无钥签名免费试用申请渠道”二维码获取一对一个性化技术支持服务并开通能力使用账户

爱立示无钥签名 是电子数据的电子标签（签名），以纯数学算法检验及证明电子数据的签名时间、起源和数据完整性，证明数据的可靠性和不可抵赖性。爱立示所创立的无钥签名 技术已经在多个地区被成功应用于电子政务、通讯、金融、云计算、物联网、版权保护等领域。
任何电子数据都可通过本地计算提取电子指纹，电子指纹经过分布式网络基础设施运算获得无钥签名 。无钥签名 技术使得对数据完整性的验证和证明仅仅依赖于数学运算，不再需要基于对人或机构的信任。无钥签名 可以由任何人独立验证，且验证永不失效，同时对量子破解免疫。 
爱立示致力于帮助社会建立公共诚信机制，让信任更简单！

本模块由是ksisdk的优化版，由原来的四个接口优化为现在的两个接口，建议使用本模块。


## sign <div id="sign"></div>

为电子数据提供签名服务，保证其原始性、真实性和完整性。可直接对文本、图片、视频、音频等各种类型的数据进行签名，对于保密性数据可直接提供其hash值（SHA256）进行签名。

sign({params}, callback(ret, err))


###params###

type：

<ul>
<li>类型：整型</li>
<li>默认值：0</li>
<li>描述：待签名的数据类型（0-文本，1-hash值，2-文件），不可为空</li></ul>


content：

<ul>
<li>类型：字符串</li>
<li>默认值：无</li>
<li>描述：待签名内容，不可为空，根据type参数的值来定义。当签名数据为文本时，content表示待签名文本内容；当签名数据为文件时，content表示待签名文件完整路径；当签名数据为hash值时，content表示待签名hash。</li></ul>

user：

<ul>
<li>类型：字符串</li>
<li>默认值：无</li>
<li>描述：用户名，签名需要身份认证时的必需参数</li></ul>

pwd：

<ul>
<li>类型：字符串</li>
<li>默认值：无</li>
<li>描述：密码，签名需要身份认证时的必需参数</li></ul>

###callback(ret, err)###

ret：
<ul>
<li>类型：JSON 对象</li></ul>

内部字段：
<pre>
{
    res_code:"0",//请求成功时的响应码，签名成功时为0
    res_message:"Signature created and stored",//请求成功时的响应信息
}
</pre>
err：
<ul>
<li>类型：JSON 对象</li></ul>
内部字段： 
<pre>
{
    msg: 签名异常，请稍后重试！//请求错误时的返回信息
}
</pre>

###示例代码:###

<pre>
    ksi = api.require('ksi');
    var params = {type:0,content:"测试文本" ,user:"user",pwd:"pwd"};    
    ksi.sign(params,function(ret, err){
       alert(JSON.stringify(ret) + JSON.stringify(err));
    } );

</pre>

###可用性###

 iOS系统  Android系统

##验证接口##

## verify <div id="verify"></div>

为电子数据提供验证服务，数据必须经过KSI提供的签名服务进行签名之后才可以验证通过。可验证的数据类型与签名数据类型一致。

verify({params}, callback(ret, err))

###params###

type：

<ul>
<li>类型：整型</li>
<li>默认值：0</li>
<li>描述：待签名的数据类型（0-文本，1-hash值，2-文件），不可为空</li></ul>


content：

<ul>
<li>类型：字符串</li>
<li>默认值：无</li>
<li>描述：待验证内容，不可为空，根据type参数的值来定义。

当验证数据为文本时，content表示待验证文本内容；当验证数据为文件时，content表示待验证文件完整路径；当验证数据为hash值时，content表示待验证hash。
</li></ul>

###callback(ret, err)###

ret：
<ul>
<li>类型：JSON 对象</li></ul>
内部字段： 
<pre>
{
    res_code:"0",//请求成功时的响应码，验证成功时为0
    res_message:"OK",//请求成功时的响应信息
    registered_time:"Sat Feb 28 2015 17:04:55 GMT+0800 (CST)",//签名时间,验证成功时返回
    hash_value:"e3:b0:c4:42:98:fc:1c:14:9a:fb:f4:c8:99:6f:b9:24:27:ae:41:e4:64:9b:93:4c:a4:95:99:1b:78:52:b8:55",//验证hash值，验证成功时返回
    hash_algorithm:"SHA256",//hash算法，验证成功时返回
}
</pre>
err：
<ul>
<li>类型：JSON 对象</li></ul>

内部字段： 
<pre>
{
    msg: 验证出现异常，请稍后重试！//请求错误时的返回信息
}
</pre>

###示例代码###

<pre>

ksi = api.require('ksi');
var params = {type:1,
content:"e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855"};
ksi.verify(params,function(ret,err){
      alert(JSON.stringify(ret) + JSON.stringify(err));
} );

</pre>

###可用性###

iOS系统 Android系统

</div>