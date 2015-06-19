/*
Title: 前端框架开发指南
Description: 前端框架开发指南
Sort: 6
*/

<div class="outline">
[.trim()](#1)

[.trimAll()](#2)

[.isArray()](#3)

[.addEvt()](#4)

[.rmEvt()](#5)

[.one()](#6)

[.dom()](#7)

[.domAll()](#8)

[.byId()](#9)

[.first()](#10)

[.last()](#11)

[.eq()](#12)

[.not()](#13)

[.prev()](#14)

[.next()](#15)

[.contains()](#16)

[.closest()](#17)

[.remove()](#18)

[.attr()](#19)

[.removeAttr()](#20)

[.hasCls()](#21)

[.addCls()](#22)

[.removeCls()](#23)

[.toggleCls()](#24)

[.val()](#25)

[.prepend()](#26)

[.append()](#27)

[.before()](#28)

[.after()](#29)

[.html()](#30)

[.text()](#31)

[.offset()](#32)

[.css()](#33)

[.cssVal()](#34)

[.jsonToStr()](#35)

[.strToJson()](#36)

[.setStorage()](#37)

[.getStorage()](#38)

[.rmStorage()](#39)

[.clearStorage()](#40)

[.fixIos7Bar()](#41)

[.fixStatusBar()](#45)

[.toast()](#42)

[.get()](#43)

[.post()](#44)
</div>

#**CSS Framework**

- 清除浏览器默认样式（借鉴CSS Reset，Normalize.css）
- 禁用系统长按菜单（-webkit-touch-callout:none）
- 禁用字体大小自动调整（-webkit-text-size-adjust:none）
- 去掉点击高亮（-webkit-tap-highlight-color:rgba(0, 0, 0, 0)）
- 禁止选择内容（-webkit-user-select:none）
- 清除浮动（.clearfix）
- 加载更多默认样式（.loading_more）

#**JavaScript Framework**

命名空间为 **$api** ，所有方法如下：

##.trim()<div id="1"></div>

- 描述：去掉字符串首尾空格
- 用法：trim(str)
- 参数：	str (类型：String) 
- 返回值：去除首尾空格的字符串
- 示例：	
```js
$api.trim('   abc  123   ');  // => "abc  123"
```

##.trimAll()<div id="2"></div>

- 描述：去掉字符串所有空格
- 用法：trimAll(str)
- 参数：str (类型：String)
- 返回值：去除所有空格的字符串
- 示例：
```js
$api.trimAll('  abc 123  ');  // => "abc123"
```

##.isArray()<div id="3"></div>

- 描述：判断对象是否为数组
- 用法：.isArray(obj)
- 参数：	obj (类型：Object)
- 返回值：Boolean
- 示例：
```js
$api.isArray([1,2,3]);  // => true
$api.isArray('123')  // => false
```

##.addEvt()<div id="4"></div>

- 描述：为DOM元素绑定事件
- 用法：.addEvt(el, name, fn, useCapture)
- 参数：

	el (类型：Element)：DOM元素

	name (类型：String)：事件类型

	fn (类型：Function)：事件回调

	useCapture (类型：Boolean)：事件捕获，默认为 false

- 示例：
```js	
$api.addEvt(element, 'click', function(){
  //do something
});
```

##.rmEvt()<div id="5"></div>

- 描述：移除DOM元素绑定的事件
- 用法：.rmEvt(el, name, fn, useCapture)
- 参数：
	
	el (类型：Element)：DOM元素

	name (类型：String)：事件类型

	fn (类型：Function)：事件回调

	useCapture (类型：Boolean)：事件捕获，默认为 false

- 示例：	
```js
$api.rmEvt(element, 'click', function(){
  //do something
});
```

##.one()<div id="6"></div>
- 描述：为DOM元素绑定事件，事件只执行一次
- 用法：.one(el, name, fn, useCapture)
- 参数：

	el (类型：Element)：DOM元素

	name (类型：String)：事件类型

	fn (类型：Function)：事件回调

	useCapture (类型：Boolean)：事件捕获，默认为 false

- 示例：	
```js
$api.one(element, 'click', function(){
  //do something
});
```

##.dom()<div id="7"></div>

- 描述：选择首个匹配的DOM元素
- 用法：

	.dom(el, selector)

	从el元素开始查找

- 参数：	
	el (类型：Element)：DOM元素

	selector (类型：Selector)：CSS 选择器

- 返回值：	返回首个匹配的DOM元素
- 示例：
```js
$api.dom(el, '#id');
$api.dom(el, '.list[type="text"]');
```
.dom(selector)

	从document元素开始查找

- 参数：	selector (类型：Selector)：CSS 选择器
- 返回值：返回首个匹配的DOM元素
- 示例：
```js
$api.dom('#id');
$api.dom('.list[type="text"]');
```


##.domAll()<div id="8"></div>
- 描述：选择所有匹配的DOM元素
- 用法：

	.domAll(el, selector)

	从el元素开始查找

- 参数：	

	el (类型：Element)：DOM元素

	selector (类型：Selector)：CSS 选择器

- 返回值：	返回所有匹配的DOM元素
- 示例：	
```js
$api.domAll(el, '.class');
$api.domAll(el, '.list:fist-child');
```
.domAll(selector)

	从document元素开始查找

- 参数：	selector (类型：Selector)：CSS 选择器
- 返回值：返回所有匹配的DOM元素
- 示例：
```js
$api.domAll('.class');
$api.domAll('.list:fist-child');
```


##.byId()<div id="9"></div>
- 描述：通过Id选择DOM元素
- 用法：.byId(id)
- 参数：	id(类型：String)：CSS id 字符串
- 返回值：	返回匹配的DOM元素
- 示例：
```js
$api.byId('idStr')
```

##.first()<div id="10"></div>
- 描述：选择DOM元素的第一个子元素
- 用法：.first(el, selector)
- 参数：	
	
	el (类型：Element)：DOM元素

	selector (类型：Selector)：CSS 选择器

- 返回值：	返回DOM元素的第一个子元素
- 示例：	
```js
$api.first(el,'li');
```
.first(el)
- 参数：el (类型：Element)：DOM元素
- 返回值：返回DOM元素的第一个子元素
- 示例：
```js
$api.first(el);
```

##.last()<div id="11"></div>
- 描述：选择DOM元素的最后一个子元素
- 用法：.last(el, selector)
- 参数：	

	el (类型：Element)：DOM元素

	selector (类型：Selector)：CSS 选择器

- 返回值：	返回DOM元素的最后一个子元素
- 示例：
```js
$api.last(el,'li');
```
.last(el)
- 参数：	el (类型：Element)：DOM元素
- 返回值：返回DOM元素的最后一个子元素
- 示例：
```js
$api.last(el);
```


##.eq()<div id="12"></div>
- 描述：选择第几个子元素
- 用法：.eq(el, index)
- 参数：

	el (类型：Element)：DOM元素

	index (类型：String | Number)：索引值

- 返回值：根据索引值返回子元素
- 示例：
```js
$api.eq(el, 2);
$api.eq(el, '2');
```

##.not()<div id="13"></div>
- 描述：根据排除选择器选择子元素
- 用法：.not(el, selector)
- 参数：

	el (类型：Element)：DOM元素

	selector (类型：Selector)：CSS 选择器

- 返回值：返回不匹配选择器的所有子元素
- 示例：
```js
$api.not(el, '.active');
```


##.prev()<div id="14"></div>
- 描述：选择相邻的前一个元素
- 用法：.prev(el)
- 参数：el (类型：Element)：DOM元素
- 返回值：返回前一个元素
- 示例：
```js
$api.prev(el);
```


##.next()<div id="15"></div>
- 描述：选择相邻的下一个元素
- 用法：.next(el)
- 参数：el (类型：Element)：DOM元素
- 返回值：返回下一个元素
- 示例：
```js
$api.next(el);
```


##.contains()<div id="16"></div>
- 描述：判断某一个元素是否包含目标元素
- 用法：.contains(parentEl, targetEl)
- 参数：

	parentEl (类型：Element)：DOM元素

	targetEl (类型：Element)：DOM元素

- 返回值：返回布尔值（true 或 false）
- 示例：
```js
$api.contains(parentEl, targetEl);
```

##.closest()<div id="17"></div>
- 描述：根据选择器匹配最近的父元素
- 用法：.closest(el, selector)
- 参数：

	el (类型：Element)：DOM元素

	selector (类型：Selector)：CSS 选择器

- 返回值：根据选择器匹配最近的父元素
- 示例：
```js
$api.closest(el, '.parent');
```


##.remove()<div id="18"></div>
- 描述：移除DOM元素
- 用法：.remove(el)
- 参数：el (类型：Element)：DOM元素
- 示例：
```js
$api.remove(el);
```

##.attr()<div id="19"></div>
- 描述：获取或设置DOM元素的属性
- 用法：.attr(el, name, value)

	设置属性值

- 参数：

	el (类型：Element)：DOM元素

	name (类型：String)：属性名

	value (类型：String)：属性值

- 返回值：	返回当前DOM元素
- 示例：
```js
$api.attr(el,'data','123');
```
.attr(el, name)

	获取属性值
- 参数：

	el (类型：Element)：DOM元素

	name (类型：String)：属性名

- 返回值：返回属性值
- 示例：
```js
$api.attr(el,'data');
```

##.removeAttr()<div id="20"></div>
- 描述：移除DOM元素的属性
- 用法：.removeAttr(el, name)
- 参数：

	el (类型：Element)：DOM元素

	name (类型：String)：属性名

- 示例：
```js
$api.removeAttr(el, 'data')
```

##.hasCls()<div id="21"></div>
- 描述：DOM元素是否含有某个className
- 用法：.hasCls(el, cls)
- 参数：

	el (类型：Element)：DOM元素

	cls (类型：String)：className

- 返回值：Boolean
- 示例：
```js
$api.hasCls(el, 'classname'); // => true
```

##.addCls()<div id="22"></div>
- 描述：为DOM元素增加className
- 用法：.addCls(el, cls)
- 参数：

	el (类型：Element)：DOM元素

	cls (类型：String)：className

- 返回值：返回当前DOM元素
- 示例：
```js
$api.addCls(el, 'newclass'); 
```


##.removeCls()<div id="23"></div>
- 描述：移除指定的className
- 用法：.removeCls(el, cls)
- 参数：

	el (类型：Element)：DOM元素

	cls (类型：String)：className

- 返回值：返回当前DOM元素
- 示例：
```js
$api.removeCls(el, 'newclass'); 
```


##.toggleCls()<div id="24"></div>
- 描述：切换指定的className
- 用法：.toggleCls(el, cls)
- 参数：

	el (类型：Element)：DOM元素

	cls (类型：String)：className

- 返回值：返回当前DOM元素
- 示例：
```js
$api.toggleCls(el, 'display'); 
```

##.val()<div id="25"></div>
- 描述：获取或设置常用 Form 表单元素的 value 值
- 用法：.val(el, val)

	设置表单元素value值

- 参数：

	el (类型：Element)：DOM元素

	val (类型：String)：想设置的value值

- 返回值：返回当前DOM元素
- 示例：
```js
$api.val(el,'123'); 
```
.val(el)

	获取表单元素value值

- 参数：el (类型：Element)：DOM元素
- 返回值：返回表单元素的value值
- 示例：
```js
$api.val(el); 
```


##.prepend()<div id="26"></div>
- 描述：在DOM元素内部，首个子元素前插入HTML字符串
- 用法：.prepend(el, html)
- 参数：

	el (类型：Element)：DOM元素

	html (类型：htmlString)：HTML字符串

- 返回值：返回当前DOM元素
- 示例：
```js
$api.prepend(el,'<li>hello</li>'); 
```

##.append()<div id="27"></div>
- 描述：在DOM元素内部，最后一个子元素后面插入HTML字符串
- 用法：.append(el, html)
- 参数：

	el (类型：Element)：DOM元素

	html (类型：htmlString)：HTML字符串

- 返回值：返回当前DOM元素
- 示例：
```js
$api.append(el,'<li>hello</li>'); 
```

##.before()<div id="28"></div>
- 描述：在DOM元素前面插入HTML字符串
- 用法：.before(el, html)
- 参数：

	el (类型：Element)：DOM元素

	html (类型：htmlString)：HTML字符串

- 返回值：返回当前DOM元素
- 示例：
```js
$api.before(el,'<h1>world</h1>'); 
```

##.after()<div id="29"></div>
- 描述：在DOM元素后面插入HTML字符串
- 用法：.after(el, html)
- 参数：

	el (类型：Element)：DOM元素

	html (类型：htmlString)：HTML字符串

- 返回值：返回当前DOM元素
- 示例：
```js
$api.after(el,'<h1>world</h1>'); 
```


##.html()<div id="30"></div>
- 描述：获取或设置DOM元素的innerHTML
- 用法：.html(el, html)

	设置innerHTML

- 参数：

	el (类型：Element)：DOM元素

	html (类型：htmlString)：HTML字符串

- 返回值：返回当前DOM元素
- 示例：
```js
$api.html(el,'<h1>world</h1>'); 
```
.html(el)

	获取innerHTML

- 参数：el (类型：Element)：DOM元素
- 返回值：返回当前DOM元素的innerHTML
- 示例：
```js
$api.html(el); 
```

##.text()<div id="31"></div>
- 描述：设置或者获取元素的文本内容
- 用法：. text (el, txt)
- 参数：

	el(类型：Element)：DOM元素

	txt(类型：String)：字符串

- 返回值：当前DOM元素
- 示例：
```js
var a = document.getElementById('a');
$api.text(a, 'text'); // => <a id=''a''>text</a>
```
	. text (el)
- 参数：el(类型：Element)：DOM元素
- 返回值：DOM元素的文本内容
- 示例：
```js
<a id=''a''>text</a>
var a = document.getElementById('a');
$api.text(a); // => text
```


##.offset()<div id="32"></div>
- 描述：获取元素在页面中的位置与宽高，(此为距离页面左侧及顶端的位置，并非距离窗口的位置)
- 用法：. offset (el)
- 参数：el(类型：Element)：DOM元素
- 返回值：该元素的位置（left,top）及宽高（width,height）,返回值是json类型的，包括l,t,w,h属性
- 示例：
```js
var offset = $api.offset(el);
var left = offset.l;
var top = offset.t;
var width = offset.w;
var height = offset.h;
```


##.css()<div id="33"></div>
- 描述：设置所传入的DOM元素的样式，可传入多条样式
- 用法：.css (el, css)
- 参数：

	el(类型：Element)：DOM元素

	css(类型：String)：想要设置的CSS样式

- 示例：
```js
$api.css(el,'width:800px;border:1px solid red');
```

##.cssVal()<div id="34"></div>
- 描述：获取指定DOM元素的指定属性的完整的值，如800px
- 用法：. cssVal (el, prop)
- 参数：

	el(类型：Element)：DOM元素

	prop(类型：String)：CSS属性

- 返回值：完整的CSS属性值
- 示例：
```js
$api.cssVal(el,'width'); // => 800px
```


##.jsonToStr()<div id="35"></div>
- 描述：将标准的JSON 对象转换成字符串格式
- 用法：. jsonToStr (json)
- 参数：json(类型：JSON)
- 返回值：转换后的字符串
- 示例：
```js
var json = {a:111, b:222};
$api.jsonToStr(json); // => "{"a":111,"b":222}"
```

##. strToJson ()<div id="36"></div>
- 描述：将JSON字符串转换成JSON对象
- 用法：. strToJson (str)
- 参数：str(类型：String)：JSON字符串
- 返回值：JSON对象
- 示例：
```js
var a = '{"a":"111", "b":"222"}';
$api.strToJson(a); // => Object {a: "111", b: "222"}
```

##.setStorage()<div id="37"></div>
- 描述：设置localStorage数据
- 用法：. setStorage (key,value)
- 参数：

	key(类型：String)：键名

	value(类型：任意类型)：值

- 示例：	
```js
$api.setStorage('name','Tom');
```

##.getStorage()<div id="38"></div>
- 描述：获取localStorage数据，**必须与$api.setStorage()配套使用**
- 用法：. getStorage(key)
- 参数：key(类型：String)：键名
- 返回值：localStorage中与键名对应的值
- 示例：
```js
$api.getStorage('name'); // => "Tom"
```

##.rmStorage()<div id="39"></div>
- 描述：清除localStorage中与键名对应的值
- 用法：. rmStorage(key)
- 参数：key(类型：String)：键名
- 示例：
```js
$api.rmStorage('name')
```


##.clearStorage ()<div id="40"></div>
- 描述：清除localStorage的所有数据，慎用
- 用法：. clearStorage ()
- 示例：
```js
$api.clearStorage ();
```

##.fixIos7Bar()<div id="41"></div>
- 描述：适配iOS7+系统状态栏，为传入的DOM元素增加20px的上内边距
- 用法：.fixIos7Bar(el)
- 参数：el (类型：Element) ： DOM元素
- 备注：自动识别iOS7+，避免应用与状态栏重叠，无法跟config.xml里面的<preference name="iOS7StatusBarAppearance" value="false" />一起使用。
- 示例：
```js
var header = document.querySelector('#header');
$api.fixIos7Bar(header);
```

##.fixStatusBar()<div id="45"></div>
- 描述：适配iOS7+、Android4.4+系统状态栏，为传入的DOM元素增加适当的上内边距，避免header与状态栏重叠
- 用法：.fixStatusBar(el)
- 参数：el (类型：Element) ： DOM元素
- 备注：自动识别iOS7+，避免应用与状态栏重叠，无法跟config.xml里面的<preference name="iOS7StatusBarAppearance" value="false" />一起使用。
- 示例：
```js
var header = document.querySelector('#header');
$api.fixStatusBar(header);
```

##.toast()<div id="42"></div>
- 描述：延时提示框
- 用法：.toast(title,text,time)
- 参数：

	title (类型：String) ： 标题(可选参数)

	text(类型：String)：内容(可选参数)

	time(类型：Number)：延时的时间(可选参数),单位为毫秒，默认值为500

- 示例：
```js
$api.toast('你好啊');
$api.toast(2000);
$api.toast('你好啊',2000);
$api.toast('你好啊','hello');
$api.toast('演示','延时提示框',1000);
```


##.get()<div id="43"></div>
- 描述：api.ajax()方法的get方式简写
- 用法：.get(url,fnSuc,dataType)
- 参数：

	url (类型：String) :  url(必传参数)

	fnSuc (类型：Function)：成功回调函数(可选参数)

	dataType(类型：String)：返回值的类型(可选参数)，有text与json两种类型，默认为json

- 返回值：根据dataType在成功回调函数里返回相应数据
- 示例：
```js
$api.get('http://www.pm25.in/api/querys/pm2_5.json?city=beijing&token=5j1znBVAsnSf5xQyNQyq',function(ret){
	alert(ret);
},'text');
```

##.post()<div id="44"></div>
- 描述：api.ajax()方法的post方式简写
- 用法：.post(url,data,fnSuc,dataType)
- 参数：

	url (类型：String) ：url(必传参数)

	data(类型：JSON):  可以有body：请求体（字符串类型）values：post参数（JSON对象）

	files：post文件（JSON对象）等参数(可选参数)

	fnSuc (类型：Function)：成功回调函数(可选参数)

	dataType(类型：String)：返回值的类型(可选参数)，有text与json两种类型，默认为json

- 返回值：向url地址发送ajax请求，并发送数据data，根据dataType在成功回调函数返回相应数据
- 示例：	
```js
$api.post('http://192.168.1.233:4321/getString',{
    body: 'String'
},function(ret){
    alert(ret);
},'text');
```
