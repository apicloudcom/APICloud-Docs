/*
Title: TV框架开发指南
Description: 基于 JavaScript 的 TV 框架开发指南
Sort: 6
*/

#**准备工作**

##必须定义的 CSS 样式
**如果不指定这两个样式，用户操作时无法收到反馈，极影响用户体验**

* `.focus{}` 是按下遥控器方向键，焦点移入某元素的样式
* `.active{}` 是按下遥控器确定键，当前元素的样式

##必须定义的 HTML 属性

`tabindex`，给能够获取焦点的 HTML 元素加此属性，当前不支持元素嵌套

1.自动排序：程序根据元素的位置，自动寻找下一个焦点元素

```html
<div tabindex>元素1</div>
<div tabindex>元素2</div>
<div tabindex>元素3</div>
```

2.指定排序：程序按照 `tabindex` 的值大小，寻找下一个焦点元素，`tabindex` 的值必须是正整数

```html
<div tabindex="1">元素1</div>
<div tabindex="2">元素2</div>
<div tabindex="3">元素3</div>
```

##名词解释

* 焦点元素：能够获取焦点的元素，也就是带有 `tabindex` 属性的元素
* scope容器：每个页面需要规定一个元素作为容器，容器内所有带有 `tabindex` 属性的元素，按下遥控器上、下、左、右时可以获取焦点，**每个页面只能有一个scope容器**

#**框架使用**

不需要额外引入 JS 文件，直接在 apiready 函数中初始化。

```js
<script type="text/javascript">
apiready = function(){
	var tv = new TV();
    tv.init({
        scope: '#menu',
        firstFocus: true
    });
};
</script>
```

#方法

<div class="outline">
[.init(options)](#m1)

[.refresh()](#m2)

[api.requestFocus()](#m3)
</div>

<div id="m1"></div>
##.init(options)

- 描述：TV框架初始化
- 用法：init(options)
- 参数：options (类型：Object)
- 示例：	
```js
var tv = new TV();
tv.init({
	scope: '#menu',
    firstFocus: true
});
```

###options 参数详解

```js
{
	scope: '#id',	//必传参数，类型：CSS 选择器，建议传 id 选择器。scope 是页面内可以获取焦点的所有元素的最外层容器，一个页面只能有一个容器。
	sortByTabIndex: false,	//可选参数，类型：Boolean，默认值：false。是否按 tabindex 值大小寻找元素
	firstFocus: false,	//可选参数，类型：Boolean，默认值：false。首个焦点元素是否需要样式
	lastFocus: false,	//可选参数，类型：Boolean，默认值：false。是否记录最后一个焦点元素的状态，适用场景：TAB 标签切换，内容区域的焦点需要记录
	focusIn: function(focused){},	//可选参数，类型：Function，focused：Boolean 型。当前的 Frame 或 Window 获取焦点时触发
	focusOut: function(focused){}, 	//可选参数，类型：Function，focused：Boolean 型。当前的 Frame 或 Window 失去焦点时触发
	focus: function(){},	//可选参数，类型：Function。某个元素获取焦点时触发
	active: function(){},	//可选参数，类型：Function。在某个元素上按下遥控器确认键时触发
	up: function(curEl,targetEl){},		//可选参数，类型：Function。curEl：当前元素，targetEl：下一个可获取焦点的元素。按下遥控器上键时触发
	down: function(curEl,targetEl){},	//可选参数，类型：Function，参数同 up 。按下遥控器下键时触发
	left: function(curEl,targetEl){},	//可选参数，类型：Function，参数同 up 。按下遥控器左键时触发
	right: function(curEl,targetEl){},	//可选参数，类型：Function，参数同 up 。按下遥控器右键时触发
	topmost: function(){},		//可选参数，类型：Function。到达最顶部焦点元素时触发
	bottommost: function(){},	//可选参数，类型：Function。到达最底部焦点元素时触发
	leftmost: function(){},		//可选参数，类型：Function。到达最左侧焦点元素时触发
	rightmost: function(){},	//可选参数，类型：Function。到达最右侧焦点元素时触发
	reachScopeTop: function(targetEl){},	//可选参数，类型：Function，targetEl：下一个可获取焦点的元素。到达scope容器的最顶部时触发
	reachScopeBottom: function(targetEl){},		//可选参数，类型：Function，targetEl：下一个可获取焦点的元素。到达scope容器的最底部时触发
	reachScopeLeft: function(targetEl, viewportPos){},		//可选参数，类型：Function，targetEl：下一个可获取焦点的元素，viewportPos：scope容器元素。到达scope容器的最左侧时触发
	reachScopeRight: function(targetEl, viewportPos){},		//可选参数，类型：Function，targetEl：下一个可获取焦点的元素，viewportPos：scope容器元素。到达scope容器的最右侧时触发
}
```

###焦点元素

上面方法中的 `curEl`，`targetEl` 参数均为焦点元素对象，类型：Object，它们带有一些属性

```js
{
	'uz-element-id': 'eid-0',	//每个可获取焦点的元素均会有一个唯一的元素id，框架自动分配，可通过此属性找到元素。示例：<div tabindex uz-element-id="eid-1"></div>
    'element': Element,		//DOM 元素引用
    'x': 0,		//DOM 元素左上角的 x 轴坐标
    'y': 0,		//DOM 元素左上角的 y 轴坐标
    'w': 100,	//DOM 元素的宽度
    'h': 100	//DOM 元素的高度
}
```

###可视区域元素

上面方法中的 `viewportPos` 代表可视区域对象，类型：Object，根据 `element.getBoundingClientRect()` 算出的属性值

```js
{
	top: 0,			//元素距离可视区域顶部的距离
	bottom: 3077,	//元素距离可视区域底部的距离
	left: 0,		//元素距离可视区域左侧的距离
	right: 1349		//元素距离可视区域右侧的距离
}
```

<div id="m2"></div>
##.refresh()

- 描述：页面布局结构或样式改变，以及AJAX请求的新数据插入页面时，重新计算焦点元素
- 用法：refresh()
- 示例：
```js
var tv = new TV();
tv.refresh();
```

<div id="m3"></div>
##api.requestFocus({params})

- 描述：强制将焦点切换到某个 frame 或者 window
- params 参数：

    name：frame的名字，为空或不传则默认为调用该接口的 frame 或 window， 类型：字符型，默认值：空
- 示例：
```js
apiready = function(){
    api.requestFocus({
        name: 'name'
    });
};
```

