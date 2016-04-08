/*
Title: 短信验证接口
Description: 短信验证
Sort: 6
*/
##API

<table>
    <tr>
        <th>URL</th>
        <th>HTTP</th>
        <th>功能</th>
    </tr>
    <tr>
        <td>/mcm/api/user/sendvercode</td>
        <td>POST</td>
        <td>发送短信验证码</td>
    </tr>
    <tr>
        <td>/mcm/api/user/checkvercode</td>
        <td>POST</td>
        <td>校验短信验证码</td>
    </tr>
    <tr>
        <td>/mcm/api/user/resetByMobile</td>
        <td>POST</td>
        <td>利用短信验证码重置密码</td>
	</tr>
    <tr>
        <td>/mcm/api/captcha/<ObjectId></td>
        <td>POST</td>
        <td>刷新图片验证码</td>
	</tr>
    <tr>
        <td>/mcm/api/captcha</td>
        <td>POST</td>
        <td>创建图片验证码</td>
	</tr>
</table>

###发送短信验证码

访问URL

```
https://d.apicloud.com/mcm/api/user/sendvercode
```

参数

|字段|必填|描述|
|----|----|----|
|mobile|是|手机号|
|imageCode|否|图片验证码|
|token|否|图片的token|

示例

```js
$.ajax({
	"url": "https://d.apicloud.com/mcm/api/user/sendvercode",
	"method": "POST",
	"cache": false,
	"headers": {
		"X-APICloud-AppId": "{{your_app_id}}",
        "X-APICloud-AppKey": "{{加密后的key}}"
	},
	"data": {"mobile":{{手机号}}}
}).success(function (data, status, header) {
	//success body
}).fail(function (header, status, errorThrown) {
	//fail body
})
```

###校验短信验证码

访问URL

```
https://d.apicloud.com/mcm/api/user/checkvercode
```

参数

|字段|必填|描述|
|----|----|----|
|mobile|是|手机号|
|vercode|是|短信验证码|

**示例**

```js
$.ajax({
	"url": "https://d.apicloud.com/mcm/api/user/checkvercode",
	"method": "POST",
	"cache": false,
	"headers": {
		"X-APICloud-AppId": "{{your_app_id}}",
        "X-APICloud-AppKey": "{{加密后的key}}"
	},
	"data": {"mobile":{{手机号}},"vercode":"{{短信验证码}}"}
}).success(function (data, status, header) {
	//success body
}).fail(function (header, status, errorThrown) {
	//fail body
})
```

**提示**：
如果注册的时候，验证手机号作为第一步或者脱离user表来使用短信验证服务，需要调用该接口来校验
###利用短信验证码重置密码

访问URL

```
https://d.apicloud.com/mcm/api/user/resetByMobile
```

参数

|字段|必填|描述|
|----|----|----|
|mobile|是|手机号|
|vercode|是|短信验证码|
|username|是|用户名|
|password|是|密码|

**示例**

```js
$.ajax({
	"url": "https://d.apicloud.com/mcm/api/user/resetByMobile",
	"method": "POST",
	"cache": false,
	"headers": {
		"X-APICloud-AppId": "{{your_app_id}}",
        "X-APICloud-AppKey": "{{加密后的key}}"
	},
	"data": {
		"mobile":{{手机号}},
		"vercode":"{{短信验证码}}",
		"username":{{用户名}}，
		"password":{{密码}}
	}
}).success(function (data, status, header) {
	//success body
}).fail(function (header, status, errorThrown) {
	//fail body
})
```

为了防止出现一些恶意性质的刷短信验证码现象，增加了发送短信验证码部分的，图片验证码验证功能，需要在云设置里边开启
###刷新图片验证码

访问URL

```
https://d.apicloud.com/mcm/api/captcha/{{token}}
```
提示：之前返回的id即为token

**示例**

```js
$.ajax({
	"url": "https://d.apicloud.com/mcm/api/captcha/{{token}}",
	"method": "POST",
	"cache": false,
	"headers": {
		"X-APICloud-AppId": "{{your_app_id}}",
        "X-APICloud-AppKey": "{{加密后的key}}"
	},
	"data": {
		"_method":"PUT"
	}
}).success(function (data, status, header) {
	//success body
}).fail(function (header, status, errorThrown) {
	//fail body
})
```
**返回值**
```js
{
    "id": "5436442ca1a14d1c60de3e06",
    "imgbase64": "{{图片转换成base64后的字符串}}",
    "createdAt": "2014-10-09T08:15:40.843Z",
    "updatedAt": "2014-10-09T08:34:28.153Z"
}
```
如下可以展示出图片
```
<img src='data:image/jpeg;base64,"+data.imgbase64 +"' />
```
###创建图片验证码


访问URL

```
https://d.apicloud.com/mcm/api/captcha
```

**示例**

```js
$.ajax({
	"url": "https://d.apicloud.com/mcm/api/captcha",
	"method": "POST",
	"cache": false,
	"headers": {
		"X-APICloud-AppId": "{{your_app_id}}",
        "X-APICloud-AppKey": "{{加密后的key}}"
	},
	"data": {

	}
}).success(function (data, status, header) {
	//success body
}).fail(function (header, status, errorThrown) {
	//fail body
})
```
**返回值**
```js
{
    "id": "5436442ca1a14d1c60de3e06",
    "imgbase64": "{{图片转换成base64后的字符串}}",
    "createdAt": "2014-10-09T08:15:40.843Z",
    "updatedAt": "2014-10-09T08:34:28.153Z"
}
```
如下可以展示出图片
```
<img src='data:image/jpeg;base64,"+data.imgbase64 +"' />
```

