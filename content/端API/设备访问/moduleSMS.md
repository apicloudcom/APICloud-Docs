/*
Title: moduleSMS
Description: moduleSMS
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">
<div class="outline">

[getSmsNumber](#a1)

[startListening](#a2)

[stopListening](#a3)

[getSmsFromDB](#a4)
</div>

 #**概述**




  moduleSMS模块已更新。

 moduleSMS模块功能：

 1.获取手机本机号码

2.监听短信，收到短信后，截获短信内容返回js

3.停止短信监听

4.查询历史短信，通过查询android手机短信数据库获取短信内容



使用此模块之前需先配置config文件的permission，方法如下：



	配置示例：

````
 <permission name="sms"/>	

````


#**getSmsNumber**<div id="a1"></div>

获取本机手机号码

getSmsNumber(callback(ret, err))


##callback(ret, err)


ret：

类型：JSON对象

内部字段：

```
{
	number:185*********           //获取到的手机号码内容
}
```

err：

类型：JSON对象

内部字段：

```
{	
   code:0,	  //错误码	
   msg:""    //错误描述
}
```


##示例代码

```js
Var sms = api.require('moduleSMS');
			var resultCallback = function(ret, err) {
				document.getElementById("tel").value = ret.number
			}
			sms.getSmsNumber(resultCallback);

```

##补充说明

获取本机号码，没有获取到则返回空值

##可用性

Android系统
可提供的1.0.0及更高版本



#**startListening**<div id="a2"></div>

开启短信监听服务

param :

类型：JSON对象

内部字段:

```
{
	time:1		//监听周期 类型是正数的int类型不得超过int类型的上限，单位是分钟，如果time为0或空时，表示监听没有时间限制，一直运行直到app退出或执行stopListening。time的值为1表示监听1分钟，1分钟后自动关闭监听。
}
```

startListening(param,callback(ret, err))

##callback(ret, err)

ret：

类型：JSON对象

内部字段：

```
{
	strAddress:10652238		//发信人号码
	strbody:*******		//截取收集新接收到的短信全部内容
	strType:接收		//短信类型，接收表示接收到的短信
	strDate:YYYY-MM-dd hh:mm:ss		//短信时间
}
```

err：

类型：JSON对象

内部字段：

```
{
	msg:””		//错误描述
}

```

##示例代码

 ```

  var resultCallback = function(ret, err) {
				if (err) {
					api.alert({
						title : '错误信息',
						msg : ret.msg + " :: " + err.msg,
						buttons : ['确定']
					}, function(ret, err) {
						//coding...
					});
				} else {
					api.alert({
						title : '监听短信',
						msg : JSON.stringify(ret.strAddress) + " , " + JSON.stringify(ret.strbody) + " , " + JSON.stringify(ret.strType) + " , " + JSON.stringify(ret.strDate),
						buttons : ['确定']
					}, function(ret, err) {
						if (ret) {
						} else {
						}
					});
				}
			}
			param = {
				time : '1'
			}
			bekeerSMS.startListening(param, resultCallback);
			api.toast({
				msg : '开始监听短信'
			});
 ```

##补充说明

如果没有传入time参数，则监听程序一直运行，否则只运行指定的分钟数。

##可用性

Android系统

可提供的1.0.0及更高版本



#**stopListening**<div id="a3"></div>

停止短信监听服务


stopListening(callback(ret, err))

##callback(ret, err)

ret：

类型：JSON对象

内部字段：

```
{
	msg:监听成功关闭		//监听关闭后返回该字符串，表示关闭成功，如果返回“监听未启动，无需关闭”则表示监听服务已被关闭或未启动
}
```
err：

类型：JSON对象

内部字段：

```
{
	msg:””		//错误描述
}

```

##示例代码

```js
function stopListening() {
			var resultCallback = function(ret, err) {
				if (err) {
					api.alert({
						title : '错误信息',
						msg : ret.msg + " :: " + err.msg,
						buttons : ['确定']
					}, function(ret, err) {
						//coding...
					});
				} else {
					api.alert({
						title : '停止监听',
						msg : ret.msg,
						buttons : ['确定']
					}, function(ret, err) {
					});
				}
			}
			bekeerSMS.stopListening(resultCallback);
		}
 ```

##补充说明


##可用性

Android系统

可提供的1.0.0及更高版本



#**getSmsFromDB**<div id="a4"></div>

停止短信监听服务
getSmsFromDB(param,callback(ret, err))


param:


类型：JSON对象

描述：可根据发信人号码、起始日期、结束日期进行筛选短信，如果没有传入某个参数或为空，表示筛选不受该参数约束。

内部字段：

```
{
	address : '',		//发信人号码
	sdate : '2016-03-01',	//查询起始日期，接收短信日期
	edate : '2016-03-07'	//查询结束日期，接收短信日期
}
```


##callback(ret, err)

ret：

类型：JSON对象

内部字段：
```
{
	strAddress:10652238		//发信人号码
	strbody:*******		//截取收集新接收到的短信全部内容
	strType:接收		//短信类型，接收表示接收到的短信
	strDate:YYYY-MM-dd hh:mm:ss		//短信时间
}
```

err：

类型：JSON对象

内部字段：

```
{
	msg:		//错误描述
}

```

##示例代码

```js
function getSmsFromDB() {
			var resultCallback = function(ret, err) {
				if (err) {
					api.alert({
						title : '错误信息',
						msg : ret.msg + " :: " + err.msg,
						buttons : ['确定']
					}, function(ret, err) {
						//coding...
					});
				} else {
					for (var data in ret) {
						api.alert({
						titile:'',
						msg:"text : " + JSON.stringify(ret[data].strAddress) + " : " + JSON.stringify(ret[data].strDate) + " : " + JSON.stringify(ret[data].strbody) + " : " + JSON.stringify(ret[data].strType),
						buttons : ['确定']
                        },function(ret,err){
                        	//coding...
                        });
					}
				}
			}
			param = {
				address : '',
				sdate : '2016-03-01',
				edate : '2016-03-07'
			}
			bekeerSMS.getSmsFromDB(param, resultCallback);
		}
  ```

##补充说明

param参数可用可不用，不用param时，将查询手机内所有短信，否则按照参数条件进行查询.

##可用性

Android系统

可提供的1.0.0及更高版本
