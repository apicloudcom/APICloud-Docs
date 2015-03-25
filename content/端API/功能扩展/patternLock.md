/*
Title: patternLock
Description: patternLock
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

#**概述**

JS对象调用patternLock模块，实现手势解锁，设置密码和修改密码的功能，并且能够自定义颜色参数

##JSON结构

	{
		“name":"patternLock", 
		"class":"PatternLock",
		"methods":["addPatternLock"]
	}

##方法

添加手势锁

	addPatternLock(param, callback(ret,error));

param  

```js

类型：JSON对象
		
var param = {
	"viewName":"main",//父视图的id
	"rightColor":"#00FF00",//验证正确时界面颜色
	"drawColor":"#222222",//画密码时路径颜色
	"wrongColor":"#FF0000",//验证失败时界面颜色
	"normalColor":"#000000",//初始化时界面颜色
	"frame": "{{0,100},{320,300}}",//手势锁视图大小
	"mode": "2",//手势锁的类型
	"rightCode": "0123"//已有的密码
};```

详细解释：

```js
	viewName
	父视图的id，将会把手势锁视图添加到该参数视图之上
		
	rightColor ｜ drawColor ｜ wrongColor ｜ normalColor
	界面自定义颜色，颜色采用16进制格式，支持3位和6位有效值
	
	frame
	手势锁视图的大小，具有固定格式:{{left,top},{width,height}}

	rightCode
	已有的密码，用于验证密码输入是否正确
		
	mode
	手势锁的类型
		
	值 | 代表含义
	--- | --- 
	0 | 解锁
	1 | 设置密码
	2 | 修改密码
```		

##callback(ret,error)

ret

返回的状态

- 参数类型:JSON对象

```js
{
	status //操作状态值
}

	值 | 代表含义
	--- | --- 
	0|解锁成功
	1|解锁失败
	2|提示请重复输入
	3|重复输入不一致
	4|重复输入一致，新密码设置成功
	5|修改密码验证成功
	6|修改密码验证失败
```
rror:
	
错误对象

- 类型：JSON对象
		
内部字段:

	{
		desc //错误的描述情况，如果参数不正确，将会直接显示具体参数错误信息
	}

##示例代码

```js
<script type="text/javascript">
	function callBack(ret, err){
		if(err) {
			alert("error :" + err.desc);
		} else {
			switch(ret.status)
		{
			case 0:
			{
				alert("Unlock Right");
			}
			break;
			case 1:
			{
				alert("Unlock Wrong");
			}
			break;
			case 2:
			{	
				alert("Repeat It");
			}
			break;
			case 3:
			{
				alert("Repeat It Worng");
			}
			break;
			case 4:
			{
				alert("Repeat It Right" + ret.code);
			}
			break;
			case 5:
			{
				alert("Verify For Chg Worng");
			}
			break;
			case 6:
			{
				alert("Verify For Chg Right");
			}
			break;
			default:
		}
	}
}
apiready = function(){
	var demo = api.require('patternLock');
	var param = {
		"viewName":"main",
		"rightColor":"#00FF00",
		"drawColor":"#222222",
		"wrongColor":"#FF0000",
		"normalColor":"#000000",
		"frame": "{{0,100},{320,300}}",
		"mode": "2",
		"rightCode": "0123"//[0-8] and not duplicate
	};
	demo.addPatternLock(param, callBack);
};
</script>
```

##补充说明

注册应用

##可用性

iOS系统

可提供的1.0.0及更高版本