返回的id,在发送短信验证的时候，需要作为token参数传递过去

验证码部分可以调用：captcha.js  现有两个版本分别对应jquery的[captcha.jquery.js](https://github.com/apicloudcom/captcha)和对应api.ajax的[captcha.apicloud.js](https://github.com/apicloudcom/captcha)

##短信验证码发送与验证返回结果

正常返回:
```js
{
	successful:true
}
```

错误返回：
```js
{
	error:{
		"name":"",
		"statusCode":"",
		"status":""
		"message":""
	}
}
```
或者
```js
//检验appId与appKey是否正确，已经检验下加密算法是否正确
{
	status:0,
	message:"invalid request."
}
```


##发送规则限制
1. 1分钟内用户允许收到的验证码上限为1条。 
2. 1小时内用户允许收到的验证码上限为7条。 
3. 1个自然日内用户允许受到的验证码上限为12条。 超出上限的验证码将被运营商直接屏蔽。 

##短信验证码限制
1. 验证码有效时间为15分钟
2. 每个手机号1小时内最多接收10条短信
3. 验证码最多可验证2次

##短信验证码注册示例
###先校验手机号再注册用户(启用图片验证码)
第一步获取图片验证码
```js
var cap = new Captcha(appId,appCode);
//获取图片添加进dom里边，展示出来
cap.getImage(function(err,img){
    if(err) return;
    $("#imgcap").html(img);
})
```
第二步输入手机号，图片验证码数字进行发送
```js
$.ajax({
	"url": "https://d.apicloud.com/mcm/api/user/sendvercode",
	"method": "POST",
	"cache": false,
	"headers": {
		"X-APICloud-AppId": "{{your_app_id}}",
        "X-APICloud-AppKey": "{{加密后的key}}"
	},
	"data": {
		"mobile":{{手机号}}
		"imageCode":{{图片验证码数字}},
		"token":cap.getToken()
	}
}).success(function (data, status, header) {
	//success body
}).fail(function (header, status, errorThrown) {
	//fail body
})
```
第三步等待用户输入短信验证码进行校验

$.ajax({
	"url": "https://d.apicloud.com/mcm/api/user/checkvercode",
	"method": "POST",
	"cache": false,
	"headers": {
		"X-APICloud-AppId": "{{your_app_id}}",
        "X-APICloud-AppKey": "{{加密后的key}}"
	},
	"data": {
		"mobile":{{手机号}},
		"vercode":{{短信验证码}}
	}
}).success(function (data, status, header) {
	//success body
	cap.setToken()//把token置为空
}).fail(function (header, status, errorThrown) {
	//fail body
})

第四步进入用户注册界面
```js
$.ajax({
	"url": "https://d.apicloud.com/mcm/api/user/checkvercode",
	"method": "POST",
	"cache": false,
	"headers": {
		"X-APICloud-AppId": "{{your_app_id}}",
        "X-APICloud-AppKey": "{{加密后的key}}"
	},
	"data": {
		"mobile":{{手机号}},
		"vercode":{{短信验证码}},
		"username":{{用户名}},
		"password":{{密码}}
		//其他字段
	}
}).success(function (data, status, header) {
	//success body
}).fail(function (header, status, errorThrown) {
	//fail body
})
```
提示:为了更加安全验证码需要二次验证
###直接注册用户(启用图片验证码)
第一步获取图片验证码
```js
var cap = new Captcha(appId,appCode);
//获取图片添加进dom里边，展示出来
cap.getImage(function(err,img){
    if(err) return;
    $("#imgcap").html(img);
})
```
第二步输入手机号，图片验证码数字进行发送
```js
$.ajax({
	"url": "https://d.apicloud.com/mcm/api/user/sendvercode",
	"method": "POST",
	"cache": false,
	"headers": {
		"X-APICloud-AppId": "{{your_app_id}}",
        "X-APICloud-AppKey": "{{加密后的key}}"
	},
	"data": {
		"mobile":{{手机号}}
		"imageCode":{{图片验证码数字}},
		"token":cap.getToken()
	}
}).success(function (data, status, header) {
	//success body
}).fail(function (header, status, errorThrown) {
	//fail body
})
```

第三步进入用户注册部分，补全注册信息
```js
$.ajax({
	"url": "https://d.apicloud.com/mcm/api/user/checkvercode",
	"method": "POST",
	"cache": false,
	"headers": {
		"X-APICloud-AppId": "{{your_app_id}}",
        "X-APICloud-AppKey": "{{加密后的key}}"
	},
	"data": {
		"mobile":{{手机号}},
		"vercode":{{短信验证码}},
		"username":{{用户名}},
		"password":{{密码}}
		//其他字段
	}
}).success(function (data, status, header) {
	//success body
	cap.setToken()//把token置为空
}).fail(function (header, status, errorThrown) {
	//fail body
})
```

提示：重置密码可以参考该步骤