/*
Title: upyunUpfile
Description: upyunUpfile
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：开发者</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[upfile](#1)
</div>

#**概述**

upyunUpfile 模块封装了又拍云上传文件的相关操作，开发者只需简单地调用相关接口，即可把图片或文档上传到又拍云并共享给其他用户，本模块使用前需到[upyun](http://www.upyun.com/)注册账号，本模块采用HTTP FORM API，不需要另外架设TOKEN服务器。

**使用此模块之前需配置  config 文件来设置bucket以及表单秘钥配置方法如下：**

- 名称：upyunUpfile
- 参数：bucket，tablekey
- 备注：以上参数为必填项，请依据实际情况填写，否则上传时会报错。
- 配置示例:


      <feature name="upyunUpfile"> 
       <param name="bucket" value="空间名"/>  
       <param name="tablekey" value="你在又拍获取到的表单 API密钥"/>  
      </feature>    

- 字段描述:

		1. bucket：在注册又拍后自定义的空间名称
		2. tablekey:表单安全密钥


# 获取表单API秘钥
登录UPYUN后在服务的高级功能中选择打开表单API，直接复制或更换**【密钥】**
![image](http://www.sihee.com.cn/h/51.png)



# 自定义bucket
注册登录后添加服务，选择创建服务
![image](http://www.sihee.com.cn/h/52.png)

按要求输入自定义的名称并创建操作者用于FTP登录。

![image](http://www.sihee.com.cn/h/53.png)

#**upfile**<div id="1"></div>

上传文件

upfile({params}, callback(ret, err))

##params

file：

- 类型：字符串
- 描述：通过图片或文件选择器获得的文件路径url

name：

- 类型：字符串
- 描述：（可选项）自定义的在又拍空间中的文件名，如不填写则采用文件名的MD5值做文件名。文件名可带路径如/up/hello.jpg


##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status: false,	      //布尔类型；状态值，true|false
	oper: 'complete',     //字符串类型；操作状态:complete-完成;progress-进度
	info:{                //JSON对象；info只在oper为complete的时候返回，progress时为隐藏
	    image-type:       //字符串类型；图片类型:JPEG;PNG
	    image-frames:     //数字类型；图片数量:1
	    image-height:     //数字类型；图片高度
	    image-width:      //数字类型；图片宽度
	    sign:             //字符串类型；图片签名
	    code:             //数字类型；返回代码:200具体请看API CODE表
	    file_size:        //数字类型；文件大小
	    url:              //字符串类型；返回的文件名，用于url访问
	    time:             //字符串类型；上传时间
	    message:          //字符串类型；返回消息 
	},
	percent:             //数字类型；上传进度,如1,39,55...100          
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
   msg:             //字符串类型；错误信息
}
```

##示例代码

       ```js
        var fileurl = '/storage/emulated/0/UZMap/A546678877855/picture/p1357545.jpg';
        var baseUrl = 'backet.b0.upaiyun.com';//又拍给你的访问域名，也可使用自己捆绑的域名youe.xxx.com
        var obj = api.require('upyunUpfile');
            obj.upfile({
	        file:fileurl,
	        name:'/hello/1.jpg'
            },function(ret,err){
	            if(ret.status) {
		          if(ret.oper == "complete"){
                 //上传成功后组装访问路径在IMG中显示图片，或直接访问文档
                    $api.attr(b,'src',baseUrl+ret.info.key);
                  }else if(ret.oper == "progress"){
                   //上传过程中获取进度数据
                    $api.text(a, ret.percent);
                  }
	             }
            });
        ```

##补充说明
#### 【创建管理员】
创建管理员是为了管理服务空间的，在服务器端需要管理员进行相关操作，下面的FTP管理也需要管理员账号密码。
![image](http://www.sihee.com.cn/h/55.png)
![image](http://www.sihee.com.cn/h/56.png)
#### 【管理上传文件】

UPYUN的文件管理采用FTP方式，登录账号为操作员账号/服务名；密码为操作员密码，如操作员账号admin，密码12345，服务名称为upup，则FTP登录账号为:**admin/upup**，密码是12345，

![image](http://www.sihee.com.cn/h/54.png)
使用FTP工具，填写如下：
![image](http://www.sihee.com.cn/h/57.png)
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


