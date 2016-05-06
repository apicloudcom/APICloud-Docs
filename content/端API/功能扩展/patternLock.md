/*
Title: patternLock
Description: patternLock
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：开发者</p>

#**概述**

patternLock 提供很方便的手势解锁功能呢。只需简单的几个步骤，您就可以很快将这一实用的功能集成到您的项目中。patternLock允许您自定义解锁界面颜色参数，满足您自定义UI的要求；patternLock还封装了设置密码，解锁密码和重置密码的三个常用功能，这些您只需要简单的传入一个参数就可以了实现了，极大地节省了您的时间。
#**JSON结构**<div id="a1"></div>
	{
		“name":"patternLock", 
		"class":"PatternLock",
		"methods":["addPatternLock"]
	}
#**方法**<div id="a1"></div>

- 添加手势锁

	addPatternLock(param, callback(ret,error));

	- param  

		类型：JSON 对象
		
			var param = {
				"viewName":"main",//父视图的id
				"rightColor":"#00FF00",//验证正确时界面颜色
				"drawColor":"#222222",//画密码时路径颜色
				"wrongColor":"#FF0000",//验证失败时界面颜色
				"normalColor":"#000000",//初始化时界面颜色
				"frame": "{{0,100},{320,300}}",//手势锁视图大小
				"mode": "2",//手势锁的类型
				"rightCode": "0123"//已有的密码
			};

		详细解释：

			viewName
			父视图的id，将会把手势锁视图添加到该参数视图之上
		
			rightColor ｜ drawColor ｜ wrongColor ｜ normalColor
			界面自定义颜色，颜色采用16进制格式，支持3位和6位有效值
	
			frame
			手势锁视图的大小，具有固定格式:{{left,top},{width,height}}

			rightCode
			已有的密码，用于验证密码输入是否正确，密码为0-9数字且不能有重复
		
			mode
			手势锁的类型
		
		值 | 代表含义
		--- | --- 
		0 | 解锁
		1 | 设置密码
		2 | 修改密码
	

		

- callback(ret,error)
	- ret

		返回的状态

		参数类型:JSON对象

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

	- error:
	
		错误对象

		类型：JSON 对象
		
		内部字段:

			{
				desc //错误的描述情况，如果参数不正确，将会直接显示具体参数错误信息
			}

##示例代码

```js
var patternLock = api.require('patternLock');
patternLock.addPatternLock({
	viewName: 'main',
	rightColor: '#00FF00',
	drawColor: '#222222',
	wrongColor: '#FF0000',
	normalColor: '#000000',
	frame: '{{0,100},{320,300}}',
	mode: '2',
	rightCode: '0123'
}, function(ret, err){		
	if( ret ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##详细功能
- 验证密码

	此时只需要设置mode为0

		"mode": “0”

- 设置密码

	此时只需要设置mode为1

		"mode": “1”

- 重置密码

	此时只需要设置mode为2

		"mode": “2”

- 设置界面颜色

	rightColor ｜ drawColor ｜ wrongColor ｜ normalColor
    自定义界面颜色，颜色采用16进制格式，支持3位和6位有效值

		"rightColor":"#00FF00",
		"drawColor":"#222222",
		"wrongColor":"#FF0000",
		"normalColor":"#000000",



##注意事项
- rightCode

	rightCode为原来已有的密码，用于验证密码输入是否正确。密码应为0-9的数字且不能有重复。

##补充说明
无

##可用性

iOS系统

可提供的1.0.0及更高版本