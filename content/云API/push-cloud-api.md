/*
Title: 推送云API
Description: 推送云API
Sort: 3
*/

#**接口验证KEY生成规则说明：**

**生成规则**

当调用 APICloud推送相关接口时，我们需要对头部信息中X-APICloud-AppKey 进行验证，X-APICloud-AppKey 的生成规则如下：

```js
AppKey= SHA1（你的应用ID + 'UZ' + 你的应用KEY +'UZ' +当前时间毫秒数）.当前时间毫秒数
```

例如：你的应用ID是A6968565094002，而你的应用KEY是62FB16B2-0ED6-B460-1F60-EB61954C823B，则你在请求头部信息X-APICloud-AppKey中设置的值应为

```js
var now = Date.now();

varappKey = sha1("A6968565094002"+"UZ"+ "62FB16B2-0ED6-B460-1F60-EB61954C823B"+"UZ"+now)+"."+now;
```

#**接口名称：消息推送接口**

**接口说明**

向某个推送组所有的成员推送消息。

**调用地址**

https://p.apicloud.com/api/push/message

**请求方式**

POST

**请求头部设置说明**

	相关接口调用需要在发送的请求头部设置相关应用ID及应用KEY。相关请求头部设置定义如下：
	X-APICloud-AppId : {your app id}
	X-APICloud-AppKey : {you app key}

**接口接收参数**

	title–消息标题，
	content – 消息内容
	type – 消息类型，1:消息 2:通知
	platform - 0:全部平台，1：ios, 2：android
	groupName - 推送组名，多个组用英文逗号隔开.默认:全部组。eg.group1,group2 .
    userIds - 推送用户id, 多个用户用英文逗号分隔，eg. user1,user2。

**接口返回数据**

```js
成功返回：
	{ status:1}
```


js 示例：


```
	 
		
			var now = Date.now();
		    var	appKey = $.sha1("A690146020****" + "UZ" + "580DAADD-523D-89ED-3913-9AC1FE4C****" + "UZ" + now) + "." + now;
		
		function push() {
			api.ajax({
				url : 'https://p.apicloud.com/api/push/message',
				method : "post",
				headers : {
					"X-APICloud-AppId" : "A690146020****",
					"X-APICloud-AppKey" : appKey
				},
				dataType : "json",
				data : {
					"values" : {
						"title" : "消息标题",
						"content" : "消息内容",
						"type" : 1, //– 消息类型，1:消息 2:通知
						"platform" : 0, //0:全部平台，1：ios, 2：android
					//	"groupName" : "department", //推送组名，多个组用英文逗号隔开.默认:全部组。eg.group1,group2 .
					//	"userIds" : "testId" //推送用户id, 多个用户用英文逗号分隔，eg. user1,user2。
					}
				}
			}, function(ret, err) {
				//coding...
				alert(JSON.stringify(ret))
				alert(JSON.stringify(err))
			});
		}
```