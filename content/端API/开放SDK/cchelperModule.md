/*
Title: cchelperModule
Description: cchelperModule
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">
<div class="outline">
[start](#a1)

[stop](#a2)
</div>

#**概述**

cchelperModule 模块封装了领通科技CChelper移动应用远程协助服务平台的SDK，通过调用此模块可以使用CChelper移动应用的远程协助服务，使用此模块前需要先去领通科技的CChelper SDK开放平台注册管理员账户，并且需要在管理系统中录入相关的应用信息，获取到唯一的appKey。

另外，还需要使用到PC windows 服务应用app，可以去领通科技官网的下载中心下载，同时需要在后台管理系统中添加服务人员账户，通过服务人员账户登录服务应用。

领通科技官网地址：[www.cutecomm.com](____)


#**start**<div id="a1"></div>

启动CChelper远程协助服务

start({params},callback(ret,err))

##params

userId:

- 类型：字符串
- 默认值：无
- 描述：应用的注册用户ID，如果没有可用为空

appKey:

- 类型：字符串
- 默认值：无
- 描述：领通科技CChelper SDK平台为应用生产的appKey，不可以为空

worknum:

- 类型：字符串
- 默认值：无
- 描述：领通科技CChelper SDK平台为应用分配的客服工号，可以指定客服，也可以为空


custom_data:

- 类型：字符串
- 默认值：无
- 描述：自定义传输给客服端显示的json数据，可以显示自己的公司的名称等


##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

    {
    	status:				//操作状态
    	result:1				// 登陆结果只用status为4、5时，才不为空
    	resultMsg:””			// 登陆结果描述只有status为4、5时，才不为空
    }
    
- 描述：status为操作状态，有如下类型的值：
	
	- 0 表示因为appKey为空，启动失败，同时err对象有错误数据
	- 1 表示调用start方法成功，err对象没有返回数据
	- 2 表示为监听登陆与连接服务器的状态，err对象携带状态数据
	- 3 表示为监听登陆与连接代理服务器的状态，err对象携带状态数据
	- 4 表示为登陆结果，err对象不携带任何数据
	- 5 表示启动桌面共享结果，err对象不携带任何数据
	- 6 表示主动停止服务器，err对象不携带任何数据
	- 7 表示正在等待空闲的服务人员，err对象不携带任何数据

err：

- 类型：JSON对象

内部字段：

    {
    	errorCode:		// 错误代码
    	errorMsg:””		// 错误描述
    }

##示例代码

    function startCChelper(){
    		//appKey 请登录或注册CaiHongSDK企业用户后，添加新应用获取APPKEY后，进行相关配置。
            var app_key = "cutecomm#apicloudtest";
            //该参数为应用注册用户账号或者id，主要用于后台标识具体用户的服务数据，无需则可以直接传空
            var user_id = "cutecomm";
            //该参数为指定客服的工号，如果想找指定的客服服务，否则可以传空
            var worknum = "";
            //为第三方集成应用用户自己定义传递的数据，该数据可以传递给客服端，客服端可以显示解析显示这些自定义数据，否则传空
            var custom_data = {
                "公司名称":"北京领通科技公司",
                "地址":"上地六街东口"
            };

            var param = {
                    appkey:app_key,
                    userId:user_id,
                    worknum:worknum,
                    custom_data:custom_data,
                };
			var resultCallback = function(ret, err){
				alert(JSON.stringify(ret) + "" + JSON.stringify(err));
			}
            var cchelper = api.require(‘cchelperModule’);
			cchelper.start(param, resultCallback);
		}


##补充说明

无。

##可用性

Android和iOS系统

可提供的1.0.0及更高版本


#**stop**<div id="a2"></div>

停止CChelper远程协助服务

stop()


##示例代码

    var cchelper = api.require(‘cchelperModule’);
    cchelper.stop();


##补充说明

无。

##可用性

Android和iOS系统

可提供的1.0.0及更高版本
