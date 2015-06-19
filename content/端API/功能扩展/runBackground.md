#**概述**

一键退到后台运行，安卓手机可以在后台运行做的app。


#**hideActivity**<div id="a1"></div>

退到后台运行

hideActivity()

##示例代码

```js
//安卓应用
var isAndroid = (/android/gi).test(navigator.appVersion);
if(isAndroid){
    var rb = api.require('runBackground');
	rb.hideActivity();
}

//绑定安卓的后退按钮事件 两秒内后退按钮点击两次 退到后台运行
var backSecond = 0;
api.addEventListener({
	name : 'keyback'
}, function (ret, err) {
	var curSecond = new Date().getSeconds();
	if (Math.abs(curSecond - backSecond) > 2) {
		backSecond = curSecond;
		api.toast({
			msg : '连续按两次到后台运行',
			duration : 2000,
			location : 'bottom'
		});
	} else {
		var rb = api.require('runBackground');
		rb.hideActivity();
	}
});

```

##补充说明

注册应用

##可用性

Android系统

可提供的1.0.0及更高版本

