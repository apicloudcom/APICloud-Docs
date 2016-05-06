/*
Title: qiniuUpfile
Description: qiniuUpfile
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

qiniuUpfile 模块封装了七牛上传文件的相关操作，开发者只需简单地调用相关接口，即可把图片或文档上传到七牛并共享给其他用户，本模块使用前需到[七牛](http://www.qiniu.com/)注册账号，本模块采用本地模拟TOKEN生成，不需要另外架设TOKEN服务器。

**使用此模块之前需配置  config 文件来设置bucket以及SK、AK，配置方法如下：**

- 名称：qiniuUpfile
- 参数：bucket，SecretKey，AccessKey
- 备注：以上参数为必填项，请依据实际情况填写，否则上传时会报错。
- 配置示例:


      <feature name="qiniuUpfile"> 
       <param name="bucket" value="空间名"/>  
       <param name="SecretKey" value="你在七牛获取到的SecretKey"/>  
       <param name="AccessKey" value="你在七牛获取到的AccessKey"/> 
      </feature>    

- 字段描述:

		1. bucket：在注册七牛后自定义的空间名称
		2. SecretKey:安全秘钥
		3. AccessKey: 授权秘钥


# 获取AK/SK
登录七牛后在个人控制面板中选择秘钥管理，点击可查看管理AK/SK
![image](http://www.sihee.com.cn/h/42.png)

![image](http://www.sihee.com.cn/h/41.png)


# 自定义bucket
注册登录后添加资源，选择添加对象存储
![image](http://www.sihee.com.cn/h/43.png)
按要求输入自定义的名称
![image](http://www.sihee.com.cn/h/44.png)

# 获取回调地址
文件上传成功后，需要在程序中引用，七牛提供一个测试的地址供我们使用，每个人分配的地址都是唯一的。

地址获取方法如下：1、选择你新建的【对象存储】

![image](http://www.sihee.com.cn/h/45.png)
2、查看七牛的测试域名
![image](http://www.sihee.com.cn/h/46.png)


3、将测试域名记录，并与返回的KEY组合，即为文件地址，如http://xxx.z0.glb.clouddn.com/xxxxc


#**upfile**<div id="1"></div>

上传文件

upfile({params}, callback(ret, err))

##params

file：

- 类型：字符串
- 描述：通过图片或文件选择器获得的文件路径url

name：

- 类型：字符串
- 描述：（可选项）自定义的在七牛空间中的文件名，如不填写则采用文件的HASH值做文件名，避免文件名有冲突


##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:,		 //布尔类型；状态值，true|false
	oper:  ,      //字符串类型；操作状态:complete-完成;progress-进度
	info: {       //JSON对象；只在oper为complete的时候返回，progress时为隐藏
	    key:  ,   //字符串类型；返回的文件名
	    hash: ,   //字符串类型；返回的文件哈希值 
	},
	percent:      //数字类型；上传进度,如1.1,12.11,50.34......95.0......100         
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
     msg:         //字符串类型；错误信息
}
```

##示例代码

       ...html
       <div>
			上传进度：<p id="progress"></p>
		</div>
		   <p id="backurl"></p>
       
       ```js
        var a = document.getElementById('progress');//显示进度，也可用进度条，在进度从95%到100%的时候有个明显停顿，此时文件已经传输完成，是在获取回调信息。
        var b = document.getElementById('imge');
        var fileurl = '/storage/emulated/0/UZMap/picture/p1357545.jpg';//文件地址，也可通过文件选择器获得
        var baseUrl = 'xxxx.com0.z0.glb.clouddn.com';//七牛给你的测试域名，也可使用自己捆绑的域名youe.xxx.com
        var obj = api.require('qiniuUpfile');
            obj.upfile({
	        file:fileurl,
	        name:'hello'
            },function(ret,err){
	            if(ret.status) {
		          if(ret.oper == "complete"){
                 //上传成功后组装访问路径，或直接访问文档
                 $api.text(b, baseUrl+ret.info.key);
                  }else if(ret.oper == "progress"){
                   //上传过程中获取进度数据
                    $api.text(a, ret.percent);
                  }
	             }
            });
        ```

##补充说明

###【文档管理】
登录七牛后台可进行上传文件的管理
![image](http://www.sihee.com.cn/h/47.png)
![image](http://www.sihee.com.cn/h/48.png)
外链默认域名加文件名就是文件的连接。

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


