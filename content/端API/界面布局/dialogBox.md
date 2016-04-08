/*
Title: dialogBox
Description: dialogBox
*/
<div class="outline">
[alert](#m1)

[sendMessage](m2)

[scene](#m3)

[evaluation](#m4)

[raffle](#m5)

[remind](#m6)

[dayNote](#m7)

[taskPlan](#m8)

[confirm](#m9)

[receiveMessage](#m10)

[activity](#m11)

[tips](#m12)

[discount](#m13)

[share](#m14)

</div>

#**概述**

dialogBox 封装了 14 种款式的对话框，每一种款式都有一个接口来调用，开发者可按照各个接口的样式来自定义对话框上的文字、图片、图文等。每一种样式图展示如下，开发者可参考配置：

alert 样式如下图所示：

![alert](/img/docImage/dialogBox/styleLogin_1.png)
![alert](/img/docImage/dialogBox/styleLogin_2.png)
![alert](/img/docImage/dialogBox/styleLogin_3.png)
![alert](/img/docImage/dialogBox/styleLogin_4.png)

sendMessage 样式如下图所示：

![sendMessage](/img/docImage/dialogBox/styleLogin_5.png)

scene 样式如下图所示：

![scene](/img/docImage/dialogBox/styleScene_1.png)
![scene](/img/docImage/dialogBox/styleSceneResult_1.png)
![scene](/img/docImage/dialogBox/styleSceneResult_2.png)

evaluation 样式如下图所示：

![evaluation](/img/docImage/dialogBox/styleEvaluation_1.png)

raffle 样式如下图所示：

![raffle](/img/docImage/dialogBox/styleRaffle_1.png)
![raffle](/img/docImage/dialogBox/styleRaffle_2.png)
![raffle](/img/docImage/dialogBox/styleRaffle_3.png)
![raffle](/img/docImage/dialogBox/styleRaffle_4.png)
![raffle](/img/docImage/dialogBox/styleRaffle_5.png)

remind 样式如下图所示：

![remind](/img/docImage/dialogBox/styleRemind_1.png)
![remind](/img/docImage/dialogBox/styleRemind_2.png)
![remind](/img/docImage/dialogBox/styleRemind_3.png)
![remind](/img/docImage/dialogBox/styleRemind_4.png)

dayNote 样式如下图所示：

![dayNote](/img/docImage/dialogBox/styleDayNote_1.png)

taskPlan 样式如下图所示：

![taskPlan](/img/docImage/dialogBox/styleTaskPlan_1.png)

confirm 样式如下图所示：

![confirm](/img/docImage/dialogBox/styleQA_1.png)

receiveMessage 样式如下图所示：

![receipt](/img/docImage/dialogBox/styleReceipt_1.png)

activity 样式如下图所示：

![activity](/img/docImage/dialogBox/styleActivity_1.png)
![activity](/img/docImage/dialogBox/styleActivity_2.png)

tips 样式如下图所示：

![tips](/img/docImage/dialogBox/styleTips_1.png)

discount 样式如下图所示：

![discount](/img/docImage/dialogBox/styleDiscount_1.png)

share 样式如下图所示：

![share](/img/docImage/dialogBox/styleShare_1.png)

##**模块接口**

<div id="m1"></div>
#**alert**

弹出 alert 样式的对话框

alert ({params}, callback(ret))

##params

texts：

- 类型：JSON 对象
- 描述：（可选项）alert 对话框模块可配置的文本
- 内部字段：

```js
{
	title: '确认',          //（可选项）字符串类型：标题内容，若不传则不显示
	content:'',            //（可选项）字符串类型：对话框文本内容，若不传则不显示
	leftBtnTitle: '取消',   //（可选项）字符串类型；左边按钮标题，若不传则不显示
	rightBtnTitle: '确认'   //（可选项）字符串类型；右边按钮标题，若不传则不显示
}
```

styles:

- 类型：JSON 对象
- 描述：alert 对话框样式配置
- 内部字段：

```js
{
	bg: '#fff',            //（可选项）字符串类型；对话框整体背景配置，支持#、rgb、rgba、img；默认：#fff
	w: 300,                //（可选项）数字类型；对话框的宽；默认：300
	h: 400,                //（可选项）数字类型；对话框的高；默认：400
	title:{                //（可选项）JSON对象；弹窗的 title 样式配置，不传则不显示标题
		marginT: '20',     //（可选项）数字类型；标题栏与对话框顶部的距离；默认：20
		icon: ,            //（可选项）字符串类型；标题前面的图标路径，要求本地路径（widget://、fs://）；图片为正方形的，如：50*50、100*100，建议开发者传大小合适的图片以适配高分辨率手机屏幕，不传则不显示
		iconSize: 40,      //（可选项）数字类型；icon 图标边长大小；默认：24
		titleSize: 14,     //（可选项）数字类型；标题字体大小；默认：14
		titleColor: '#fff',//（可选项）字符串类型；标题字体颜色，支持#、rgb、rgba；默认：#fff
	},
	content:{              //（可选项）JSON 对象；文本内容配置，若不传则不显示
		marginT: '20',     //（可选项）数字类型；内容文本距离标题栏底部的距离，如果标题栏不存在，则是到窗口顶部的距离；默认：20
		marginL: '20',     //（可选项）数字类型；内容文本距离对话框左边的距离；默认：20
		color: '#eee',     //（可选项）字符串类型；内容文本字体颜色，支持 rgb、rgba、#；默认：#eee
		size: 10,          //（可选项）数字类型：内容文本字体大小；默认：10
	},
	left:{                 //（可选项）JSON 对象；左边按钮样式配置，不传则不显示左边按钮
		marginB: 7,        //（可选项）数字类型；左边按钮的下边距；默认：7
		marginL: 18,       //（可选项）数字类型；左边按钮的左边距；默认：18
		w: 90,             //（可选项）数字类型；左边按钮的宽；默认：90
		h: 35,             //（可选项）数字类型；左边按钮的高；默认：35
		corner: 2,         //（可选项）数字类型；左边按钮圆角半径；默认：0.0
		bg: '#fff',        //（可选项）字符串类型；左边按钮的背景，支持rgb、rgba、#、img；默认：'#fff'
		color: '#007FFF',  //（可选项）字符串类型；左边按钮标题字体颜色，支持rgb，rgba、#；默认：'#007FFF'
		size: 12           //（可选项）数字类型；左边按钮标题字体大小；默认：12
	},
	right: {               //（可选项）JSON 对象；右边按钮样式配置，不传则不显示右边按钮
		marginB: 7,        //（可选项）数字类型；右边按钮的下边距；默认：7
		marginL: 18,       //（可选项）数字类型；右边按钮的左边距；默认：18
		w: 90,             //（可选项）数字类型；右边按钮的宽；默认：90
		h: 35,             //（可选项）数字类型；右边按钮的高；默认：35
		corner: 2,         //（可选项）数字类型；右边按钮圆角半径；默认：0.0
		bg: '#fff',        //（可选项）字符串类型；右边按钮的背景，支持rgb、rgba、#、img；默认：'#fff'
		color: '#007FFF',  //（可选项）字符串类型；右边按钮标题字体颜色，支持rgb、rgba、#；默认：'#007FFF'
		size: 12           //（可选项）数字类型；右边按钮标题字体大小；默认：12
	}
}
```
##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	eventType: 'left',        //字符串类型；交互事件类型，取值范围如下：
                              // left（表示用户点击了左边按钮）
                              // right（表示用户点击了右边按钮）
}
```

##示例代码

```js
var dialogBox = api.require('dialogBox');
dialogBox.alert ({
	texts: {
		title: '确认',          
		content:'送你一个超级礼包，内有超值福利，先到先得，点击领取 >>',           
		leftBtnTitle: '取消',   
		rightBtnTitle: '确认' 
	}
	styles:{
		title:{   
			icon: 'widget://image/chatBox.png',  
			size: 14,      
			color: '#fff'    
		},
		content:{  
			color: '#eee',     	
			size: 10  		
		},
		ok:{            
			marginB: 7,      
			marginL: 10,     
		    w: 90,           
		    h: 35,
		    corner: 2,       
		    bg: '#fff',   
		    size: 12    
		},
		cancel:{            
			marginB: 7,      
			marginL: 100,      
		    w: 90,           
		    h: 35,
		    corner: 2,       
		    bg: '#e0e',   
		    size: 12    
		}
	}
},function(ret){
    api.alert({msg:JSON.stringify(ret)});
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m2"></div>
#**sendMessage**

弹出 sendMessage 样式的对话框

sendMessage ({params}, callback(ret))

##params

texts：

- 类型：JSON 对象
- 描述：（可选项）sendMessage 对话框模块可配置的文本
- 内部字段：

```js
{
	title: '昵称',          //（可选项）字符串类型：标题栏显示文本内容，若不传则不显示
	inputText: '',         //（可选项）字符串类型；标题栏输入框默认文本，若不传则不显示
	content:'',            //（可选项）字符串类型：对话框文本内容，若不传则不显示
	leftBtnTitle: '取消',   //（可选项）字符串类型；左边按钮标题，若不传则不显示
	rightBtnTitle: '发送'   //（可选项）字符串类型；右边按钮标题，若不传则不显示
}
```

styles:

- 类型：JSON 对象
- 描述：sendMessage 对话框样式配置
- 内部字段：

```js
{
	bg: '#fff',                 //（可选项）字符串类型；对话框整体背景配置，支持#、rgb、rgba、img；默认：#fff
	w: 300,                     //（可选项）数字类型；对话框的宽；默认：300
	h: 400,                     //（可选项）数字类型；对话框的高；默认：400
	title:{                     //（可选项）JSON 对象；弹窗的 title 样式配置，不传则不显示标题
		h: '60',                //（可选项）数字类型；标题栏高度；默认：60
		show: {                 //（可选项）JSON 对象；标题栏显示文字样式配置
			marginL: 6,         //（可选项）数字类型；显示文本相对于标题栏左边的距离；默认：6
			titleSize: 14,      //（可选项）数字类型；标题字体大小；默认：14
			titleColor: '#fff'  //（可选项）字符串类型；标题字体颜色，支持#、rgb、rgba；默认：#fff
		},
		input:{                 //（可选项）JSON 对象；标题栏输入文本框样式配置
			marginL: 6,         //（可选项）数字类型；输入文本框相对于显示文本的距离，若显示文本不存在，则是与标题栏左边的距离；默认：6
			textSize: 14,       //（可选项）数字类型；输入文本框文本字体大小；默认：14
			textColor: '#fff'   //（可选项）字符串类型；输入文本框文本字体颜色，支持#、rgb、rgba；默认：#fff
		}
	},
	content:{                   //（可选项）JSON 对象；文本内容配置，若不传则不显示
		marginT: '20',          //（可选项）数字类型；内容文本距离标题栏底部的距离，如果标题栏不存在，则是到窗口顶部的距离；默认：20
		marginL: '20',          //（可选项）数字类型；内容文本距离对话框左边的距离；默认：20
		color: '#eee',          //（可选项）字符串类型；内容文本字体颜色，支持 rgb、rgba、#；默认：#eee
		size: 10                //（可选项）数字类型：内容文本字体大小；默认：10
	},
	left:{                      //（可选项）JSON 对象；左边按钮样式配置，不传则不显示左边按钮
		marginB: 7,             //（可选项）数字类型；左边按钮的下边距；默认：7
		marginL: 18,            //（可选项）数字类型；左边按钮的左边距；默认：18
		w: 90,                  //（可选项）数字类型；左边按钮的宽；默认：90
		h: 35,                  //（可选项）数字类型；左边按钮的高；默认：35
		corner: 2,              //（可选项）数字类型；左边按钮圆角半径；默认：0.0
		bg: '#fff',             //（可选项）字符串类型；左边按钮的背景，支持rgb、rgba、#、img；默认：'#fff'
		color: '#007FFF',       //（可选项）字符串类型；左边按钮标题字体颜色，支持rgb，rgba、#；默认：'#007FFF'
		size: 12                //（可选项）数字类型；左边按钮标题字体大小；默认：12
	},
	right: {                    //（可选项）JSON 对象；右边按钮样式配置，不传则不显示右边按钮
		marginB: 7,             //（可选项）数字类型；右边按钮的下边距；默认：7
		marginL: 18,            //（可选项）数字类型；右边按钮的左边距；默认：18
		w: 90,                  //（可选项）数字类型；右边按钮的宽；默认：90
		h: 35,                  //（可选项）数字类型；右边按钮的高；默认：35
		corner: 2,              //（可选项）数字类型；右边按钮圆角半径；默认：0.0
		bg: '#fff',             //（可选项）字符串类型；右边按钮的背景，支持rgb、rgba、#、img；默认：'#fff'
		color: '#007FFF',       //（可选项）字符串类型；右边按钮标题字体颜色，支持rgb、rgba、#；默认：'#007FFF'
		size: 12                //（可选项）数字类型；右边按钮标题字体大小；默认：12
	}
}
```
##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	eventType: 'left',        //字符串类型；交互事件类型，取值范围如下：
                              // left（表示用户点击了左边按钮）
                              // right（表示用户点击了右边按钮）
}
```

##示例代码

```js
var dialogBox = api.require('dialogBox');
dialogBox. sendMessage ({
	texts: {
		title: '你的昵称',
		inputText: '（点击此处修改昵称）',          
		content:'亲，从你一个80元大礼包，请查收！退订请回复TD',           
		leftBtnTitle: '取消',   
		rightBtnTitle: '发送' 
	}
	styles:{
		title:{                     
			h: '60',                
			show: { 
				marginL: 6,
				titleSize: 14,
				titleColor: '#fff'
			},
			input:{                
				marginL: 6,         
				textSize: 14, 
				textColor: '#fff'
			}
		},
		content:{  
			color: '#eee',     	
			size: 10  		
		},
		ok:{            
			marginB: 7,      
			marginL: 10,     
		    w: 90,           
		    h: 35,
		    corner: 2,       
		    bg: '#fff',   
		    size: 12    
		},
		cancel:{            
			marginB: 7,      
			marginL: 100,      
		    w: 90,           
		    h: 35,
		    corner: 2,       
		    bg: '#e0e',   
		    size: 12    
		}
	}
},function(ret){
    if (ret) {
		api.alert({msg:JSON.stringify(ret)});
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m3"></div>
#**scene**

弹出 scene 样式的对话框

scene ({params},callback(ret))

##params

rect:

- 类型：JSON 对象类型
- 描述：scene 对话框的位置及尺寸配置
- 内部字段：

```js
{
    x: 50,                      //（可选项）数字类型；弹出框左上角的 x 坐标（相对于所属的 Window 或 Frame）；默认值：80
    y: 80,                      //（可选项）数字类型；弹出框左上角的 y 坐标（相对于所属的 Window 或 Frame）；默认值：100
    w: 220,                     //（可选项）数字类型；弹出框的宽度；默认值：220
    h: 320                      //（可选项）数字类型；弹出框的高度；默认值：320
}
```

styles:

- 类型：JSON 对象；
- 描述：scene 对话框样式设置
- 内部字段

```js
{
	title:{                            //（可选项）JSON 对象；弹窗 title 样式配置，不传则不显示
		bg: '#aaa',                    //（可选项）字符串类型；标题栏背景颜色配置，支持 #、rgb、rgba；默认：#aaa
		h: 44,                         //（可选项）数字类型；标题栏高度，默认：44
		size: 14,        	           //（可选项）数字类型；标题字体大小；默认：14
		color: #fff      	           //（可选项）字符串类型；标题字体颜色，支持#、rgb、rgba；默认：#fff
	},
	sceneImg:{                         //（可选项）JSON 对象；场景图片样式配置，不传则不显示
		h: 100,                        //（可选项）场景图片高度；默认：100
		path: ''                       // 字符串类型；场景图片路径（要求本地路径（widget://、fs://	）
	},
	content:{                          //（可选项）JSON 对象；文本内容样式配置
		color: '#eee',                 //（可选项）字符串类型；文本字体颜色,支持 rgb、rgba、#；默认：#eee
		size: 10                       //（可选项）数字类型；文本字体大小；默认：10 
	},
	cell: {                            //（可选项）JSON 对象；分组子项每一行的样式配置
    	bg: '#fff',                    //（可选项）字符串类型；分组子项的背景，支持rgb、rgba、#、img；默认：#fff
    	h: 68,                         //（可选项）数字类型；分组子项的高度；默认：68
    	text: {                        //（可选项）JSON 对象；事件选项文字样式配置，事件选项文字会自己上下居中显示
    		color: '#636363',          //（可选项）字符串类型；主标题文字颜色，支持rgb、rgba、#；默认：#636363
    		size: 13                   //（可选项）数字类型；主标题字体大小；默认：13
    	},
    	icon: {                        //（可选项）JSON 对象；头像的样式配置
    		marginL: 15,               //（可选项）数字类型；头像相对于分组子项左边的间距大小；默认：15
    		marginT: 9,                //（可选项）数字类型；头像相对于分组子项上边的间距大小；默认：9
    		w: 50,                     //（可选项）数字类型；头像的宽度；默认：50
    		h: 50,                     //（可选项）数字类型；头像的高度；默认：同 w
    		corner: 25                 //（可选项）数字类型；头像的圆角半径；默认：25
    	},
    	lineColor: '#eee',             //（可选项）字符串类型；分隔线的颜色，支持：rgb、rgba、#；默认：'#eee'
    	ok: {                          //（可选项）底部确认按钮的样式配置，不传则不显示底部按钮
			bg: '#89a',                //（可选项）字符串类型；底部按钮的背景颜色，支持：rgb、rgba、#；默认：'#89a'
			titleColor: '#f00',        //（可选项）字符串类型；底部按钮 title 文字颜色，支持：rgb、rgba、#；默认：'#f00'     
			titleSize: 14              //（可选项）数字类型；底部按钮 title 文字大小；默认：14
    	}
	}
}
```
texts：

- 类型：JSON 对象
- 描述：（可选项）scene对话框模块可配置的文本
- 内部字段：

```js
{
	title: '确认',          //（可选项）字符串类型；标题内容，若不传则不显示
	content:'场景',         //（可选项）字符串类型；对话框文本内容，若不传则不显示
	okBtnTitle: '取消'      //（可选项）字符串类型；底部按钮标题，若不传则不显示
}
```
optionDatas:

- 类型：数组类型
- 描述：（可选项）场景事件选项数据源，若为空则不显示
- 内部字段：

```js
[
	{                                  //（可选项）JSON 对象组成的数组；一个分组的数据信息
		title: '分组标题',              //（可选项）字符串类型；分组标题文字，若不传则不显示
		cells: [{                      //（可选项）数组类型；该分组中的 cell 数据
			icon: 'fs://creater.png',  //（可选项）字符串类型；图标地址，支持本地和网络资源路径（widget://、fs://）
			text: '事件选项文字'         //（可选项）字符串类型；事件选项文字
		}]
	}
]
```
##callback(ret)
ret：

- 类型：JSON对象
- 内部字段：

```js
{
	index: 1,           //数字类型；表示用户点击了的选项的索引
}
``` 

##示例代码

```js
var dialogBox = api.require('dialogBox');
dialogBox.scene ({
	rect: {
	    x: 50,                              
	    y: 80,                              
	    w: 220,                            
	    h: 320                             
	},
	styles: {
		title:{     
			bg: '#aaa',     
			h: 44,       	 
			size: 14,        
			color: #fff    
		},
		sceneImg: {
			h: 100,          
			path: ''        
		},
		content:{
			color: '#eee',         			
			size: 10        
		},
	    cell: {      
	    	bg: '#fff',                    
	    	h: 68,                         
	    	text: {                        
	    		color: '#636363',          
	    		size: 13                 
	    	},
	    	icon: {                       
	    		marginL: 15,              
	    		marginT: 9,                
	    		w: 50,                     
	    		h: 50,                     
	    		corner: 25                 
	    	}
		},
		OKButton: {
	    	bg: '#89a',                
			titleColor: '#f00'    
    	}
	},
	texts: {
		title: '情景1',          
		content:'火车售票处前的队伍蜿蜒纵横，旁边一小伙一边张望，一边将手伸向前面买票人的口袋，啊，是小偷!',         
		okBtnTitle: '确定' 
	}
	optionDatas: [{                 
		title: '分组标题',                
		cells: [{            
			text: '1、拿出手机偷拍'            
		},
		{       
			text: '2、见义勇为抓小偷'            
		},
		{       
			text: '3、大声提醒买票的人'            
		}]
	}]
}, function(ret) {
    alert(JSON.stringify(ret));
});

```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


<div id="m4"></div>
#**evaluation**

弹出 evaluation 样式的对话框

evaluation ({params}, callback(ret))

##params

styles:

- 类型：JSON 对象
- 描述：evaluation 对话框样式配置
- 内部字段：

```js
{
	bg: '#fff',             //（可选项）字符串类型；标题字体颜色，支持#、rgb、rgba、img，默认：#fff
	w: 300,                 //（可选项）数字类型；对话框的宽；默认 300
	h: 250,                 //（可选项）数字类型；对话框的高；默认 250
	title:{                 //（可选项）JSON 对象；对话框标题栏样式配置
		marginT: 20,        //（可选项）数字类型；标题栏顶部与弹出框顶部距离；默认 20
		size: 14,           //（可选项）数字类型；标题字体大小；默认：14
		color: '#fff',      //（可选项）字符串类型；标题字体颜色，支持 #、rgb、rgba；默认：#fff
		bold: true          //（可选项）布尔类型；标题字体是否是粗体；默认：true
	},
	content:{               //（可选项）JSON 对象；文本内容样式配置；不传则不显示
		marginT: '20',      //（可选项）数字类型；文本顶部与标题栏底部的距离，如果标题栏不存在，则是到弹出框顶部的距离；默认20
		color: '#eee',      //（可选项）字符串类型：文本字体颜色,支持 rgb、rgba、#；默认：#eee
		size: 10,           //（可选项）数字类型：文本数字类型；默认：10
	},
	buttons:[{              //（可选项）数组类型；JSON 对象组成的数组，按钮样式配置
		marginB: 0,         //（可选项）数字类型；按钮的下边距；默认：0
		marginL: 0,         //（可选项）数字类型；按钮的左边距；默认：0
		w: 300,             //（可选项）数字类型；按钮的宽；默认：300
		h: 35,              //（可选项）数字类型；按钮的高；默认：35
		bg: '#fff',         //（可选项）字符串类型；按钮的背景，支持 rgb，rgba，#，img；默认：'#fff'
		color: '#007FFF',   //（可选项）字符串类型；按钮显示文字颜色，支持 rgb，rgba,#；默认：'#007FFF'
		size: 12            //（可选项）数字类型；按钮显示文字的大小；默认：12
	}]
}
```
texts：

- 类型：JSON 对象
- 描述：（可选项）evaluation 对话框模块可配置的文本
- 内部字段：

```js
{
	title: '确认',          //（可选项）字符串类型；标题内容，若不传则不显示
	content:'场景',         //（可选项）字符串类型；对话框文本内容，若不传则不显示
	button: [{             //（可选项）数组类型；按钮显示文字组成的数组
		text: '取消'        //（可选项）字符串类型；按钮显示文字；默认：未设置时只显示背景
	}]
}
```
##callback(ret)
ret：

- 类型：JSON对象
- 内部字段：

```js
{
	index: 1,           //数字类型；表示用户点击了的按钮的索引
}
``` 

##示例代码
```js
var dialogBox = api.require('dialogBox');
dialogBox.evaluation ({
	styles: {
		bg: '#fff',
		w: 300,  
		h: 250,
		title:{ 
			marginT: 20,
			size: 14,
			color: '#fff',
			bold: true
		},
		content:{               
			marginT: '20',     
			color: '#eee',
			size: 10
		},
		buttons:[{
			marginB: 0,
			marginL: 0, 
			w: 300,
			h: 35,
			bg: '#fff',
			color: '#007FFF',
			size: 12
		}]
	},
	texts:	{
		title: '评价',          
		content:'给个评价吧',         
		button: [
		{            
			text: '下次再说' 
		},
		{
		   text: '亲，给个好评吧'
		}]
	}
},function(ret) {
    alert(JSON.stringify(ret));
});
```
##可用性

iOS系统，Android系统

可提供的 1.0.0 及更高版本

<div id="m5"></div>
#**raffle**

弹出 raffle 样式的对话框

raffle ({params}, callback(ret))

##params

texts：

- 类型：JSON 对象
- 描述：（可选项）raffle 对话框模块可配置的文本
- 内部字段：

```js
{
	title: '确认',          //（可选项）字符串类型；标题内容，若不传则不显示
	mainText: '收入囊中',    //（可选项）字符串类型；主文本内容，若不传则不显示
	subText: '告诉好友',     //（可选项）字符串类型；副文本内容，若不传则不显示
	leftTitle: '取消',      //（可选项）字符串类型；左边按钮标题，若不传则不显示
	rigthTitle: '确定'      //（可选项）字符串类型；左边按钮标题，若不传则不显示
}
```
styles:

- 类型：字符串
- 描述：raffle 对话框样式设置
- 内部字段：

```js
{
	bg: '#fff',                //（可选项）字符串类型；标题字体颜色，支持#、rgb、rgba、img，默认：#fff
	w: 300,                    //（可选项）数字类型；对话框的宽；默认 300
	h: 400,                    //（可选项）数字类型；对话框的高；默认 400
	title:{                    //（可选项）JSON 对象；弹窗标题栏样式配置
		size: 14,              //（可选项）数字类型；标题字体大小；默认：14
		color: '#fff',         //（可选项）字符串类型；标题字体颜色，支持#、rgb、rgba；默认：#fff
	},
	icon:{                     //（可选项）JSON 对象；图标样式配置，不传则不显示
		marginT: 20,           //（可选项）数字类型；图标顶部与标题栏底部的距离，图标左右居中显示；默认：20
		w: 40,                 //（可选项）数字类型；图标宽度；默认：40
		h: 40,                 //（可选项）数字类型；图标高度；默认：40
		iconPath: 'widget://'  // 字符串类型；图标路径，要求本地路径（widget://、fs://）；
	},
    main: {                    //（可选项）JSON 对象；主文本样式设置，主文本会左右居中显示
        marginT: 74,           //（可选项）数字类型；主文本相对于 icon 底部的间距大小；默认：20
        color: '#636363',      //（可选项）字符串类型；主文本文字颜色，支持rgb、rgba、#；默认：#636363
        size: 13               //（可选项）数字类型；主文本字体大小；默认：13
    },
    sub: {                     //（可选项）JSON 对象；副文本样式设置，副文本会左右居中显示
        marginT: 8,            //（可选项）数字类型；副文本和主文本之间的间隙大小；默认：8
        color: '#999999',      //（可选项）字符串类型；副文本文字颜色，支持 rgb、rgba、#；默认：#999999
        size: 12               //（可选项）数字类型；副文本字体大小；默认：12
    },
	left:{                     //（可选项）JSON 对象；左边按钮样式设置, 不传则不显示
		marginB: 7,            //（可选项）数字类型；左边按钮的下边距；默认：7
		marginL: 18,           //（可选项）数字类型；左边按钮的左边距；默认：18
		w: 90,                 //（可选项）数字类型；左边按钮的宽；默认：90
		h: 35,                 //（可选项）数字类型；左边按钮的高；默认：35
		corner: 2,             //（可选项）数字类型；左边按钮圆角半径；默认：0.0
		bg: '#fff',            //（可选项）字符串类型；左边按钮的背景，支持rgb，rgba，#，img；默认：'#fff'
		color: '#007FFF',      //（可选项）字符串类型；左边按钮显示文字颜色，支持rgb，rgba,#；默认：'#007FFF'
		size: 12               //（可选项）数字类型；左边按钮显示文字的大小；默认：12
	},
	right: {                   //（可选项）JSON 对象；右边按钮样式设置，不传则不显示
		marginB: 7,            //（可选项）数字类型；右边按钮的下边距；默认：7
		marginL: 18,           //（可选项）数字类型；右边按钮的左边距；默认：18
		w: 90,                 //（可选项）数字类型；右边按钮的宽；默认：90
		h: 35,                 //（可选项）数字类型；右边按钮的高；默认：35
		corner: 2,             //（可选项）数字类型；右边按钮圆角半径；默认：0.0
		bg: '#fff',            //（可选项）字符串类型；右边按钮的背景，支持rgb，rgba，#，img；默认：'#fff'
		color: '#007FFF',      //（可选项）字符串类型；右边按钮显示文字颜色，支持rgb，rgba,#；默认：'#007FFF'
		size: 12               //（可选项）数字类型；右边按钮显示文字的大小；默认：12
	}
}
```
##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	eventType: 'left',          //字符串类型；交互事件类型，取值范围如下：
                                // left（表示用户点击了左边按钮）
                                // right（表示用户点击了右边按钮）
}
```
##示例代码

```js
var dialogBox = api.require('dialogBox');
dialogBox.raffle ({
	texts: {
		title: '恭喜你',          
		mainText: '5枚钱币',    
		subText: '这就中了，还有什么你做不到',    
		leftTitle: '收入囊中',   
		rigthTitle: '告诉好友'   
	},
	styles: {
		bg: '#fff',               
		w: 300,                  
		h: 400,                    
		title:{                    
			size: 14,             
			color: '#fff',         
		},
		icon:{         
			marginT: 20,           
			w: 40,                 
			h: 40,               
			iconPath:           
		},
	    main: {                   
	        marginT: 74,          
	        color: '#636363',      
	        size: 13            
	    },
	    sub: {                     
	        marginT: 8,      
	        color: '#999999',
	        size: 12   
	    },
		leftButton:{      
			marginB: 7, 
			marginL: 18,
			w: 90,
			h: 35,
			corner: 2,        
			bg: '#fff',     
			color: '#007FFF',
			size: 12 
		},
		rightButton: {    
			marginB: 7,   
			marginL: 18, 
			w: 90,  
			h: 35,   
			corner: 2,  
			bg: '#fff', 
			color: '#007FFF',  
			size: 12              
		}
	}
},function(ret) {
    alert(JSON.stringify(ret));
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m6"></div>
#**remind**

弹出 remind 样式的对话框

remind({params}, callback(ret))

##params

texts：

- 类型：JSON 对象
- 描述：（可选项）remind 对话框模块可配置的文本
- 内部字段：

```js
{
	mainTitle: '服务未打开',    //（可选项）字符串类型；主标题，若不传则不显示
	subTitle: '请打开定位服务',  //（可选项）字符串类型；副标题，若不传则不显示
	button: '确定'             //（可选项）字符串类型；底部按钮标题，若不传则不显示
}
```

styles:

- 类型：JSON 对象类型
- 描述：remind 对话框样式设置
- 内部字段：

```js
{
	bg: '#fff',                //（可选项）字符串类型；对话框背景颜色，支持#、rgb、rgba、img，默认：#fff
	w: 300,                    //（可选项）数字类型；对话框的宽；默认 300 
	h: 200,                    //（可选项）数字类型；对话框的高；默认 200
	main: {                    //（可选项）JSON 对象；主标题样式设置，主文本会左右居中显示
        marginT: 74,           //（可选项）数字类型；主标题相对于弹出框顶部的间距大小；默认：20
        color: '#636363',      //（可选项）字符串类型；主标题文字颜色，支持rgb、rgba、#；默认：#636363
        size: 13,              //（可选项）数字类型；主标题字体大小；默认：13
        bold: true             //（可选项）布尔类型；主标题字体粗体显示 true | false；默认：true
    },
    sub: {                     //（可选项）JSON 对象；副标题样式设置，副文本会左右居中显示
        marginT: 8,            //（可选项）数字类型；副标题和主文本之间的间隙大小；默认：8
        color: '#999999',      //（可选项）字符串类型；副标题文字颜色，支持 rgb、rgba、#；默认：#999999
        size: 12               //（可选项）数字类型；副标题字体大小；默认：12
    },
	button: {                  //（可选项）JSON 对象；底部按钮样式设置, 不传则不显示
		marginB: 7,            //（可选项）数字类型；按钮的下边距；默认：7
		marginL: 18,           //（可选项）数字类型；按钮的左边距；默认：18
		w: 90,                 //（可选项）数字类型；按钮的宽；默认：90
		h: 35,                 //（可选项）数字类型；按钮的高；默认：35
		corner: 2,             //（可选项）数字类型；按钮圆角半径；默认：0.0
		bg: '#fff',            //（可选项）字符串类型；按钮的背景，支持rgb，rgba，#，img；默认：'#fff'
		color: '#007FFF',      //（可选项）字符串类型；按钮显示文字颜色，支持rgb，rgba,#；默认：'#007FFF'
		size: 12               //（可选项）数字类型；按钮显示文字的大小；默认：12
	}
}
```
##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	eventType: 'ok',          //字符串类型；交互事件类型，表示用户点击了底部按钮
}
```
##示例代码

```js
var dialogBox = api.require('dialogBox');
dialogBox.remind ({
	{
		mainTitle: '服务未打开',    
		subTitle: '请打开“定位服务”来允许“xxx”定位你的位置',    
		button: '确定'    
	},
	styles: {
		bg: '#fff', 
		w: 300,                    
		h: 200,                   
		main: {                   
	        marginT: 74,           
	        color: '#636363',      
	        size: 13,             
	        bold: true            
	    },
	    sub: {                    
	        marginT: 8,            
	        color: '#999999',      
	        size: 12              
	    },
		button: {                  
			marginB: 7,           
			marginL: 18,           
			w: 90,                
			h: 35,                 
			corner: 2,             
			bg: '#fff',            
			color: '#007FFF',      
			size: 12  
		}
	}
},function(ret) {
    alert(JSON.stringify(ret));
});
```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m7"></div>
#**dayNote**

弹出 dayNote 样式的对话框

dayNote({params}, callback(ret))

##params

rect：

- 类型：JSON 对象
- 描述：（可选项）dayNote 对话框的位置及尺寸配置
- 内部字段：

```js
{
    x: 0,                       //（可选项）数字类型；对话框左上角的 x 坐标（相对于所属的 Window 或 Frame）；默认值：0
    y: 0,                       //（可选项）数字类型；对话框左上角的 y 坐标（相对于所属的 Window 或 Frame）；默认值：0
    w: api.winWidth,            //（可选项）数字类型；对话框的宽度；默认值：所属的 Window 或 Frame 的宽度
    h: api.winHeight            //（可选项）数字类型；对话框的高度；默认值：所属的 Window 或 Frame 的宽高度
}
```

texts：

- 类型：JSON 对象
- 描述：（可选项）taskPlan 对话框模块可配置的文本
- 内部字段：

```js
{
	note: [{               //（可选项）数组类型；各行日笺内容组成数组，若不传则不显示
	   text: ''            //（可选项）字符串类型；每一行日笺内容，若不传则不显示
	}],
	date: '',              //（可选项）字符串类型；日期栏日期，若不传则不显示
	btnDate: ''            //（可选项）字符串类型；日期栏按钮标题，若不传则不显示
}
```

styles:

- 类型：JSON 对象
- 描述：dayNote 对话框样式设置
- 内部字段：

```js
{
	mask: '#fff',              //（可选项）字符串类型；标题字体颜色，支持 #、rgb、rgba、img，默认：#fff
	bg: {
		path: '#fff',          //（可选项）字符串类型；背景图片路径，要求本地路径（widget://、fs://）；
		marginT: 10,           //（可选项）数字类型；背景图片相对于弹出框顶部的间距大小；默认：10
		marginL: 10,           //（可选项）数字类型；背景图片相对于弹出框左边的间距大小；默认：10
		w: 300,                //（可选项）数字类型；背景图片宽度；默认：300
		h: 400                 //（可选项）数字类型；背景图片高度；默认：400
	},
	note: [{                   //（可选项）数组类型；每一行内容的样式组成的数组；
		bg: '#fff',            //（可选项）字符串类型；文本内容背景颜色，支持rgb，rgba,#；默认：'#fff'
		marginT: 10,           //（可选项）数字类型；文本相对于弹出框顶部的间距大小；默认：10
		marginL: 10,           //（可选项）数字类型；文本相对于弹出框左边的间距大小；默认：10
		w: 300,                //（可选项）数字类型；文本宽度；默认：300
		h: 400,                //（可选项）数字类型；文本高度；默认：400
		align: 'left',         //（可选项）字符串类型；文本对齐方式，left | center | right；默认：left
		color: '#007FFF',      //（可选项）字符串类型；按钮显示文字颜色，支持rgb，rgba,#；默认：'#007FFF'
		size: 12               //（可选项）数字类型；按钮显示文字的大小；默认：12
	}],
	date: {                    //（可选项）JSON 对象；日笺日期栏样式设置,上下左右居中
		h: 60,                 //（可选项）数字类型；日期栏高度；默认：60    
		btnBg: '#fff',         //（可选项）字符串类型；日笺栏显示动作按钮背景颜色，支持 #、rgb、rgba、img；默认：#fff
		btnColor: '#111'       //（可选项）字符串类型；日笺栏显示动作按钮标题颜色，支持 #、rgb、rgba；默认：#111
	},
	cancelButton: {            //（可选项）JSON 对象，取消按钮设置，居中显示，不传则不显示
		size: 44,              //（可选项）数字类型；底部取消按钮的高和宽；默认：44
		bg: 'rgba(0,0,0,0)',   //（可选项）字符串类型；取消按钮的 100% 宽度的背景，支持rgb，rgba，#，img；默认：rgba(0,0,0,0)
		icon: 'widget://'      //（可选项）字符串类型；取消按钮的图标，要求本地路径（widget://、fs://）；默认：默认X型图标
    }
}
```
##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	eventType: 'check',          //字符串类型；交互事件类型，表示用户点击了日笺栏的按钮
}
```

##示例代码
```js
var dialogBox = api.require('dialogBox');
obj.dayNote ({ 
	rect: {
	    x: 0,                       
	    y: 0,                       
	    w: api.winWidth,            
	    h: api.winHeight 
	},
	texts:{
		note: [{ 
		   text: '后来我终于明白'
		},{ 
		   text: '它尽管跟天气一样难以预料'
		},{ 
		   text: '却也跟天气一样难以避免'
		}],
		date: '2016-04-07',
		btnDate: '查看日笺' 
	},
	styles:{
		mask: '#fff',              
		bg: {
			path: '#fff',          
			marginT: 10,           
			marginL: 10,           
			w: 300,                
			h: 400               
		},
		note: [{                   		
			bg: '#fff',            
			marginT: 10,           
			marginL: 10,           
			w: 300,                
			h: 400,                
			align: 'left',         
			color: '#007FFF',      
			size: 12               
		}],
		date: {                  
			h: 60,                  
			btnBg: '#fff',         
			btnColor: '#111'       
		},
		cancelButton: {            
			size: 44,             
			bg: '#fff',         
			icon: 'widget://'     
	    }
	}
},function(ret) {
    alert(JSON.stringify(ret));
});
```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


<div id="m8"></div>
#**taskPlan**

弹出 taskPlan 样式的对话框

taskPlan ({params},callback(ret))

##params

rect：

- 类型：JSON 类型
- 描述：（可选项）taskPlan 对话框的尺寸配置, 上下左右居中对齐
- 内部字段：

```js
{
    w: 300,            //（可选项）数字类型；对话框的宽度；默认值：300
    h: 280             //（可选项）数字类型；对话框的高度；默认值：280
}
```
texts：

- 类型：JSON 对象
- 描述：（可选项）taskPlan 对话框模块可配置的文本
- 内部字段：

```js
{
	mainTitle: '',         //（可选项）字符串类型；主标题，若不传则不显示
	subText: '',           //（可选项）字符串类型；副标题，若不传则不显示
	content: [{            //（可选项）数组类型；各行文本内容，若不传则不显示
	   text: ''            //（可选项）字符串类型；每一行文本内容，若不传则不显示
	}],
	btnTitle: ''           //（可选项）字符串类型；左边按钮标题，若不传则不显示
}
```
styles:

- 类型：JSON 对象类型
- 描述：taskPlan 对话框样式设置
- 内部字段：

```js
{
	bg: '#fff',                //（可选项）字符串类型；标题字体颜色，支持#、rgb、rgba、img，默认：#fff
	main: {                    //（可选项）JSON 对象；主标题样式设置，主文本会左右居中显示
        marginT: 74,           //（可选项）数字类型；主标题相对于弹出框顶部的间距大小；默认：20
        color: '#636363',      //（可选项）字符串类型；主标题文字颜色，支持rgb、rgba、#；默认：#636363
        size: 13,              //（可选项）数字类型；主标题字体大小；默认：13
        bold: true,            //（可选项）布尔类型；主标题字体粗体显示 true | false；默认：true
        text: ''               //（可选项）字符串类型；主标题内容
    },
    sub: {                     //（可选项）JSON 对象；副标题样式设置，副文本会左右居中显示
        marginT: 8,            //（可选项）数字类型；副标题和主文本之间的间隙大小；默认：8
        color: '#999999',      //（可选项）字符串类型；副标题文字颜色，支持 rgb、rgba、#；默认：#999999
        size: 12,              //（可选项）数字类型；副标题字体大小；默认：12
        text: '告诉好友'        //（可选项）字符串类型；副标题内容
    },
    content: [{                //（可选项）数组类型；每一行内容的样式组成的数组；
		text:                  //（可选项）字符串类型；文本内容；
		bg: '#fff',            //（可选项）字符串类型；文本内容背景颜色，支持rgb，rgba,#；默认：'#fff'
		underLine: true,       // 可选项）布尔类型；文本是否下划线，true | false；默认：false
		underLineColor: '#10c',//（可选项）字符串类型；文本下划线颜色，仅 underLine 为 true 时有效，支持rgb，rgba,#；默认：'#10c',
		marginT: 10,           //（可选项）数字类型；文本相对于弹出框顶部的间距大小；默认：10
		marginL: 10,           //（可选项）数字类型；文本相对于弹出框左边的间距大小；默认：10
		w: 300,                //（可选项）数字类型；文本宽度；默认：300
		h: 400,                //（可选项）数字类型；文本高度；默认：400
		align: 'left',         //（可选项）字符串类型；文本对齐方式，left | center | right；默认：left
		color: '#007FFF',      //（可选项）字符串类型；按钮显示文字颜色，支持rgb，rgba,#；默认：'#007FFF'
		size: 12               //（可选项）数字类型；按钮显示文字的大小；默认：12
	}],
	button: {                  //（可选项）JSON 对象；底部按钮样式设置, 不传则不显示
		marginB: 10,           //（可选项）数字类型；按钮的下边距；默认：10
		marginL: 20,           //（可选项）数字类型；按钮的左边距；默认：20
		w: 280,                //（可选项）数字类型；按钮的宽；默认：280
		h: 40,                 //（可选项）数字类型；按钮的高；默认：40
		bg: '#fff',            //（可选项）字符串类型；按钮的背景，支持rgb，rgba，#，img；默认：'#fff'
		color: '#007FFF',      //（可选项）字符串类型；按钮显示文字颜色，支持rgb，rgba,#；默认：'#007FFF'
		text: '我知道了',       //（可选项）字符串类型；按钮显示文字；默认：未设置时只显示背景
		size: 12               //（可选项）数字类型；按钮显示文字的大小；默认：12
	}
}
```
##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	eventType: 'task',               // 字符串类型；交互事件类型，取值范围如下：
                                     // task（表示用户点击了底部按钮）
                                     // underLine（表示用户带有下划线的文本内容；只在当 underLine 为true 时有效
}
```
##示例代码
```js
var dialogBox = api.require('dialogBox');
obj.taskPlan ({ 
	rect: {
	    w: 300,            
	    h: 280             
	},
	texts:{
		mainTitle: '昨天玩的不够努力哦', 
		subText: '今天没有获得任务次数奖励呢',       
		content: [{             
		   text: '今日赚任务总次数：3次'     
		},{
		   text: '3次（基础）+ 0次（奖励）'     
		}],
		btnTitle: '开始做任务'           
	},
	styles:{
		bg: '#fff',                
		main: {                    
	        marginT: 74,           
	        color: '#636363',      
	        size: 13,             
	        bold: true,            
	    },
	    sub: {                     
	        marginT: 8,            
	        color: '#999999',      
	        size: 12,              
	    },
	    content: [{                
			bg: '#fff',            
			underLine: true,       
			underLineColor: '#10c',
			marginT: 10,           
			marginL: 10,          
			w: 300,                
			h: 400,                
			align: 'left',         
			color: '#007FFF',      
			size: 12               
		}],
		button: {                 
			marginB: 10,           
			marginL: 20,           
			w: 280,                
			h: 40,                 
			bg: '#fff',            
			color: '#007FFF',      
			size: 12               
		}
	}
},function(ret) {
    alert(JSON.stringify(ret));
});
```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m9"></div>
#**confirm**

弹出 confirm 样式的对话框

confirm({params}

##params

texts:

- 类型：JSON 对象类型
- confirm 对话框文本及图标路径的配置
- 内部字段：

```js
{   
  iconPath     :'  ',  // 字符串类型；标题图标的路径（支持 widget:// fs://）；不填则不显示
	contentText  :'  ',  // 字符串类型；文本信息；不填则不显示
	confirmText  :'确定', // 字符串类型；确认按钮的文本信息;不填则不显示
},
```

rect:

- 类型：JSON 对象类型
- confirm 对话框的位置及尺寸
- 内部字段：

```js
{   
	 x:80,   //（可选项）数字类型；弹出框左上角的 x 坐标（相对于所属的 Window 或 Frame）；默认值：80
	 y:80,   //（可选项）数字类型；弹出框左上角的 y 坐标（相对于所属的 window 或 Frame）；默认值：80
	 w:200,  //（可选项）数字类型；弹出框的宽度；默认值：200
	 h:300   //（可选项）数字类型；弹出框的高度；默认值：300
},
```

styles:

- 类型：JSON 对象类型
- confirm 对话框样式设置
- 内部字段：

```js
{
	 bg:'#FFF',  //（可选项）字符串类型；对话框整体背景配置，支持#、rgb、rgba、img；默认：#FFF
	 icon:{      //（可选项）JSON对象类型；对话框标题图片的配置
		 w:100,    // 数字类型；标题图标的宽度；默认值：100
		 h:100     // 数字类型，标题图标的高度；默认值：100
	 },
	 content:{           // JSON对象类型；标题文本设置
		 margin:30,        // 数字类型；文本内容距离上下左右边缘的距离；默认值：30
		 textColor:'#FFF', // 字符串类型；文本的字体颜色；支持#、rgb、rgba；默认值：#FFF
		 textSize:18       // 数字类型；文本字体的大小；默认值：18
	 },
	 confirm:{           // JSON对象类型；确认按钮的配置
		 bg:'#FF0',        // 字符串类型；确认按钮文本的背景颜色；支持#、rgb、rgba；默认值：#FFF
		 textColor:'#EEE', // 字符串类型；确认按钮的字体颜色；支持#、rgb、rgba；默认值：#EEE
		 textSize:18       // 数字类型；确认按钮的字体大小；默认值：18
	 }
}
```

##callback(ret)

ret:

- 类型：JSON对象
- 内部字段：

```js
{
	eventType : "ok"
}
```

##示例代码

```js
var dialogBox = api.require('dialogBox');
dialogBox.confirm ({
	texts:{   
	  iconPath   :'widget://image/someIcon.png',
		contentText  :'内容文本',
		confirmText  :'确定'
	},
	styles:{
	 bg:'#FFF',
	 rect:{    
		 	x:0,
			y:0,
			w:200,
			h:300
	 },
	 icon:{  
		 w:100,
		 h:100
	 },
	 content:{
		 margin:30,
		 textColor:'#FFF',
		 textSize:18
	 },
	 confirm:{
		 bg:'#FF0',
		 textColor:'#F0F',
		 textSize:18
	 }
}}, function(ret){

});
```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


<div id="m10"></div>
#**receipt**

弹出 receipt 样式的对话框

receipt({params}

##params

datas:

- 类型：JSON 数组类型
- 对话框列表的显示数据
- 内部字段：

```js
[
	{
		itemKey   :  '起步价', // 字符串类型；列表标题内容；不填则不显示
		itemValue :  '0.00'   // 字符串类型；列表描述内容；不填则不显示
	}
]
```

styles:

- 类型：JSON 对象类型
- receipt 对话框样式设置
- 内部字段：

```js
{
	 bg:'#FFF',            // 字符串类型；对话框的背景色，支持#、rgb、rgba、img；默认：#FFF
	 rect:{                // JSON对象类型；对话款的位置及尺寸的设置
		 	x:0,               //（可选项）数字类型；弹出框左上角的 x 坐标（相对于所属的 Window 或 Frame）；默认值：80
			y:0,               //（可选项）数字类型；弹出框左上角的 y 坐标（相对于所属的 Window 或 Frame）；默认值：80
			w:200,             //（可选项）数字类型；弹出框的宽度；默认值：200
			h:300              //（可选项）数字类型；弹出框的宽度；默认值：300
	 },
	 title:{               // JSON对象类型；对话框标题设置
		 text:"标题",        // 字符串类型；标题内容；不填则不显示
		 textColor:"#000",  // 字符串类型；标题的字体颜色；支持#、rgb、rgba；默认值：#FFF
		 textSize:18,       // 数字类型；标题的字体大小；默认值：18
		 marginTop:10       // 数字类型；标题的上边距；默认值：18
	 },
	 topBorder:{          // JSON对象类型；上边界线的设置
		 borderColor:"#000",// 字符串类型；边界线颜色，支持#、rgb、rgba、img；默认：#000
		 borderHeight:"2",  // 数字类型；边界线的高度，默认值：2
		 marginTop: 10      // 数字类型；边界线的上边距，默认值：10
	 },
	 item:{  									// JSON对象类型；列表项的设置
		 itemTextColor: "#000", // 字符串类型；列表的字体颜色，支持#、rgb、rgba；默认值：#FFF
		 itemTextSize : 18,     // 数字类型；列表的字体大小；默认值：18
		 itemMarginLeft:10,     // 数字类型；列表的左边距；默认值：10
		 itemMarginRight:10,    // 数字类型；列表的右边距；默认值：10
		 itemMarginTop:10,      // 数字类型；列表的上边距；默认值：10
		 itemMarginBottom:10,   // 数字类型；列表的下边距；默认值：10
		 itemBgColor:"#FFF"     // 字符串类型；列表项的背景颜色，支持#、rgb、rgba；默认值：#FFF
	 },
	 bottomBorder:{          // JSON对象类型；下边界线的设置
		 borderColor:"#000",   // 字符串类型；边界线颜色，支持#、rgb、rgba；默认值：#000
		 borderHeight:2,       // 数字类型；边界线的高度；默认值：2
		 marginTop: 10         // 数字类型；边界线的上边距；默认值：10
	 },
	 cancelBtn:{
		  cancelText:"取消",         // 字符串类型；取消按钮文本配置；不填则不显示
			cancelTextSize: 18,       // 数字类型；取消按钮字体大小；默认值：18
			cancelTextColor:"#000",   // 字符串类型；取消按钮字体颜色，支持#、rgb、rgba；默认值：#000
			marginTop: 10             // 数字类型；取消按钮上边距；默认值：10
	 }
}
```

##callback(ret)

ret:

- 类型：JSON对象
- 内部字段：

```js
{
	eventType : "cancel"
}
```

##示例代码
```js
var dialogBox = api.require('dialogBox');
dialogBox.receipt({
	datas:[
		{
			itemKey   :  '起步价',
			itemValue :  '0.00'
		},
		{
			itemKey   :  '小计',
			itemValue :  '100'
		},
		{
			itemKey   : '总消费',
			itemValue : '150'
		}
	],
	styles:{
		 bg:'#FFF',
		 rect:{   
			 	x:0,
				y:0,
				w:200,
				h:300
		 },
		 title:{   
			 text:"标题",
			 textColor:"#000",
			 textSize:18,
			 marginTop:10
		 },
		 topBorder:{  
			 borderColor:"#000",
			 borderHeight:"2",
			 marginTop: 10
		 },
		 item:{  
			 itemTextColor: "#000",
			 itemTextSize : 18,  
			 itemMarginLeft:10,  
			 itemMarginRight:10,
			 itemMarginTop:10,
			 itemMarginBottom:10,
			 itemBgColor:"#FFF"
		 },
		 bottomBorder:{
			 borderColor:"#000",
			 borderHeight:"2",
			 marginTop: 10
		 },
		 cancelBtn:{
			  text:"取消",
				textSize: 18,
				textColor:"#FFF",
				marginTop: 10
		 }
	}

}, function(ret){

});
```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


<div id="m11"></div>
#**activity**

弹出 activity 样式的对话框

activity({params}

##params

styles:

- 类型：JSON 对象类型
- activity 对话框样式设置
- 内部字段：

```js
{
	 bg:'#FFF',  // 字符串类型；对话框的背景色，支持#、rgb、rgba、img；默认：#FFF
	 rect:{      // JSON对象类型；对话框的位置及尺寸的设置
		 	x:0,     //（可选项）数字类型；弹出框左上角的 x 坐标（相对于所属的 Window 或 Frame）；默认值：80
			y:0,     //（可选项）数字类型；弹出框左上角的 y 坐标（相对于所属的 Window 或 Frame）；默认值：80
			w:200,   //（可选项）数字类型；弹出框的宽度；默认值：200
			h:300    //（可选项）数字类型；弹出框的宽度；默认值：300
	 },
	 topImage:{
		 path:"widget://image/top_image.png", //字符串类型；顶部图标的的路径，支持（widget:// fs://），不填则不显示
		    w: 200,                           //字符串类型；图标的宽度；默认值：200
		    h: 80                             //字符串类型；图标的高度；默认值：80
	 },
	 title:{                  // JSON对象类型；标题文本信息设置
		 text:"这里是标题文本",   // 字符串类型；标题文本；不填则不显示
		 textColor:"#000",      // 字符串类型；对话框的背景色，支持#、rgb、rgba 默认：#FFF
		 textSize:24,           // 数字类型；标题文本字体大小；默认值：24
		 marginTop:15           // 数字类型；上边距值；默认值：15
	 },
	 content:{             // JSON对象类型；内容文本信息设置
		 text:"这里是内容",   // 字符串类型；内容文本；不填则不显示
		 textColor:"#000",   // 字符串类型；内容字体颜色；支持#、rgb、rgba 默认：#000
		 textSize:20,        // 数字类型；字体的大小；默认值：20
		 marginTop:15        // 数字类型；上边距；默认值：15
	 },
	 okBtn:{             // JSON对象类型；确定按钮设置
		 text:"ok",        // 字符串类型；确定按钮的文本设置；
		 textColor:"#000", // 字符串类型；确定按钮字体颜色；支持#、rgb、rgba 默认：#000
		 textSize:16,      // 数字类型；确定按钮字体大小；默认值：16
		 marginTop:15      // 数字类型；上边距；默认值：15
	 }
}
```

##callback(ret)

ret:

- 类型：JSON对象
- 内部字段：

```js
{
	eventType : "ok"
}
```

##示例代码
```js
var dialogBox = api.require('dialogBox');
dialogBox.activity({
	styles:{
		 bg:'#FFF',
		 rect:{     
			 	x:0,   
				y:0,   
				w:200,  
				h:300  
		 },
		 topImage:{
			 path:"widget://image/top_image.png",
			 w: 200,
			 h: 80
		 },
		 title:{
			 text:"这里是标题文本",
			 textColor:"#000",
			 textSize:24,  
			 marginTop:15
		 },
		 content:{  
			 text:"这里是内容",
			 textColor:"#000",  
			 textSize:20,
			 marginTop:15  
		 },
		 okBtn:{
			 text:"ok",
			 textColor:"#000",
			 textSize:16,
			 marginTop:15
		 }
	}
});
```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


<div id="m12"></div>
#**tips**

弹出 tips 样式的对话框

tips({params}

##params

styles:

- 类型：JSON 对象类型
- confirm 对话框样式设置
- 内部字段：

```js
{
	 bg:'#FFF', // 字符串类型；对话框的背景色，支持#、rgb、rgba、img；默认：#FFF
	 rect:{     // JSON对象类型；对话框的位置及尺寸的设置
		 	x:0,    //（可选项）数字类型；弹出框左上角的 x 坐标（相对于所属的 Window 或 Frame）；默认值：80
			y:0,    //（可选项）数字类型；弹出框左上角的 y 坐标（相对于所属的 Window 或 Frame）；默认值：80
			w:200,  //（可选项）数字类型；弹出框的宽度；默认值：200
			h:300   //（可选项）数字类型；弹出框的高度；默认值：300
	 },
	 topImage:{
		 path:"widget://image/top_image.png", // 字符串类型；顶部图标的的路径，支持 (widget:// fs://)，不填则不显示
		    w: 200,                           // 数字类型；图标的宽度；默认值：200
		    h: 80                             // 数字类型；图标的高度；默认值：80
	 },
	 title:{                 // JSON对象类型；标题文本信息设置
		 text:"这里是标题文本",  // 字符串类型；标题文本
		 textColor:"#000",     // 字符串类型；标题文本字体颜色，支持#、rgb、rgba；默认：#000
		 textSize:24,          // 数字类型；标题文本字体大小；默认值：24
		 marginTop:15          // 数字类型；上边距； 默认值：15
	 },
	 content:{             // JSON对象设置；内容文本设置
		 text:"这里是内容",   // 字符串类型；内容文本；不填则不显示
		 textColor:"#000",   // 字符串类型；内容文本字体颜色，支持#、rgb、rgba；默认：#000
		 textSize:20,        // 数字类型；字体的大小；默认值：20
		 marginTop:15        // 数字类型；上边距；默认值：15
	 },
	 buttons:[{                               // JSON对象类型；底部分享按钮设置
		 iconPath:'widget://image/icon.png',    // 字符串类型；按钮图标的路径，支持 widget:// fs://；不填则不显示
		 iconWidth: 30,                         // 数字类型；按钮图标的宽；默认值：30
		 iconHeight:30,                         // 数字类型；按钮图标的高；默认值：30
		 text:"微信",                           // 字符串类型；按钮文本；
		 textColor:"#000",                      // 字符串类型 按钮文本字体颜色，字符串类型；标题文本字体颜色，支持#、rgb、rgba；默认：#000   
		 textSize:16,                           // 数字类型；按钮文本字体的大小；默认值：16
		 marginTop:15 ,                         // 数字类型；上边距；默认值：15  
		 marginLeft:10                          // 数字类型；按钮左边距；默认值：10
	 }]
}
```

##callback(ret)
ret:

- 类型：JSON对象
- 内部字段：

```js
{
	index: index,        // 数字类型；点击按钮的索引；
	eventType : "click"  // 字符串类型；按钮操作类型，只支持点击操作
}
```

##示例代码
```js
var dialogBox = api.require('dialogBox');
dialogBox.activity({
	styles:{
		 bg:'#FFF',
		 rect:{    
			 	x:0,   
				y:0,   
				w:200,  
				h:300  
		 },
		 topImage:{
			 path:"widget://image/top_image.png",
			 w: 200,
			 h: 80
		 },
		 title:{
			 text:"这里是标题文本",
			 textColor:"#000",
			 textSize:24,
			 marginTop:15
		 },
		 content:{  
			 text:"这里是内容",
			 textColor:"#000",
			 textSize:20,
			 marginTop:15
		 },
		 buttons:[{
			 iconPath:'widget://image/weixin.png',
			 iconWidth: 30,
			 iconHeight:30,
			 text:"微信",
			 textColor:"#000",
			 textSize:16,
			 marginTop:15
		 },
		 {
			 iconPath:'widget://image/weibo.png',
			 iconWidth: 30,
			 iconHeight:30,
			 text:"微博",
			 textColor:"#000",
			 textSize:16,
			 marginTop:15 ,
			 marginLeft:10
		 }]
	}
}, function(ret){
	alert(JSON.stringify(ret));
});
```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


<div id="m13"></div>
#**discount**

弹出 discount 样式的对话框

discount({params}

##params

styles:

- 类型：JSON 对象类型
- discount 对话框样式设置
- 内部字段：

```js
{
	 bg:'#FFF', // 字符串类型；对话框的背景色，支持#、rgb、rgba、img；默认：#FFF
	 rect:{     // JSON对象类型；对话框的位置及尺寸的设置
		 	x:0,    //（可选项）数字类型；弹出框左上角的 x 坐标（相对于所属的 Window 或 Frame）；默认值：80
			y:0,    //（可选项）数字类型；弹出框左上角的 x 坐标（相对于所属的 Window 或 Frame）；默认值：80
			w:200,  //（可选项）数字类型；弹出框的宽度；默认值：200
			h:300   //（可选项）数字类型；弹出框的高度；默认值：300
	 },
	 image:{
		 imagePath:"widget://image/image.png"   // 字符串类型；图片路径，支持 widget:// fs:// ；不传则不显示
		 marginBottom:30                        // 数字类型；下边距；默认值：30
	 },
	 cancelBtn:{                              // JSON对象类型；取消按钮设置
		 icon:"widget://image/cancel_btn.png"   // 字符串类型；按钮图标路径，支持 widget:// fs:// ；不传则不显示
		 w:50,                                  // 数字类型；按钮宽；默认值：50
		 h:50,                                  // 数字类型；按钮高；默认值：50
		 cancelText : "取消",                   // 字符串类型；取消按钮文本设置；
		 cancelTextSize: 18,                    // 数字类型；取消按钮文本字体大小；默认值：18
		 cancelTextColor: "#000"                // 字符串类型；取消按钮的字体颜色，支持#、rgb、rgba；默认：#000   
	 }

}
```

##callback(ret)
ret:

- 类型：JSON对象
- 内部字段：

```js
{
	eventType : "cancel"  // 字符串类型；回调事件类型
}
```

##示例代码
```js
var dialogBox = api.require('dialogBox');
dialogBox.discount({
	styles:{
	 bg:'#FFF',
	 rect:{   
		 	x:0,   
			y:0,   
			w:200,
			h:300  
	 },
	 image:{
		 imagePath:"widget://image/image.png"
		 marginBottom:30
	 },
	 cancelBtn:{
		 icon:"widget://image/cancel_btn.png"
		 w:50,
		 h:50  
	 }

}});
```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


<div id="m14"></div>
#**share**

弹出 share 样式的对话框

share({params}

##params

datas:

- 类型: JSON数组类型
- share 对话框数据
- 内部字段:

```js
[
	{
		itemText: "微信",                                // 字符串类型；每一项的文本字段
		itemIcon: "widget://image/icon/weixin_icon.png"  // 字符串类型；每一项图片的路径 支持 fs:// widget://；不传则不显示
	}
]
```

styles:

- 类型：JSON 对象类型
- share 对话框样式设置
- 内部字段：

```js
{
	 bg:'#FFF',      // 字符串类型；对话框的背景色，支持#、rgb、rgba、img；默认：#FFF
	 w：300,         // 数字类型；对话框的宽；默认值：300
	 h: 300,         // 数字类型；对话框的高；默认值：300
	 column: 3,      // 数字类型；支持的行数；默认值：3
	 align:'center'  // 字符串类型；对话框的相对位置，支持 center，top, bottom

	 itemText：{               // JSON对象类型，网格每一项文本设置
		 itemTextColor: "#000",  // 字符串类型；每一项的文本字体颜色设置，支持#、rgb、rgba；默认：#000
		 itemTextSize: 18,       // 字符串类型；每一项的文本字体大小设置；默认值：18
	 },
	 itemIcon:{            // JSON对象类型，每一项图片样式的设置
		 itemIconWidth: 30,  // 数字类型；图标宽；默认值：30
		 itemIconHeight: 30, // 数字类型；图标高；默认值：30
		 marginTop: 8        // 数字类型；上边距；默认值：8
	 }
}
```

##callback(ret)
ret:

- 类型：JSON对象
- 内部字段:

```js
{
	eventType : "click"，// 字符串类型；回调事件类型；只支持 click
	index : index        // 数字类型；点击项的索引
}
```

##示例代码
```js
var dialogBox = api.require('dialogBox');
dialogBox.share({
	datas:[
	{
		itemText: "微信",
		itemIcon: "widget://image/icon/weixin_icon.png"
	},
	{
		itemText: "QQ",
		itemIcon: "widget://image/icon/qq_icon.png"
	},
	{
		itemText: "微博",
		itemIcon: "widget://image/icon/weibo_icon.png"
	},
	{
		itemText: "短信",
		itemIcon: "widget://image/icon/shortmessage_icon.png"
	}
],
styles:{
	 bg:'#FFF',
	 w：300,
	 h: 300,
	 column: 3,
	 align:'center'

	 itemText：{
		 itemTextColor: "#000",
		 itemTextSize: 18,  
	 },
	 itemIcon:{
		 itemIconWidth: 30,
		 itemIconHeight: 30,
		 marginTop: 8
	 }
}}, function(ret){
	alert(JSON.stringify(ret));
});


##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
