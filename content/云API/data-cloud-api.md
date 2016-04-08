/*
Title: 数据云API
Description: 数据云API
Sort: 1
*/

[REST API 详解](#1)

[对象](#2)

[用户](#3)

[角色](#4)

[ACL](#9)

[批量操作](#8)

[文件(file)](#5)

[更新操作符](#10)

[查询](#6)

[错误代码清单](#7)

###提示
----------

现有5张系统表：accessToken、file、role、roleMapping、user

为了显示跟自定义表进行区别，所以统一在开始位置了加下划线以示区别，_accessToken、_file、_role、_roleMapping、_user。实际操作不需要加下划线。


#**REST API 详解**<div id="1"></div>

Restful API可以让您用任何可以发送 http 请求的设备来与 API Cloud 进行交互, 您可以使用 Restful API 做以下事情, 例如:

- 一个移动网站可以通过 Javascript 来获取 API Cloud 上的数据.
- 一个网站可以展示来自 API Cloud 的数据。
- 您可以上传大量的数据, 之后可以被一个移动 app 读取。
- 使用任何语言写的程序都可以操作 API Cloud 上的数据。
- 如果您不再需要使用 API Cloud，您可以导出您所有的数据。

##API 版本

- 1.0 版本：2014年9月15日发布。

##快速参考

所有的API访问都是通过HTTP进行的。相关API访问需要在https://d.apicloud.com/ 下。



##对象

<table>
    <tr>
        <th>URL</th>
        <th>HTTP</th>
        <th>功能</th>
    </tr>
    <tr>
        <td>/mcm/api/&lt;className&gt;</td>
        <td>POST</td>
        <td>创建对象</td>
    </tr>
    <tr>
        <td>/mcm/api/&lt;className&gt;/&lt;objectId&gt;</td>
        <td>GET</td>
        <td>获取对象</td>
    </tr>
    <tr>
        <td>/mcm/api/&lt;className&gt;/&lt;objectId&gt;</td>
        <td>PUT</td>
        <td>更新对象</td>
    </tr>
    <tr>
        <td>/mcm/api/&lt;className&gt;</td>
        <td>GET</td>
        <td>查询对象</td>
    <tr>
        <td>/mcm/api/&lt;className&gt;/&lt;objectId&gt;</td>
        <td>DELETE</td>
        <td>删除对象</td>
	 <tr>
        <td>/mcm/api/&lt;className&gt;/count</td>
        <td>GET</td>
        <td>统计对象数量</td>
	 <tr>
        <td>/mcm/api/&lt;className&gt;/&lt;objectId&gt;/exists</td>
        <td>GET</td>
        <td>判断对象是否存在</td>
</table>

##Relation对象

<table>
	<tr>
        <td>/mcm/api/&lt;className&gt;/&lt;objectId&gt;/&lt;relationColName&gt;</td>
        <td>GET</td>
        <td>获取关联对象</td>
    <tr>
        <td>/mcm/api/&lt;className&gt;/&lt;objectId&gt;/&lt;relationColName&gt;</td>
        <td>POST</td>
        <td>创建关联对象</td>
    <tr>
        <td>/mcm/api/&lt;className&gt;/&lt;objectId&gt;/&lt;relationColName&gt;/count</td>
        <td>GET</td>
        <td>统计关联对象数量</td>
	 <tr>
        <td>/mcm/api/&lt;className&gt;/&lt;objectId&gt;/&lt;relationColName&gt;</td>
        <td>DELETE</td>
        <td>删除所有关联对象</td>
</table>

##用户

<table>
    <tr>
        <th>URL</th>
        <th>HTTP</th>
        <th>功能</th>
    </tr>
    <tr>
        <td>/mcm/api/user/</td>
        <td>POST</td>
        <td>新增用户</td>
    </tr>
    <tr>
        <td>/mcm/api/user/login</td>
        <td>POST</td>
        <td>登录</td>
    </tr>
    <tr>
        <td>/mcm/api/user/logout</td>
        <td>POST</td>
        <td>登出</td>
    </tr>
    <tr>
        <td>/mcm/api/user/verifyEmail</td>
        <td>POST</td>
        <td>发送验证邮件</td>
    <tr>
        <td>/mcm/api/user/resetRequest</td>
        <td>POST</td>
        <td>密码重置</td>
    <tr>
        <td>/mcm/api/user/&lt;objectId&gt;</td>
        <td>GET</td>
        <td>获取用户</td>
    </tr>
    <tr>
        <td>/mcm/api/user/&lt;objectId&gt;</td>
        <td>PUT</td>
        <td>更改用户信息</td>
    <tr>
        <td>/mcm/api/user/&lt;objectId&gt;</td>
        <td>DELETE</td>
        <td>删除用户</td>
</table>



##角色

<table>
    <tr>
        <th>URL</th>
        <th>HTTP</th>
        <th>功能</th>
    </tr>
    <tr>
        <td>/mcm/api/role</td>
        <td>POST</td>
        <td>创建角色</td>
    </tr>
    <tr>
        <td>/mcm/api/role/&lt;objectId&gt;</td>
        <td>GET</td>
        <td>获取角色</td>
    </tr>
    <tr>
        <td>/mcm/api/role/&lt;objectId&gt;</td>
        <td>PUT</td>
        <td>更新角色</td>
    </tr>
    <tr>
        <td>/mcm/api/role/&lt;objectId&gt;</td>
        <td>DELETE</td>
        <td>删除角色</td>
</table>


##请求验证

当调用 APICloud 云开发接口时，我们需要对头部信息中X-APICloud-AppKey 进行验证，X-APICloud-AppKey 的生成规则如下：

```js
your app key = SHA1（你的应用ID + 'UZ' + 你的应用KEY +'UZ' + 当前时间毫秒数）.当前时间毫秒数
```

例如：你的应用ID是A6968565094002，而你的应用KEY是62FB16B2-0ED6-B460-1F60-EB61954C823B，则你在请求头部信息X-APICloud-AppKey中设置的值应为
"A6968565094002"+"UZ"+"62FB16B2-0ED6-B460-1F60-EB61954C823B"+"UZ"+当前时间毫秒数组合字符串后通过SHA1加密后返回的字符串＋.当前时间毫秒数。


示例代码如下：

```js
var now = Date.now();
var appKey = sha1("A6968565094002"+"UZ"+"62FB16B2-0ED6-B460-1F60-EB61954C823B"+"UZ"+now)+"."+now
```

##请求格式

对于POST和PUT请求，请求的主体必须是 JSON 格式，而且 HTTP header 的 Content-Type 需要设置为 application/json。
用户验证是通过 HTTP header 来进行的。**X-APICloud-AppId**头标明正在运行的是哪个App程序，而**X-APICloud-AppKey**头用来授权鉴定终端。
对于 Javascript 使用，API Cloud 支持跨域资源共享，所以您可以将这些 header 同 XMLHttpRequest 一同使用。

##响应格式

对于所有的请求的响应格式都是一个 JSON 对象。
一个请求是否成功是由 HTTP 状态码标明的。一个 2XX 的状态码表示成功，而一个 4XX 表示请求失败。当一个请求失败时响应的主体仍然是一个 JSON 对象，但是总是会包含 code。 您可以用它们来进行调试。


#**对象**<div id="2"></div>

##对象格式

通过 REST API 保存数据需要将对象的数据通过 JSON 来编码。 这个数据是无模式化的（Schema Free），这意味着您不需要提前标注每个对象上有那些 key。您只需要随意设置 key-value 对就可以， 后端会存储它的。举个例子，假设您准备设置一个公司信息。一个简单的对象可能包含：

```js
{
	"name": "API Cloud",
	"level": "Branch",
	"area": "Haidian District"
}
```

Key 必须是字母和数字组成的 String，Value 可以是任何可以 JSON 编码的东西。每个对象都有一个类名，您可以通过类名来区分不同的数据。例如, 我们可以把公司对象称之为 Company。我们推荐您使用 NameYourClassesLikeThis 和 nameYourKeysLikeThis 这样的格式为您的 Key-Value 命名，可以使您的代码看起来很漂亮。当您从 API Cloud 中获取对象时，一些字段会被自动加上：createdAt，updatedAt 和 objectID。这些字段的名字是保留的，您不能自行设置它们。我们上面设置的对象在获取时应该是下面的样子。

```js
{
	"name": "API Cloud",
	"level": "Branch",
	"area": "Haidian District",
	"createAt": "2014-08-20T02:06:57.931Z",
	"updateAt": "2014-08-20T02:06:57.931Z ",
	"objectId": "5436219ea1a14d1c60de3e05"
}
```

createdAt 和 updatedAt 都是 UTC 时间戳，以 ISO 8601 标准和毫秒级精度储存：YYYY-MM-DDTHH:MM:SS.MMMMZ。objectId 是一个 string，在类中唯一标明了一个对象。在 REST API 中 class 级的在一个资源上的操作只会根据类名来进行。例如，如果类名是 Company，那么 class 的 URL 就是
http://d.apicloud.com/mcm/api/Company

针对于一个特定的对象的操作可以通过组织一个 URL 来做。例如， 对 Company 中的一个 objectId 为 5436219ea1a14d1c60de3e05 的对象的操作应使用如下 URL：
https://d.apicloud.com/mcm/api/Company/5436219ea1a14d1c60de3e05

##创建对象

为了在 API Cloud 上创建一个新的对象，应该向 class 的 URL 发送一个 POST 请求，其中应该包含对象本身。例如，要创建如上对象：

**curl**
```js
curl -X POST \
	-H "X-APICloud-AppId: {{your_app_id}}" \
	-H "X-APICloud-AppKey: {{加密后的key}}" \
	-H "Content-Type: application/json" \
	-d '{"name": "API Cloud","level": "Branch","area": "Haidian District"}' \
    https://d.apicloud.com/mcm/api/Company
```

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.save({
	"name": "API Cloud",
	"level": "Branch",
	"area": "Haidian District"
}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company",
  	"method": "POST",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	},
  	"data": {
		"name": "API Cloud",
		"level": "Branch",
		"area": "Haidian District"
  	}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```

当创建成功时，HTTP的返回Code是 200，响应的主体是一个 JSON 对象，包含新的对象的 objectId，createdAt和updateAt 时间戳。

```js
{
	"id": "5436442ca1a14d1c60de3e06",
	"name": "API Cloud",
	"level": "Branch",
	"area": "Haidian District",
	"createdAt": "2014-10-09T08:15:40.843Z",
	"updatedAt": "2014-10-09T08:15:40.843Z"
}
```

##获取对象

当你创建了一个对象时，你可以通过发送一个 GET 请求以获取它的内容。例如，为了得到我们上面创建的对象：
**curl**
```js
curl -X GET \
	-H "X-APICloud-AppId: {{your_app_id}}" \
	-H "X-APICloud-AppKey: {{加密后的key}}" \
    https://d.apicloud.com/mcm/api/Company/5436442ca1a14d1c60de3e06
```

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.get({"_id":"5436442ca1a14d1c60de3e06"}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company/5436442ca1a14d1c60de3e06",
  	"method": "GET",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```

返回的主体是一个 JSON 对象包含所有用户提供的字段加上 createdAt，updatedAt 和 objectId 字段：

```js
{
	"id": "5436442ca1a14d1c60de3e06",
	"name": "API Cloud",
	"level": "Branch",
	"area": "Haidian District",
	"createdAt": "2014-10-09T08:15:40.843Z",
	"updatedAt": "2014-10-09T08:15:40.843Z"
}
```

##更改对象

为了更改一个对象上已经有的数据，您可以发送一个 PUT 请求到对象相应的 URL 上，任何您未指定的 key 都不会更改，所以您可以只更新对象数据的一个子集。例如，我们来更改我们对象的一个 area 的字段：

**curl**
```js
curl -X PUT \
	-H "X-APICloud-AppId: {{your_app_id}}" \
	-H "X-APICloud-AppKey: {{加密后的key}}" \
	-H "Content-Type: application/json" \
	-d '{"area":"Dongcheng District"}' \
    https://d.apicloud.com/mcm/api/Company/5436442ca1a14d1c60de3e06
```

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.save({"_id":"5436442ca1a14d1c60de3e06"},{"area":"Dongcheng District"}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company/5436442ca1a14d1c60de3e06",
  	"method": "POST",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	},
  	"data": {"area":"Dongcheng District","_method":"PUT"}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```


返回的主体是一个 JSON 对象包含所有用户提供的字段加上 createdAt，updatedAt 和 objectId 字段，其中 updatedAt 为最新的UTC更新时间戳。

```js
{
	"id": "5436442ca1a14d1c60de3e06",
	"name": "API Cloud",
	"level": "Branch",
	"area": "Dongcheng District",
	"createdAt": "2014-10-09T08:15:40.843Z",
	"updatedAt": "2014-10-09T08:34:28.153Z"
}
```

##删除对象
为了在 API Cloud 中删除一个对象，可以发送一个 DELETE 请求到指定的对象的 URL，比如：

**curl**
```js
curl -X DELETE \
	-H "X-APICloud-AppId: {{your_app_id}}" \
	-H "X-APICloud-AppKey: {{加密后的key}}" \
    https://d.apicloud.com/mcm/api/Company/5436442ca1a14d1c60de3e06
```
**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.delete({"_id":"5436442ca1a14d1c60de3e06"},function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company/5436442ca1a14d1c60de3e06",
  	"method": "POST",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	},
  	"data": {"_method":"DELETE"}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```

##数据类型

在API Cloud中创建对象时，相关对象字段数据类型可以被定义为以下十种的任何一种，相关支持数据类型如下：

- String (字符串)
- Number (数字)
- Boolean (布尔值)
- Date (日期时间)
- File (文件类型)包含id、url、name三个字段
- Array (数组)
- Object (对象)与JSON对象相同
- GeoPoint (地理位置)包含lat、lng两个字段
- Pointer (一对一)
- Relation (一对多)

#**用户**<div id="3"></div>

##新增用户

**默认everyone权限**

注册一个新用户时 username 、password两个字段都是必要的。password 字段会以和其他的字段不一样的方式处理，它在储存时会被加密而且永远不会被返回给任何来自客户端的请求。
为了新增一个用户，需要向 user 路径发送一个 POST 请求，示例如下:

**curl**
```js
curl -X POST \
	-H "X-APICloud-AppId: {{your_app_id}}" \
	-H "X-APICloud-AppKey: {{加密后的key}}" \
	-H "Content-Type: application/json" \
	-d '{"username":"apicloud","password":"123456","email":"test@apicloud.com"}' \
    https://d.apicloud.com/mcm/api/user
```

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("user");
Model.save({
	"username":"apicloud",
	"password":"123456",
	"email":"test@apicloud.com"
}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/user",
  	"method": "POST",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	},
  	"data":{
		"username":"apicloud",
		"password":"123456",
		"email":"test@apicloud.com"
	}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```

如果创建成功，返回的状态码是200，返回的主体是一个 JSON 对象，包含 objectId, createdAt和updatedAt 等属性信息，示例如下：

```js
{
	"createdAt": "2014-10-14T07:16:29.248Z",
	"updatedAt": "2014-10-14T07:16:29.248Z",
	"id": "5436442ca1a14d1c60de3e16",
	"username": "apicloud",
	"email": "test@apicloud.com"
}
```

##验证Email

设置 Email验证是API Cloud云设置选项中的一项。Email 验证会在 User 对象中改变 emailVerified 字段的值， 当一个用户的 Email 被新设置或者修改过的话，emailVerified 会被设定为 false。 API Cloud 会对用户填写的邮箱发送一个链接，当用户点击这个链接时，可以把 emailVerified 设置为 true。

emailVerified 字段有三种状态：

- true : 用户点击 email 中的地址来连接API Cloud 来验证Email地址。邮箱验证通过后，emailVerified 为 true。
- false : User 对象最后一次被刷新的时候，用户并没有确认过他的 Email 地址，如果您看到 emailVerified 为 false 的话，您可以考虑刷新 User 对象。
- null : 所创建User 对象未输入email。

##请求验证Email

**默认everyone权限**

发送给用户的邮箱验证邮件在两周内失效，为了发送验证请求，需要向verifyEmail路径发送一个 POST 请求，示例如下：

**curl**
```js
curl -X POST \
-H "X-APICloud-AppId: {{your_app_id}}" \
	-H "X-APICloud-AppKey: {{加密后的key}}" \
	-H "Content-Type: application/json" \
	-d '{"username":"apicloud","email":"customer@mail.apicloud.com","language":"zh_CN"}' \
    https://d.apicloud.com/mcm/api/user/verifyEmail
```

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("user");
Model.verify({
	"username":"apicloud",
	"email":"customer@mail.apicloud.com",
	"language":"zh_CN"
}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/user/verifyEmail",
  	"method": "POST",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	},
  	"data": {
		"username":"apicloud",
		"email":"customer@mail.apicloud.com",
		"language":"zh_CN"
	}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```
无论发送邮件成功或失败，返回的主体都是JSON对象，成功返回：

```js
{
	"status": 1,
	"msg": "发送验证邮件成功"
}
```

否则，如果失败，将返回包含具体错误原因信息的JSON对象：

```js
{
	"status": 0,
	"code": 119,
	"msg": "请在设置中开启邮箱验证服务"
}
```

注意：在进行邮件发送前，请先确认已经设置了云设置中的“注册用户邮箱验证”状态为开启状态。

##密码重置

**默认everyone权限**

您可以使用这项功能，前提是用户将 Email 与他们的账户关联起来。如果执行重置密码操作，需要发送一个 POST 请求到 /resetRequest，示例如下：

**curl**
```js
curl -X POST \
	-H "X-APICloud-AppId: {{your_app_id}}" \
	-H "X-APICloud-AppKey: {{加密后的key}}" \
	-H "Content-Type: application/json" \
	-d '{"username":"apicloud","email":"test@mail.apicloud.com","language":"zh_CN"}' \
    https://d.apicloud.com/mcm/api/user/resetRequest
```

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("user");
Model.reset({
	"username":"apicloud",
	"email":"customer@mail.apicloud.com",
	"language":"zh_CN"
}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/user/resetRequest",
  	"method": "POST",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	},
  	"data": {
		"username":"apicloud",
		"email":"customer@mail.apicloud.com",
		"language":"zh_CN"
	}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```

如果发送成功，返回的主体是一个 JSON 对象：

```js
{
	"msg": "请到邮箱查收邮件"
}
```

##获取用户

**默认owner权限**

您可以发送一个 GET 请求到 URL 以获取用户信息，示例如下:

**curl**
```js
curl -X GET \
	-H "X-APICloud-AppId: {{your_app_id}}" \
	-H "X-APICloud-AppKey: {{加密后的key}}" \
	-H "authorization":{{login 返回的id}}" \
	-H "Content-Type: application/json" \
    https://d.apicloud.com/mcm/api/user/5437a1a9e41cbf4a52d7c9d6
```

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("user");
Model.get({"_id":"5437a1a9e41cbf4a52d7c9d6"}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/user/5437a1a9e41cbf4a52d7c9d6",
  	"method": "GET",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```

返回的 body 是一个 JSON 对象，包含所有用户提供的字段，除了密码以外，也包括了 createdAt、updatedAt 和 objectId 字段。

```js
{
	"createdAt": "2014-10-14T07:16:29.248Z",
	"updatedAt": "2014-10-14T07:25:52.026Z",
	"id": "5437a1a9e41cbf4a52d7c9d6",
	"username": "apicloud",
	"email": "test@mail.apicloud.com",
	"emailVerified": null,
	"verificationToken": "701fc3d75900a0307f30e084e8b24136f9784b05f8f21ed23b472453912e9604ee8561d3d10167cb10d36f3ea9c1b5c01cc2d43242ace893ab5902637e45d6e9"
}
```

注意： 在进行用户获取操作后，相关系统会返回一个verificationToken（类似于userToken），相关Token时效为15分钟。

##更新用户

**默认owner权限**

为了更改一个用户已有的信息，需要对这个用户的 URL 发送一个 PUT 请求。 任何您没有指定过的 key 会保持不动，所以您可以只改动用户数据中的一部分，username 和 password 均可以改动，您可以发送一个 PUT 请求到 URL 以更改用户信息，示例如下：

如果我们想对用户居住地址的信息做出一些修改:

**curl**
```js
curl -X PUT \
	-H "X-APICloud-AppId: {{your_app_id}}" \
	-H "X-APICloud-AppKey: {{加密后的key}}" \
	-H "authorization":{{login 返回的id}}" \
	-H "Content-Type: application/json" \
	-d '{"address":"No.10, Building 3, Haiwei road, Haidian district"}' \
    https://d.apicloud.com/mcm/api/user/543ccdcd6c0a61303282414e
```

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("user");
Model.save({"_id":"543ccdcd6c0a61303282414e"},{"address":"No.10, Building 3, Haiwei road, Haidian district"}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/user/543ccdcd6c0a61303282414e",
  	"method": "POST",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	},
  	"data": {"address":"No.10, Building 3, Haiwei road, Haidian district","_method":"PUT"}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```

如果成功，返回的 body 是一个 JSON 对象：

```js
{
	"createdAt": "2014-10-14T07:16:29.248Z",
	"updatedAt": "2014-10-14T07:52:34.055Z",
	"id": "543ccdcd6c0a61303282414e",
	"username": "apicloud",
	"email": "test@mail.apicloud.com",
	"emailVerified": null,
	"verificationToken": "701fc3d75900a0307f30e084e8b24136f9784b05f8f21ed23b472453912e9604ee8561d3d10167cb10d36f3ea9c1b5c01cc2d43242ace893ab5902637e45d6e9",
	"address": "No.10, Building 3, Haiweiroad, Haidian district"
}
```

##删除用户

**默认owner权限**

为了在 API Cloud 上删除一个用户，可以向它的 URL 上发送一个 DELETE 请求，示例如下：

**curl**
```js
curl -X DELETE \
	-H "X-APICloud-AppId: {{your_app_id}}" \
	-H "X-APICloud-AppKey: {{加密后的key}}" \
	-H "authorization":{{login 返回的id}}" \
	-H "Content-Type: application/json" \
    https://d.apicloud.com/mcm/api/user/5437a1a9e41cbf4a52d7c9d6
```

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("user");
Model.delete({"_id":"5437a1a9e41cbf4a52d7c9d6"},function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/user/5437a1a9e41cbf4a52d7c9d6",
  	"method": "POST",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	},
  	"data": {"_method":"DELETE"}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```


##用户登录

**默认erveyone权限**

在您允许用户注册之后, 在以后您需要让他们用自己的用户名和密码登陆. 为了做到这一点, 发送一个 POST 请求到 /mcm/api/user/login, 加上 username 和 password 作为参数.

**curl**
```js
curl -X POST \
	-H "X-APICloud-AppId: {{your_app_id}}" \
	-H "X-APICloud-AppKey: {{加密后的key}}" \
	-H "Content-Type: application/json" \
	-d '{"username":"apicloud","password":"111111"}' \
    https://d.apicloud.com/mcm/api/user/login
```

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("user");
Model.login({"username":"apicloud","password":"111111"}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/user/login",
  	"method": "POST",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	},
  	"data": {"username":"apicloud","password":"111111"}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```


返回的主体是一个 JSON 对象. 它包含了 createdAt,updateAt,id,userId 和 ttl 字段.

```js
{
  "createdAt": "2015-02-02T11:12:18.484Z",
  "updatedAt": "2015-02-02T11:12:18.484Z",
  "id": "Ta48prapSvEuwGzgPuM9c8TtbHKJV0mfh4nqcVqEgpAVhMrCz2m1ih6lRZ04V73J",
  "ttl": 1209600,
  "userId": "54cf5b7bd41a2a720ee3d5fd"
}
```


##退出登录

**默认erveyone权限**

登录完成后可以把返回的id作为token进行请求，如果需要注销用户，需要发送一个 POST 请求到 /mcm/api/user/logout，把login返回的id作为headers里authorization的参数

**curl**
```js
curl -X POST \
	-H "X-APICloud-AppId: {{your_app_id}}" \
	-H "X-APICloud-AppKey: {{加密后的key}}" \
	-H "authorization":{{login 返回的id}}" \
	-H "Content-Type: application/json" \
    https://d.apicloud.com/mcm/api/user/logout
```

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("user");
Model.logout({token: "{{login 返回的id}}"}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/user/logout",
  	"method": "POST",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}",
		"authorization":{{login 返回的id}}"
  	}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```

如果成功，返回的主体是一个 空JSON 对象，

```js
{}

```


#**角色**<div id="4"></div>

当您的 app 的规模和用户基数成长时，您可能发现您需要比 ACL 模型 (针对每个用户) 更加粗粒度的访问控制您的数据的方法。为了适应这种需求, API Cloud支持一种基于角色的权限控制方式。角色系统提供一种逻辑方法让您通过权限的方式来访问您的API Cloud 数据。角色是一种有名称的对象，包含了用户和其他角色。任何授予一个角色的权限隐含着授予它包含着的其他的角色相应的权限。

##创建角色

创建一个新角色，需要发送一个 POST 请求到 role 根路径，相关示例如下：

**curl**
```js
curl -X POST \
	-H "X-APICloud-AppId: {{your_app_id}}" \
	-H "X-APICloud-AppKey: {{加密后的key}}" \
	-H "Content-Type: application/json" \
	-d '{"name":"manager1","description":"manager desc"}' \
    https://d.apicloud.com/mcm/api/role
```

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("role");
Model.save({"name":"manager1","description":"manager desc"}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/role",
  	"method": "POST",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	},
  	"data": {"name":"manager1","description":"manager desc"}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```


如果创建成功，返回的 body 是一个 JSON 对象，除了包括角色名称外也包括了 createdAt、updatedAt 和 objectId 字段，相关JSON返回对象如下：

```js
{
	"createdAt": "2014-10-16T02:31:42.399Z",
	"updatedAt": "2014-10-16T02:31:42.399Z",
	"id": "543f2e0e474f229d61185565",
	"name": "manager",
	"description": "manager desc"
}
```

##获取角色

您可以同样通过发送一个 GET 请求来获取某个角色对象。例如我们想要获取上面创建的对象：

**curl**
```js
curl -X GET \
	-H "X-APICloud-AppId: {{your_app_id}}" \
	-H "X-APICloud-AppKey: {{加密后的key}}" \
    https://d.apicloud.com/mcm/api/role/543f2e0e474f229d61185565
```

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("role");
Model.get({"_id":"543f2e0e474f229d61185565"}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/role/543f2e0e474f229d61185565",
  	"method": "GET",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```

如果成功，响应的 body 是一个包含角色所有字段的JSON对象：

```js
{
	"createdAt": "2014-10-16T02:31:42.399Z",
	"updatedAt": "2014-10-16T02:31:42.399Z",
	"id": "543f2e0e474f229d61185565",
	"name": "manager",
	"description": "manager desc"
}
```

##更新角色

您可以同样通过发送一个 PUT 请求来更新某个角色对象，比如我们想要更新上面所创建角色对象的描述：

**curl**
```js
curl -X PUT \
	-H "X-APICloud-AppId: {{your_app_id}}" \
	-H "X-APICloud-AppKey: {{加密后的key}}" \
	-d '{"name":"manager1"}' \
    https://d.apicloud.com/mcm/api/role/543f2e0e474f229d61185565
```

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("role");
Model.save({"_id":"543f2e0e474f229d61185565"},{"name":"manager1"}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/role/543f2e0e474f229d61185565",
  	"method": "POST",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	},
  	"data": {"name":"manager1","_method":"PUT"}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```

响应的 body 是一个包含角色的所有字段（含更新字段）的JSON对象：

```js
{
	"createdAt": "2014-10-16T02:31:42.399Z",
	"updatedAt": "2014-10-16T02:43:47.360Z",
	"id": "543f2e0e474f229d61185565",
	"name": "manager1",
	"description": "manager desc"
}
```

##删除角色

您可以通过发送一个 DELETE 请求来删除某个已创建的角色对象，示例如下：

**curl**
```js
curl -X DELETE \
	-H "X-APICloud-AppId: {{your_app_id}}" \
	-H "X-APICloud-AppKey: {{加密后的key}}" \
    https://d.apicloud.com/mcm/api/role/543f2e0e474f229d61185565
```

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("role");
Model.delete({"_id":"543f2e0e474f229d61185565"},function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/role/543f2e0e474f229d61185565",
  	"method": "POST",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	},
  	"data": {"_method":"DELETE"}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```

如果执行成功，则返回200状态码。

#**ACL**<div id="9"></div>

**待补充**

#**批量操作**<div id="8"></div>


为了减少网络交互的次数太多带来的时间浪费, 您可以在一个请求中对多个对象进行 create/update/delete 操作.

在一个批次中每一个操作都有相应的方法、路径和主体, 这些参数可以代替您通常会使用的 HTTP 方法. 这些操作会以发送过去的顺序来执行, 比如我们要创建一系列的 GameScore 的对象:

**curl**
```js
curl -X POST \
  -H "X-APICloud-AppId: {{your_app_id}}" \
  -H "X-APICloud-AppKey: {{加密后的key}}" \
  -H "Content-Type: application/json" \
  -d '{
        "requests": [
          {
            "method": "POST",
            "path": "/mcm/api/company",
            "body": {
              "name": "apicloud",
              "address": "北京市..."
            }
          },
          {
            "method": "POST",
            "path": "/mcm/api/company",
            "body": {
              "name": "百度",
              "address": "北京市西二旗"
            }
          }
        ]
      }' \
  https://d.apicloud.com/mcm/api/batch

```

**js-sdk**
```js
var client = new Resource("appId", "appKey");
client.batch([
	{
		"method": "POST",
		"path": "/mcm/api/company",
		"body": {
			"name": "apicloud",
			"address": "北京市..."
		}
	},
	{
		"method": "POST",
		"path": "/mcm/api/company",
		"body": {
			"name": "百度",
			"address": "北京市西二旗"
		}
	}
], function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/batch",
  	"method": "POST",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	},
  	"data": {
		"requests": [{
			"method": "POST",
			"path": "/mcm/api/company",
			"body": {
				"name": "apicloud",
				"address": "北京市..."
			}
		},
		{
			"method": "POST",
			"path": "/mcm/api/company",
			"body": {
				"name": "百度",
				"address": "北京市西二旗"
			}
		}]
	}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```
批量操作的响应会是一个列表, 列表的元素数量和给定的操作数量是一致的. 每一个在列表中的元素都是一个对象."success" 的值是通常是进行其他 REST 操作会返回的值:
```js
{
  "createdAt": "2012-06-15T16:59:11.276Z",
  "id": "51c3ba67e4b0f0e851c16221"
}

```

"error" 的值会是一个对象有返回码和 "error" 字符串:

```js
{
  "error": {
    "code": 101,
    "error": ""
  }
}

```

#**文件(file)**<div id="5"></div>

**表结构**

- name文件名称(带后缀)
- url：文件访问地址
- type：文件类型
- size：文件大小（字节）

**相关参数**

请求地址： http://d.apicloud.com/mcm/api/file

参数：

```js
	"X-APICloud-AppId: {{your_app_id}}"
	"X-APICloud-AppKey: {{加密后的key}}"
	"filename": file.name,
	"type": file.type
```

###**上传示例**

**curl示例**

```js
curl -X POST \
 -H "X-APICloud-AppId:{{your_app_id}}" \
 -H "X-APICloud-AppKey:{{加密后的key}}" \
 -H "application/x-www-form-urlencoded;" \
 -F "file=@{{file.path}};filename={{file.filename}};type={{file.type}}" \
 https://d.apicloud.com/mcm/api/file
```

**js-sdk**
```js
var File = client.Factory("file");

api.getPicture({},function(ret,err){
    File.save({file:{isFile:true,path:ret.data,values:{filename:"ava.png"}}},function(data,err){
        alert("file:\t"+JSON.stringify(data));
        alert("file:\t"+JSON.stringify(err));
    })
})
```

**web示例**

```html
<div id="picker"></div>
```

```js
var uploadurl = WebUploader.create({
	pick: "#picker",
	swf: '/libs/webuploader/Uploader.swf',
	server: 'http://d.apicloud.com/mcm/api/file',
	resize: false,
	auto: true
});
uploadurl.on("fileQueued", function (file) {
	uploadurl.option('formData', {
		filename: file.name,
		type: file.type
	});
});
//文件上传成功
uploadurl.on('uploadSuccess', function (file, res) {
	if (res && res.id) {
		alert("成功")
	} else if (res &&res.status == 0) {
		alert("失败")
	} else {
		alert("失败")
	}
});
//文件上传失败
uploadurl.on('uploadError', function (file, reason) {
	alert("失败")
});
//上传完成，不管成功失败
uploadurl.on('uploadComplete', function (file) {
	uploadurl.removeFile(file);
});
uploadurl.on('uploadBeforeSend', function (block, data, headers) {
	headers["X-APICloud-AppKey"] = "{{加密后的key}}";
	headers["X-APICloud-AppId"] = "{{your_app_id}}";
});
//上传中
uploadurl.on('uploadProgress',function(file,percentage){

});
```

提示:示例中使用的是WebUploader http://fex.baidu.com/webuploader/

成功后返回：

```js
{
	"createdAt": "2014-12-02T10:19:47.308Z",
	"updatedAt": "2014-12-02T10:19:47.308Z",
	"id": "547d924304fca43974ca87a5",
	"url": "http://file.apicloud.com/mcm/A6961095046004/a6c6cef31b5aa903db7e2788ce74f29d.png",
	"name": "2.png",
	"type": "image/png",
	"size": 3798,
	"filename": "2.png",
	"lastModifiedDate": "Tue Apr 08 2014 12:23:20 GMT+0800 (中国标准时间)"
}
```

**扩展**

如在其他表中有File类型的字段，添加记录可以如下添加：

**jquery.ajax**
```js
var file={
	id: "547d92ed04fca43974ca87a6"
	name: "2.png"
	url: "http://file.apicloud.com/mcm/A6961095046004/a6c6cef31b5aa903db7e2788ce74f29d.png"
}
var options={
	url:"http://d.apicloud.com/mcm/api/{{className}}",
	method:"POST",
	data:{
		"{{fileColumnName}}":file
		...
	},
	headers:{
		"X-APICloud-AppKey" = "{{加密后的key}}";
		"X-APICloud-AppId" = "{{your_app_id}}";
	}
}
$.ajax(options).done(function(data){
	//新增后的处理
})
```


**结果**

```js
{
	"id": "547d92ed04fca43974ca87a7",
	"createdAt": "2014-12-02T10:22:37.379Z",
	"updatedAt": "2014-12-02T10:22:37.379Z",
	"file": {
		"url": "http://file.apicloud.com/mcm/A6961095046004/a6c6cef31b5aa903db7e2788ce74f29d.png",
		"name": "2.png",
		"id": "547d92ed04fca43974ca87a6"
	}
}
```
#**更新操作符**<div id="10"></div>

###**操作符**

|名称			    | 说明 |
|--------     |--------|
|$inc			|增加字段的值指定的数量|
|$mul				|增加字段的值乘以指定的数量|
|$set			|在文档中设置一个字段的值。|
|$min			|仅更新字段如果指定的值小于现有的字段值。|
|$max		|仅更新字段如果指定的值大于现有的字段值。|
|$push		|增加一个项到数组的尾部|
|$pushAll		|增加多个项到数组的尾|
|$pull		|删除一个项从数组当中|
|$pullAll		|删除多个项从数组中|

###**$inc**
-----

$inc操作符增加一个字段指定值和具有以下形式:

```js
{ $inc: { <field1>: <amount1>, <field2>: <amount2>, ... } }
```
####行为

$inc是一个原子操作在一个文档中.

####Example

考虑有如下一个集合:

```js
{
  "_id": "543f2e0e474f229d61185565",
  "sku": "abc123",
  "quantity": 10
}
```
使用$inc进行更新

**curl**
```js
curl -X PUT \
    -H "X-APICloud-AppId: {{your_app_id}}" \
    -H "X-APICloud-AppKey: {{加密后的key}}" \
    -d '{"$inc": { quantity: -2},"sku":"APICloud"}' \
    https://d.apicloud.com/mcm/api/Company/543f2e0e474f229d61185565
```

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.save({"_id":"543f2e0e474f229d61185565"},{"$inc": { quantity: -2},"sku":"APICloud"}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company/543f2e0e474f229d61185565",
  	"method": "POST",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	},
  	"data": {"$inc": { quantity: -2},"sku":"APICloud","_method":"PUT"}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```
更新后的文档会像:
```js
{
   "_id" : 543f2e0e474f229d61185565,
   "sku" : "APICloud",
   "quantity" : 8,
}
```

###**$mul**
-----
$mul操作符增加一个字段乘以指定值和具有以下形式:

```js
{ $mul: { <field1>: <amount1>, <field2>: <amount2>, ... } }
```
####行为

$mul是一个原子操作在一个文档中.

####Example

考虑有如下一个集合:

```js
{ 
	"_id": "543f2e0e474f229d61185565", 
	"item": "ABC", 
	"price": 10.99 
}
```
使用$mul进行更新

**curl**
```js
curl -X PUT \
    -H "X-APICloud-AppId: {{your_app_id}}" \
    -H "X-APICloud-AppKey: {{加密后的key}}" \
    -d '{"$mul": { "price": 1.25 }}' \
    https://d.apicloud.com/mcm/api/Company/543f2e0e474f229d61185565
```

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.save({"_id":"543f2e0e474f229d61185565"},{"$mul": { "price": 1.25 }}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company/543f2e0e474f229d61185565",
  	"method": "POST",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	},
  	"data": {"$mul": { "price": 1.25 },"_method":"PUT"}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```

更新后的文档会像:
```js
{ 
	"_id": 1, 
	"item": "ABC", 
	"price": 13.7375 
}
```

###**$set**
-----
$set操作符替换一个字段的值用指定的值,具有以下形式:

```js
{ $set: { <field1>: <amount1>, <field2>: <amount2>, ... } }
```

####Example

考虑有如下一个集合:

```js
{
  "_id": "543f2e0e474f229d61185565",
  "sku": "abc123",
  "quantity": 250,
  "instock": true,
  "reorder": false,
  "details": { model: "14Q2", make: "xyz" },
  "tags": [ "apparel", "clothing" ],
  "ratings": [ { by: "ijk", rating: 4 } ]
}
```
使用$set进行更新

**curl**
```js
curl -X PUT \
    -H "X-APICloud-AppId: {{your_app_id}}" \
    -H "X-APICloud-AppKey: {{加密后的key}}" \
    -d '{"$set": {quantity: 500,details: { model: "14Q3", make: "xyz" },tags: [ "coats", "outerwear", "clothing" ]}}' \
    https://d.apicloud.com/mcm/api/Company/543f2e0e474f229d61185565
```

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.save({"_id":"543f2e0e474f229d61185565"},{
	"$set": {
		quantity: 500,
		details: { 
			model: "14Q3", 
			make: "xyz" 
		},
		tags: [
			"coats", 
			"outerwear", 
			"clothing" 
		]
	}
}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company/543f2e0e474f229d61185565",
  	"method": "POST",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	},
  	"data": {
		"$set": {
			quantity: 500,
			details: { 
				model: "14Q3", 
				make: "xyz" 
			},
			tags: [
				"coats", 
				"outerwear", 
				"clothing" 
			]
		},
		"_method":"PUT"
	}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```

更新后的文档会像:
```js
{
  "_id": "543f2e0e474f229d61185565",
  "sku": "abc123",
  "quantity": 500,
  "instock": true,
  "reorder": false,
  "details": { model: "14Q3", make: "xyz" },
  "tags": [ "coats", "outerwear", "clothing" ],
  "ratings": [ { by: "ijk", rating: 4 } ]
}
```

###**$min**
-----
$min操作符更新字段的值为一个指定的值,如果值小于指定字段的当前值,具有以下形式:

```js
{ $min: { <field1>: <amount1>, <field2>: <amount2>, ... } }
```

####Example

考虑有如下一个集合:

```js
{ 
	"_id": "543f2e0e474f229d61185565", 
	"highScore": 800, 
	"lowScore": 200 
}
```
使用$min进行更新

**curl**
```js
curl -X PUT \
    -H "X-APICloud-AppId: {{your_app_id}}" \
    -H "X-APICloud-AppKey: {{加密后的key}}" \
    -d '{"$min": { "lowScore": 150 }}' \
    https://d.apicloud.com/mcm/api/Company/543f2e0e474f229d61185565
```

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.save({"_id":"543f2e0e474f229d61185565"},{"$min": { "lowScore": 150 }}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company/543f2e0e474f229d61185565",
  	"method": "POST",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	},
  	"data": {"$min": { "lowScore": 150 },"_method":"PUT"}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```

更新后的文档会像:
```js
{ 
	"_id": "543f2e0e474f229d61185565", 
	"highScore": 800, 
	"lowScore": 150 
}
```

###**$max**
-----
$max操作符更新字段的值指定的值如果指定的值大于字段的当前值,具有以下形式:

```js
{ $max: { <field1>: <amount1>, <field2>: <amount2>, ... } }
```

####Example

考虑有如下一个集合:

```js
{ 
	"_id": "543f2e0e474f229d61185565", 
	"highScore": 800, 
	"lowScore": 200 
}
```
使用$set进行更新

**curl**
```js
curl -X PUT \
    -H "X-APICloud-AppId: {{your_app_id}}" \
    -H "X-APICloud-AppKey: {{加密后的key}}" \
    -d '{"$max": { "highScore": 950 }}' \
    https://d.apicloud.com/mcm/api/Company/543f2e0e474f229d61185565
```

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.save({"_id":"543f2e0e474f229d61185565"},{"$max": { "highScore": 950 }}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company/543f2e0e474f229d61185565",
  	"method": "POST",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	},
  	"data": {"$max": { "highScore": 950 },"_method":"PUT"}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```

更新后的文档会像:
```js
{ 
	"_id": 1, 
	"highScore": 950, 
	"lowScore": 200 
}
```

###**$push**
-----

$push操作符将指定值添加到数组中,具有以下形式:

```js
{ $push: { <field1>: <value1>, ... } }
```
####行为

如果字段不是数组类型，操作将会失败。

####Example

考虑有如下一个集合:

```js
{
   "_id" : "543f2e0e474f229d61185565",
   "quizzes" : [
      { "wk": 1, "score" : 10 },
      { "wk": 2, "score" : 8 },
      { "wk": 3, "score" : 5 },
      { "wk": 4, "score" : 6 }
   ]
}
```
使用$push进行更新

**curl**
```js
curl -X PUT \
    -H "X-APICloud-AppId: {{your_app_id}}" \
    -H "X-APICloud-AppKey: {{加密后的key}}" \
    -d '{"$push": { quizzes: { "wk": 5, "score": 8 }}}' \
    https://d.apicloud.com/mcm/api/Company/543f2e0e474f229d61185565
```

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.save({"_id":"543f2e0e474f229d61185565"},{"$push": { quizzes: { "wk": 5, "score": 8 }}}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company/543f2e0e474f229d61185565",
  	"method": "POST",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	},
  	"data": {"$push": { quizzes: { "wk": 5, "score": 8 }},"_method":"PUT"}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```

更新后的文档会像:
```js
{
   "_id" : "543f2e0e474f229d61185565",
   "quizzes" : [
      { "wk": 1, "score" : 10 },
      { "wk": 2, "score" : 8 },
      { "wk": 3, "score" : 5 },
      { "wk": 4, "score" : 6 },
	  { "wk": 5, "score" : 8 }
   ] 
}
```

###**$pushAll**
-----

$pushAll操作符将数组添加到数组中,具有以下形式:

```js
{ $pushAll: { <field>: [ <value1>, <value2>, ... ] } }
```
####行为

如果字段不是数组类型，操作将会失败。

####Example

考虑有如下一个集合:

```js
{
   "_id" : "543f2e0e474f229d61185565",
   "quizzes" : [
      { "wk": 1, "score" : 10 },
      { "wk": 2, "score" : 8 },
      { "wk": 3, "score" : 5 },
      { "wk": 4, "score" : 6 }
   ]
}
```
使用$pushAll进行更新

**curl**
```js
curl -X PUT \
    -H "X-APICloud-AppId: {{your_app_id}}" \
    -H "X-APICloud-AppKey: {{加密后的key}}" \
    -d '{"$pushAll": { quizzes: [{ "wk": 5, "score": 8 },{ "wk": 6, "score": 14 }]}}' \
    https://d.apicloud.com/mcm/api/Company/543f2e0e474f229d61185565
```

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.save({"_id":"543f2e0e474f229d61185565"},{"$pushAll": { quizzes: [{ "wk": 5, "score": 8 },{ "wk": 6, "score": 14 }]}}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company/543f2e0e474f229d61185565",
  	"method": "POST",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	},
  	"data": {"$pushAll": { quizzes: [{ "wk": 5, "score": 8 },{ "wk": 6, "score": 14 }]},"_method":"PUT"}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```
更新后的文档会像:
```js
{
   "_id" : "543f2e0e474f229d61185565",
   "quizzes" : [
      { "wk": 1, "score" : 10 },
      { "wk": 2, "score" : 8 },
      { "wk": 3, "score" : 5 },
      { "wk": 4, "score" : 6 },
	  { "wk": 5, "score" : 8 },
	  { "wk": 6, "score" : 14 }
   ] 
}
```

###**$pull**
-----

$pull操作符将指定项从数组中删除,具有以下形式:

```js
{ $pull: { <field1>: value, <field2>: value, ... } }
```
####行为

如果字段不是数组类型，操作将会失败。

####Example

考虑有如下一个集合:

```js
{
   _id: "543f2e0e474f229d61185565",
   fruits: [ "apples", "pears", "oranges", "grapes", "bananas" ],
   vegetables: [ "carrots", "celery", "squash", "carrots" ]
}
```
使用$pull进行更新

**curl**
```js
curl -X PUT \
    -H "X-APICloud-AppId: {{your_app_id}}" \
    -H "X-APICloud-AppKey: {{加密后的key}}" \
    -d '{"$pull": { "fruits":"apples", "vegetables": "carrots" }}' \
    https://d.apicloud.com/mcm/api/modelName/543f2e0e474f229d61185565
```


**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.save({"_id":"543f2e0e474f229d61185565"},{"$pull": { "fruits":"apples", "vegetables": "carrots" }}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company/543f2e0e474f229d61185565",
  	"method": "POST",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	},
  	"data": {"$pull": { "fruits":"apples", "vegetables": "carrots" },"_method":"PUT"}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```
更新后的文档会像:
```js
{
  "_id" : "543f2e0e474f229d61185565",
  "fruits" : [ "pears","oranges", "grapes", "bananas" ],
  "vegetables" : [ "celery", "squash" ]
}
```
###**$pullAll **
-----

$pullAll 操作符将指定项从数组中删除,具有以下形式:

```js
{ $pullAll: { <field1>: [ <value1>, <value2> ... ], ... } }
```
####行为

如果字段不是数组类型，操作将会失败。

####Example

考虑有如下一个集合:

```js
{
   _id: "543f2e0e474f229d61185565",
   "fruits": [ "apples", "pears", "oranges", "grapes", "bananas" ],
   "vegetables": [ "carrots", "celery", "squash", "carrots" ]
}
```
使用$pullAll进行更新

**curl**
```js
curl -X PUT \
    -H "X-APICloud-AppId: {{your_app_id}}" \
    -H "X-APICloud-AppKey: {{加密后的key}}" \
    -d '{"$pullAll": { "fruits": [ "apples", "oranges" ]}}' \
    https://d.apicloud.com/mcm/api/modelName/543f2e0e474f229d61185565
```

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.save({"_id":"543f2e0e474f229d61185565"},{"$pullAll": { "fruits": [ "apples", "oranges" ]}}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company/543f2e0e474f229d61185565",
  	"method": "POST",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	},
  	"data": {"$pullAll": { "fruits": [ "apples", "oranges" ]},"_method":"PUT"}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```

更新后的文档会像:
```js
{
  "_id" : "543f2e0e474f229d61185565",
  "fruits" : [ "pears", "grapes", "bananas" ],
  "vegetables": [ "carrots", "celery", "squash", "carrots" ]
}
```

#**查询**<div id="6"></div>

##类型(filterType)

- fields
- limit
- order
- skip
- where
- include
- includefilter



##请求语法

**REST 语法**

	filterType=spec&filterType=spec....

**example**

	GET /mcm/api/user?filter[where][id]=1234

**Stringified 语法**

	{ filterType: spec, filterType: spec, ... }

**example**

	GET /mcm/api/user?filter={"where":{"id":1234}}

##字段过滤(Fields filter)

设置字段是否显示在结果列表内。

**REST 语法**

```js
filter[fields][propertyName]=<true|false>&filter[fields][propertyName]=<true|false>...
```

**Stringified 语法**

	filter={ "fields": {"propertyName": <true|false>, "propertyName": <true|false>, ... } }

###Examples

只显示id,make,model字段

**REST 语法**

```js
GET /mcm/api/car?filter[fields][id]=true&filter[fields][make]=true&filter[fields][model]=true
```

**Stringified 语法**

```js
GET /mcm/api/car?filter={ "fields": {"id": true, "make": true, "model": true} }
```

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.query({
	fields:{"id": true, "make": true, "model": true}//或者["id","make","model"]
}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
var filter = {
	fields:{"id": true, "make": true, "model": true}//或者["id","make","model"]
}
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company?filter=" + encodeURIComponent(JSON.stringify(filter)),
  	"method": "GET",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```


**Returns:**

```js
[
	{
    	"id": "1",
    	"make": "Nissan",
    	"model": "Titan"
	},
	{
    	"id": "2",
    	"make": "Nissan",
		"model": "Avalon"
  	},
  ...
]
```

排除vin字段

**REST 语法**

```js
GET /mcm/api/car?filter[fields][vin]=false
```

**Stringified 语法**
```js
GET /mcm/api/car?filter={ "fields": {"vin": false} }
```

###Examples

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.query({
	fields:{"vin": false}
}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
var filter = {
	fields:{"vin": false}
}
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company?filter=" + encodeURIComponent(JSON.stringify(filter)),
  	"method": "GET",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```

##条数过滤(Limit filter)

限制返回的记录数指定的数量(或更少)

**REST 语法**
```js
filter[limit]=n
```

**Stringified 语法**
```js
filter={"limit": n}
```
###Examples

返回前5条结果

**REST 语法**
```js
GET /mcm/api/cars?filter[limit]=5
```

**Stringified 语法**
```js
GET /mcm/api/cars?filter={"limit": 5}
```
**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.query({
	limit:5
}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
var filter = {
	limit:5
}
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company?filter=" + encodeURIComponent(JSON.stringify(filter)),
  	"method": "GET",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```
##排序(Order filter)

**REST 语法**

一列
```js
filter[order]=propertyName<ASC|DESC>
```
两列

```js
filter[order][0]=propertyName <ASC|DESC>&filter[order][1]=propertyName <ASC|DESC>...
```

**Stringified 语法**

一列

```js
filter={ "order": "propertyName <ASC|DESC>" }
```
两列

```js
filter={ "order": ["propertyName <ASC|DESC>", "propertyName <ASC|DESC>",...] }
```

###Examples

按audibleRange 进行倒叙排序，并限制返回3条数据

**REST 语法**
```js
GET /mcm/api/weapons?filter[order]=audibleRange DESC&filter[limit]=3
```
**Stringified 语法**
```js
GET /mcm/api/weapons?filter={"order": "audibleRange DESC", "limit": 3 }
```

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.query({
	"order": "audibleRange DESC", 
	"limit": 3
}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
var filter = {
	"order": "audibleRange DESC", 
	"limit": 3
}
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company?filter=" + encodeURIComponent(JSON.stringify(filter)),
  	"method": "GET",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```
**跳过(Skip filter)**

跳过一些数据后返回

**REST **
```js
filter[skip]=n
```

**Stringified 语法**
```js
filter={ "skip": n }
```
###Examples

**REST 语法**
```js
GET /mcm/api/cars?filter[limit]=10&filter[skip]=20
```

**Stringified 语法**
```js
GET /mcm/api/cars?filter={"limit":10,"skip":20}
```

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.query({
	"limit":10,
	"skip":20
}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
var filter = {
	"limit":10,
	"skip":20
}
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company?filter=" + encodeURIComponent(JSON.stringify(filter)),
  	"method": "GET",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```
##条件过滤(Where filter)

在过滤器指定一组逻辑条件匹配,类似于一个where子句的SQL查询

**REST 语法**

```js
filter[where][property]=value
filter[where][property][op]=value
```
**Examples**
```js
GET /mcm/api/cars?filter[where][carClass]=fullsize
```
**Stringified 语法**
```js
filter={"where": {"property": value}}
filter={"where": {"property": {"op": value}}}
```
###Examples
```js
GET /mcm/api/cars?filter={"where":{"carClass":"fullsize"}}
```

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.query({
	"where":{"carClass":"fullsize"}
}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
var filter = {
	"where":{"carClass":"fullsize"}
}
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company?filter=" + encodeURIComponent(JSON.stringify(filter)),
  	"method": "GET",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```
**操作符**

|操作符			| 说明 |
|--------		|--------|
|and			|逻辑与|
|or				|逻辑或|
|gt,gte			|大于(>),大于或等于(> =)。只有效数值和日期值|
|lt,lte			|小于(<),小于或等于(< =)。只有效数值和日期值|
|between		|在…之间|
|inq,nin		|在/不在一个数组之内|
|near			|地理位置,返回最接近点,按距离的顺序排序|
|ne				|不等于(!=)|
|like,nlike		|like/not like 操作符返回符合正则表达式的数据|
##Examples

equal

**REST 语法**
```js
GET /mcm/api/weapons?filter[where][name]=M1911
```
**Stringified 语法**
```js
GET /mcm/api/weapons?filter={"where":{"name":"M1911"}}
```
##gt and lt

**REST 语法**
```js
GET /mcm/api/weapons?filter[where][effectiveRange][gt]=900
GET /mcm/api/weapons?filter[where][audibleRange][lt]=10
```
**Stringified 语法**
```js
GET /mcm/api/weapons?filter={"where":{"effectiveRange":{"gt":900}}}
GET /mcm/api/weapons?filter={"where":{"audibleRange":{"lt":10}}}
```
###Examples

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.query({
	"where":{
		"effectiveRange":{"gt":900},
		"audibleRange":{"lt":10}
	}
}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
var filter = {
	"where":{
		"effectiveRange":{"gt":900},
		"audibleRange":{"lt":10}
	}
}
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company?filter=" + encodeURIComponent(JSON.stringify(filter)),
  	"method": "GET",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```

##and / or

**语法**
```js
[where][<and|or>][0]condition1&[where][<and|or>]condition2...
```
**REST 语法**
```js
GET /mcm/api/cars?filter[where][and][0][title]=My%20Post&filter[where][and][1][content]=Hello
```
**Stringified 语法**
```js
GET /mcm/api/cars?filter={"where": {"and": [{"title": "My Post"}, {"content": "Hello"}]}}
```

###Examples

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.query({
	"where": {
		"and": [
			{"title": "My Post"}, 
			{"content": "Hello"}
		]
	}
}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
var filter = {
	"where": {
		"and": [
			{"title": "My Post"}, 
			{"content": "Hello"}
		]
	}
}
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company?filter=" + encodeURIComponent(JSON.stringify(filter)),
  	"method": "GET",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```

##between

**REST 语法**
```js
GET /mcm/api/cars?filter[where][price][between][0]=0&filter[where][price][between][1]=7
```
**Stringified 语法**
```js
GET /mcm/api/cars?filter={"where":{"price":{"between":[0,7]}}}
```

###Examples

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.query({
	"where": {
		"price":{"between":[0,7]}
	}
}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
var filter = {
	"where": {
		"price":{"between":[0,7]}
	}
}
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company?filter=" + encodeURIComponent(JSON.stringify(filter)),
  	"method": "GET",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```

##near

**查询的是GeoPoint列，格式为：维度,经度**

**REST 语法**
```js
GET /mcm/api/locations?filter[where][geo][near]=-28.1,153.536&filter[limit]=3
```
**Stringified 语法**
```js
GET /mcm/api//locations?filter={"where":{"geo":{"near":"-28.1,153.536"}},"limit":3}
```

###Examples

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.query({
	"where":{
		"geo":{
			"near":"-28.1,153.536"
		}
	},
	"limit":3
}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
var filter = {
	"where":{
		"geo":{
			"near":"-28.1,153.536"
		}
	},
	"limit":3
}
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company?filter=" + encodeURIComponent(JSON.stringify(filter)),
  	"method": "GET",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```

###maxDistance
对地理位置做范围限制，必须配合near使用
**REST 语法**
```js
GET /mcm/api/locations?filter[where][geo][near]=-28.1,153.536&filter[where][geo][maxDistance]=1000&filter[limit]=3
```
**Stringified 语法**
```js
GET /mcm/api//locations?filter={"where":{"geo":{"near":"-28.1,153.536","maxDistance":1000}},"limit":3}
```

###Examples

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.query({
	"where":{
		"geo":{
			"near":"-28.1,153.536",
			"maxDistance":1000
		}
	},
	"limit":3
}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
var filter = {
	"where":{
		"geo":{
			"near":"-28.1,153.536",
			"maxDistance":1000
		}
	},
	"limit":3
}
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company?filter=" + encodeURIComponent(JSON.stringify(filter)),
  	"method": "GET",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```

###type
对地理位置做范围单位限制，必须配合near使用，默认为meters
类型
  - miles(英里)
  - radians(弧度)
  - kilometers(公里)
  - meters(米)
  - feet(英尺)
  - degrees(角度)

**REST 语法**
```js
GET /mcm/api/locations?filter[where][geo][near]=-28.1,153.536&filter[where][geo][maxDistance]=1000&filter[where][geo][type]=kilometers&filter[limit]=3
```
**Stringified 语法**
```js
GET /mcm/api//locations?filter={"where":{"geo":{"near":"-28.1,153.536","maxDistance":1000,"type":"kilometers"}},"limit":3}
```

###Examples

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.query({
	"where":{
		"geo":{
			"near":"-28.1,153.536",
			"maxDistance":1000,
			"type":"kilometers"
		}
	},
	"limit":3
}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
var filter = {
	"where":{
		"geo":{
			"near":"-28.1,153.536",
			"maxDistance":1000,
			"type":"kilometers"
		}
	},
	"limit":3
}
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company?filter=" + encodeURIComponent(JSON.stringify(filter)),
  	"method": "GET",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```
##like and nlike

**REST 语法**
```js
GET /mcm/api/Post?filter[where][title][like]=M.+st
GET /mcm/api/Post?filter[where][title][nlike]=M.+XY
GET /mcm/api/User?filter[where][name][like]=%St%
GET /mcm/api/User?filter[where][name][nlike]=M%XY
```
**Stringified 语法**
```js
GET /mcm/api/Post?filter={"where":{"title": {"like": "M.+st"}}}
GET /mcm/api/Post?filter={"where":{"title": {"nlike": "M.+XY"}}}
GET /mcm/api/User?filter={"where": {"name": {"like": "%St%"}}}
GET /mcm/api/User?filter={"where": {"name": {"nlike": "M%XY"}}}
```

###Examples

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.query({
	"where":{
		"title":{
			"like":"M.+st"
		},
		"name::{
			"nlike":"M%XY"
		}
	}
}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
var filter = {
	"where":{
		"title":{
			"like":"M.+st"
		},
		"name::{
			"nlike":"M%XY"
		}
	}
}
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company?filter=" + encodeURIComponent(JSON.stringify(filter)),
  	"method": "GET",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```
##inq

**REST 语法**
```js
GET /mcm/api/medias?filter[where][keywords][inq]=foo&filter[where][keywords][inq]=bar
```
**Stringified 语法**
```js
GET /mcm/api/medias?filter={"where": {"keywords": {"inq": ["foo", "bar"]}}}
```

###Examples

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.query({
	"where":{
		"keywords": {"inq": ["foo", "bar"]}
	}
}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
var filter = {
	"where":{
		"keywords": {"inq": ["foo", "bar"]}
	}
}
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company?filter=" + encodeURIComponent(JSON.stringify(filter)),
  	"method": "GET",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```

##关系过滤(Include filter)

查询relation,pointer相关的数据

**REST 语法**
```js
GET /mcm/api/cars?filter[include][relatedModel]=propertyName
```
**Stringified 语法**
```js
GET /mcm/api/cars?filter={"include": "relatedModel"}
GET /mcm/api/cars?filter={"include": ["relatedModel1", "relatedModel2", ...]}
GET /mcm/api/cars?filter={"include": {"relatedModel1": [{"relatedModel2": "propertyName"} , "relatedModel"]}}
```
##Examples

**REST 语法**
```js
GET /mcm/api/members?filter[include]=posts
```
**Stringified 语法**
```js
GET /mcm/api/members?filter={"include":"posts"}
```
**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.query({
	"include":"posts"
}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
var filter = {
	"include":"posts"
}
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company?filter=" + encodeURIComponent(JSON.stringify(filter)),
  	"method": "GET",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```

**Returns**

```js
[
	{
		"name": "Member A",
		"age": 21,
    	"id": 1,
    	"posts": [
		{
        	"title": "Post A",
        	"id": 1,
        	"memberId": 1
      	},
		{
	        "title": "Post B",
	        "id": 2,
	        "memberId": 1
      	},
      	{
	        "title": "Post C",
	        "id": 3,
	        "memberId": 1
		}
	  ]
	},
	{
		"name": "Member B",
	    "age": 22,
	    "id": 2,
	    "posts": [
		{
	        "title": "Post D",
	        "id": 4,
	        "memberId": 2
		}
      ]
	},
... ]
```

**REST 语法**
```js
GET /mcm/api/members?filter[include][posts]=authorPointer
```
**Stringified 语法**
```js
GET /mcm/api/members?filter={"include":{"posts":"authorPointer"}}
```
**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.query({
	"include":{"posts":"authorPointer"}
}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
var filter = {
	"include":{"posts":"authorPointer"}
}
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company?filter=" + encodeURIComponent(JSON.stringify(filter)),
  	"method": "GET",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```
**Returns**

```js
[
	{
		"name": "Member A",
    	"age": 21,
    	"id": 1,
    	"posts": [
		{
	        "title": "Post A",
	        "id": 1,
	        "memberId": 1,
	        "authorPointer": {
				"name": "Member A",
	          	"age": 21,
	          	"id": 1
        	}
		},
      	{
	        "title": "Post B",
	        "id": 2,
	        "memberId": 1,
	        "authorPointer": {
          		"name": "Member A",
          		"age": 21,
          		"id": 1
        }
	},
      {
	        "title": "Post C",
	        "id": 3,
	        "memberId": 1,
	        "authorPointer": {
				"name": "Member A",
				"age": 21,
				"id": 1
        }
      }
    ]
  },
  {
    "name": "Member B",
    "age": 22,
	"id": 2,
    "posts": [
		{
			"title": "Post D",
        	"id": 4,
        	"memberId": 2,
        	"authorPointer": {
	          	"name": "Member B",
	          	"age": 22,
	          	"id": 2
        }
      }
    ]
  }, ... ]
```

**REST 语法**
```js
GET /api/members?filter[include][posts]=authorPointer&filter[where][age]=21
```
**Stringified 语法**
```js
GET /api/members?filter={"include":{"posts":"authorPointer"},"where":{"age":21}}
```
**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.query({
	"include":{"posts":"authorPointer"},
	"where":{"age":21}
}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
var filter = {
	"include":{"posts":"authorPointer"},
	"where":{"age":21}
}
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company?filter=" + encodeURIComponent(JSON.stringify(filter)),
  	"method": "GET",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```
**Returns**

```js
[
  {
    "name": "Member A",
    "age": 21,
    "id": 1,
    "posts": [
      {
        "title": "Post A",
        "id": 1,
        "memberId": 1,
        "authorPointer": {
          "name": "Member A",
          "age": 21,
          "id": 1
        }
      },
      {
        "title": "Post B",
        "id": 2,
        "memberId": 1,
        "authorPointer": {
          "name": "Member A",
          "age": 21,
          "id": 1
        }
      },
      {
        "title": "Post C",
        "id": 3,
        "memberId": 1,
        "authorPointer": {
          "name": "Member A",
          "age": 21,
          "id": 1
        }
      }
    ]
  }
]
```

**REST 语法**
```js
GET /mcm/api/members?filter[include][posts]=authorPointer&filter[limit]=2
```
**Stringified 语法**
```js
GET /mcm/api/members?filter={"include":{"posts":"authorPointer"},"limit":2}
```
**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.query({
	"include":{"posts":"authorPointer"},
	"limit":2
}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
var filter = {
	"include":{"posts":"authorPointer"},
	"limit":2
}
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company?filter=" + encodeURIComponent(JSON.stringify(filter)),
  	"method": "GET",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```
**Returns**

```js
[
  {
    "name": "Member A",
    "age": 21,
    "id": 1,
    "posts": [
      {
        "title": "Post A",
        "id": 1,
        "memberId": 1,
        "authorPointer": {
          "name": "Member A",
          "age": 21,
          "id": 1
        }
      },
      {
        "title": "Post B",
        "id": 2,
        "memberId": 1,
        "authorPointer": {
          "name": "Member A",
          "age": 21,
          "id": 1
        }
      },
      {
        "title": "Post C",
        "id": 3,
        "memberId": 1,
        "authorPointer": {
          "name": "Member A",
          "age": 21,
          "id": 1
        }
      }
    ]
  },
  {
    "name": "Member B",
    "age": 22,
    "id": 2,
    "posts": [
      {
        "title": "Post D",
        "id": 4,
        "memberId": 2,
        "authorPointer": {
          "name": "Member B",
          "age": 22,
          "id": 2
        }
      }
    ]
  }
]
```

**REST 语法**
```js
GET /mcm/api/members?filter[include]=posts&filter[include]=passports
```
**Stringified 语法**
```js
GET /mcm/api/members?filter={"include":["posts","passports"]}
```
**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.query({
	"include":["posts","passports"]
}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
var filter = {
	"include":["posts","passports"]
}
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company?filter=" + encodeURIComponent(JSON.stringify(filter)),
  	"method": "GET",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```
**Returns**

```js
[
  {
    "name": "Member A",
    "age": 21,
    "id": 1,
    "posts": [
      {
        "title": "Post A",
        "id": 1,
        "memberId": 1
      },
      {
        "title": "Post B",
        "id": 2,
        "memberId": 1
      },
      {
        "title": "Post C",
        "id": 3,
        "memberId": 1
      }
    ],
    "passports": [
      {
        "number": "1",
        "id": 1,
        "ownerId": 1
      }
    ]
  },
  {
    "name": "Member B",
    "age": 22,
    "id": 2,
    "posts": [
      {
        "title": "Post D",
        "id": 4,
        "memberId": 2
      }
    ],
    "passports": [
      {
        "number": "2",
        "id": 2,
        "ownerId": 2
      }
    ]
  }, ... ]
```

##关系表过滤(Include filter)


对relation,pointer相关的数据进行过滤，必须配合include使用

**REST 语法**
```js
GET /mcm/api/cars?filter[include][relatedModel]=propertyName&filter[includefilter][relatedModelName][limit]=2
```
**Stringified 语法**
```js
GET /mcm/api/cars?filter={"include": "relatedModel","includefilter":{"relatedModelName":{"limit":2}}}
GET /mcm/api/cars?filter={"include": ["relatedModel1", "relatedModel2", ...],"includefilter":{"relatedModel1Name":{"limit":2},"relatedModel2Name":{"where":{"propertyName":"username"}}}}
GET /mcm/api/cars?filter={"include": {"relatedModel1": [{"relatedModel2": "propertyName"} , "relatedModel"]},"includefilter":{"relatedModel1Name":{"limit":2},"relatedModel2Name":{"where":{"propertyName":"username"}},"relatedModelName":{"limit":2}}}
```

**提示** relatedModel1Name 为relation或者pointer的class的名称，如果是relation的表，则id为必须要返回的字段，如果是pointer的表，则id与pointer的字段为必须返回字段

##Examples

**REST 语法**
```js
GET /mcm/api/members?filter[include]=posts&filter[includefilter][Posts][limit]=2
```
**Stringified 语法**
```js
GET /mcm/api/members?filter={"include":"posts","includefilter":{"Posts":{"limit":2}}}
```
**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.query({
	"include":"posts",
	"includefilter":{"Posts":{"limit":2}}
}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
var filter = {
	"include":"posts",
	"includefilter":{"Posts":{"limit":2}}
}
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company?filter=" + encodeURIComponent(JSON.stringify(filter)),
  	"method": "GET",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```
**Returns**

```js
[
	{
		"name": "Member A",
		"age": 21,
    	"id": 1,
    	"posts": [
		{
        	"title": "Post A",
        	"id": 1,
        	"memberId": 1
      	},
		{
	        "title": "Post B",
	        "id": 2,
	        "memberId": 1
      	}
	  ]
	},
	{
		"name": "Member B",
	    "age": 22,
	    "id": 2,
	    "posts": [
		{
	        "title": "Post D",
	        "id": 4,
	        "memberId": 2
		}
      ]
	},
... ]
```

**REST 语法**
```js
GET /mcm/api/members?filter[include][posts]=authorPointer&filter["includefilter"][author][fields]=id&filter["includefilter"][author][fields]=name
```
**Stringified 语法**
```js
GET /mcm/api/members?filter={"include":{"posts":"authorPointer"},"includefilter":{"author":{"fields":["id","name"]}}}
```
**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.query({
	"include":{"posts":"authorPointer"},
	"includefilter":{"author":{"fields":["id","name"]}}
}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
var filter = {
	"include":{"posts":"authorPointer"},
	"includefilter":{"author":{"fields":["id","name"]}}
}
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company?filter=" + encodeURIComponent(JSON.stringify(filter)),
  	"method": "GET",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```

**Returns**

```js
[
	{
		"name": "Member A",
    	"age": 21,
    	"id": 1,
    	"posts": [
		{
	        "title": "Post A",
	        "id": 1,
	        "memberId": 1,
	        "authorPointer": {
				"name": "Member A",
	          	"id": 1
        	}
		},
      	{
	        "title": "Post B",
	        "id": 2,
	        "memberId": 1,
	        "authorPointer": {
          		"name": "Member A",
          		"id": 1
        }
	},
      {
	        "title": "Post C",
	        "id": 3,
	        "memberId": 1,
	        "authorPointer": {
				"name": "Member A",
				"id": 1
        }
      }
    ]
  },
  {
    "name": "Member B",
    "age": 22,
	"id": 2,
    "posts": [
		{
			"title": "Post D",
        	"id": 4,
        	"memberId": 2,
        	"authorPointer": {
	          	"name": "Member B",
	          	"id": 2
        }
      }
    ]
  }, ... ]
```

**REST 语法**
```js
GET /api/members?filter[include][posts]=authorPointer&filter[where][age]=21&filter[includefilter][post][where][title]=Post A&filter[includefilter][author][fields]=id&filter[includefilter][author][fields]=name
```
**Stringified 语法**
```js
GET /api/members?filter={"include":{"posts":"authorPointer"},"where":{"age":21},"includefilter":{"post":{"where":{"title":"Post A"}},"author":{"fields":["id","name"]}}}
```
**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.query({	
	"where":{"age":21},
	"include":{"posts":"authorPointer"},
	"includefilter":{
		"post":{"where":{"title":"Post A"}},
		"author":{"fields":["id","name"]}
	}
}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
var filter = {
	"where":{"age":21},
	"include":{"posts":"authorPointer"},
	"includefilter":{
		"post":{"where":{"title":"Post A"}},
		"author":{"fields":["id","name"]}
	}
}
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company?filter=" + encodeURIComponent(JSON.stringify(filter)),
  	"method": "GET",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```

**Returns**

```js
[
  {
    "name": "Member A",
    "age": 21,
    "id": 1,
    "posts": [
      {
        "title": "Post A",
        "id": 1,
        "memberId": 1,
        "authorPointer": {
          "name": "Member A",
          "id": 1
        }
      }
    ]
  }
]
```

**REST 语法**
```js
GET /mcm/api/members?filter[include][posts]=authorPointer&filter[limit]=2&filter[includefilter][post][limit]=2
```
**Stringified 语法**
```js
GET /mcm/api/members?filter={"include":{"posts":"authorPointer"},"limit":2,"includefilter":{"post":{"limit":2}}}
```

**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.query({	
	"include":{"posts":"authorPointer"},
	"limit":2,
	"includefilter":{"post":{"limit":2}}
}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
var filter = {
	"include":{"posts":"authorPointer"},
	"limit":2,
	"includefilter":{"post":{"limit":2}}
}
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company?filter=" + encodeURIComponent(JSON.stringify(filter)),
  	"method": "GET",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```

**Returns**

```js
[
  {
    "name": "Member A",
    "age": 21,
    "id": 1,
    "posts": [
      {
        "title": "Post A",
        "id": 1,
        "memberId": 1,
        "authorPointer": {
          "name": "Member A",
          "age": 21,
          "id": 1
        }
      },
      {
        "title": "Post B",
        "id": 2,
        "memberId": 1,
        "authorPointer": {
          "name": "Member A",
          "age": 21,
          "id": 1
        }
      }
    ]
  },
  {
    "name": "Member B",
    "age": 22,
    "id": 2,
    "posts": [
      {
        "title": "Post D",
        "id": 4,
        "memberId": 2,
        "authorPointer": {
          "name": "Member B",
          "age": 22,
          "id": 2
        }
      }
    ]
  }
]
```

**REST 语法**
```js
GET /mcm/api/members?filter[include]=posts&filter[include]=passports&filter[limit]=5&filter[includefilter][post][limit]=1&filter[includefilter][passport][limit]=1
```
**Stringified 语法**
```js
GET /mcm/api/members?filter={"include":["posts","passports"],"limit":5,"includefilter":{post:{"limit":1},"passport":{"limit":1}}}
```
**js-sdk**
```js
var client = new Resource("appId", "appKey");
var Model = client.Factory("Company");
Model.query({	
	"include":["posts","passports"],
	"limit":5,
	"includefilter":{
		post:{"limit":1},
		"passport":{"limit":1}
	}
}, function(ret,err){
	if(err){
		//处理错误 err
	}else{
		//处理数据 ret
	}
})
```	

**jquery.ajax**
```js
var filter = {
	"include":["posts","passports"],
	"limit":5,
	"includefilter":{
		post:{"limit":1},
		"passport":{"limit":1}
	}
}
$.ajax({
  	"url": "https://d.apicloud.com/mcm/api/Company?filter=" + encodeURIComponent(JSON.stringify(filter)),
  	"method": "GET",
  	"cache": false,
  	"headers": {
    	"X-APICloud-AppId": "{{your_app_id}}",
    	"X-APICloud-AppKey": "{{加密后的key}}"
  	}
}).success(function (data, status, header) {
  	//success body
}).fail(function (header, status, errorThrown) {
  	//fail body
})
```
**Returns**

```js
[
  {
    "name": "Member A",
    "age": 21,
    "id": 1,
    "posts": [
      {
        "title": "Post A",
        "id": 1,
        "memberId": 1
      }
    ],
    "passports": [
      {
        "number": "1",
        "id": 1,
        "ownerId": 1
      }
    ]
  },
  {
    "name": "Member B",
    "age": 22,
    "id": 2,
    "posts": [
      {
        "title": "Post D",
        "id": 4,
        "memberId": 2
      }
    ],
    "passports": [
      {
        "number": "2",
        "id": 2,
        "ownerId": 2
      }
    ]
  }, ... ]
```

**提示**：pointer类型的列查询时需要在列名后增加Pointer，例如列名author，查询时就是authorPointer

#**错误代码清单**<div id="7"></div>

- 100:"操作失败",
- 101:"应用不存在",
- 102:"数据云服务未开启，请在控制台的云开发中开启！",
- 103:"您没有应用访问权限",
- 104:"参数错误",
- 105:"Class不存在",
- 106:"Class名称错误",
- 107:"Class名称已经存在",
- 108:"连接数据库失败",
- 109:"内置Class不可删除",
- 110:"列字段已经存在",
- 111:"删除Class失败",
- 112:"删除数据失败",
- 113:"默认字段不可删除",
- 114:"删除列失败",
- 115:"导入数据文件不可为空",
- 116:"导入数据失败",
- 117:"导出数据失败",
- 118:"邮箱格式错误",
- 119:"邮箱验证未开启, 请在控制台的云开发中开启！",
- 120:"文件不存在",
- 121:"文件上传失败",
- 122:"保存文件失败",
- 123:"文件大小不能大于20M"
- 124:"导出数据不存在"
