/*
Title: dialogBox
Description: dialogBox
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<div class="outline">
[alert](#m1)

[sendMessage](#m2)

[scene](#m3)

[evaluation](#m4)

[raffle](#m5)

[taskPlan](#m6)

[receipt](#m7)

[tips](#m8)

[discount](#m9)

[share](#m10)

[actionMenu](#m11)

[close](#m12)

</div>

#**概述**

dialogBox 封装了十一种款式的对话框，每一种款式都提供一个接口来调用，开发者可按照各个接口的样式来自定义对话框上的文字、图片、图文等。后续我们会根据开发者需求继续添加若干样式对话框接口。每一种样式图展示如下，开发者可参考配置：

alert 样式如下图所示：

![alert](/img/docImage/dialogBox/alert1.png)
![alert](/img/docImage/dialogBox/alert2.png)
![alert](/img/docImage/dialogBox/alert3.png)

sendMessage 样式如下图所示：

![sendMessage](/img/docImage/dialogBox/sendMessage.png)

scene 样式如下图所示：

![scene](/img/docImage/dialogBox/scene1.png)
![scene](/img/docImage/dialogBox/scene2.png)

evaluation 样式如下图所示：

![evaluation](/img/docImage/dialogBox/evaluation.png)

raffle 样式如下图所示：

![raffle](/img/docImage/dialogBox/raffle1.png)
![raffle](/img/docImage/dialogBox/raffle2.png)
![raffle](/img/docImage/dialogBox/raffle3.png)

taskPlan 样式如下图所示：

![taskPlan](/img/docImage/dialogBox/taskPlan.png)

receipt 样式如下图所示：

![receipt](/img/docImage/dialogBox/receipt.png)

tips 样式如下图所示：

![tips](/img/docImage/dialogBox/tips.png)

discount 样式如下图所示：

![discount](/img/docImage/dialogBox/discount.png)

share 样式如下图所示：

![share](/img/docImage/dialogBox/share.png)

actionMenu 样式如下图所示：

![actionMenu](/img/docImage/dialogBox/actionMenu1.png)
![actionMenu](/img/docImage/dialogBox/actionMenu2.png)

弹出的对话框都可以通过调用 close 接口来关闭。

##**模块接口**

<div id="m1"></div>
#**alert**

弹出 alert 样式的对话框

alert({params}, callback(ret, err))

##params

texts：

- 类型：JSON 对象
- 描述：（可选项）alert 对话框模块可配置的文本
- 内部字段：

```js
{
	title: '确认',          //（可选项）字符串类型；标题内容，若不传则不显示该文本
	content:'这里是文本内容', //（可选项）字符串类型：对话框文本内容，文本所占区域的高度随字文本多少自适应，若不传则不显示该文本
	leftBtnTitle: '取消',   //（可选项）字符串类型；左边按钮标题，若不传则不显示该文本
	rightBtnTitle: '确认'   //（可选项）字符串类型；右边按钮标题，若不传则不显示该文本
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
	title:{                //（可选项）JSON对象；弹窗标题栏样式配置，不传则不显示标题区域
		marginT: 20,       //（可选项）数字类型；标题栏与对话框顶端间距；默认：20
		icon: '',          //（可选项）字符串类型；标题前面的图标路径，要求本地路径（widget://、fs://）；图片为正方形的，如：50*50、100*100，建议开发者传大小合适的图片以适配高分辨率手机屏幕，不传则不显示
		iconSize: 40,      //（可选项）数字类型；icon 图标边长大小,若 icon 不存在则此参数无效；默认：24
		titleSize: 14,     //（可选项）数字类型；标题字体大小；默认：14
		titleColor: '#fff' //（可选项）字符串类型；标题字体颜色，支持#、rgb、rgba；默认：#fff
	},
	content:{              //（可选项）JSON 对象；文本内容配置，若不传则不显示该区域
		marginT: 20,       //（可选项）数字类型；内容文本顶端与标题栏底端的距离，如果标题栏不存在，则是到窗口顶端的距离；默认：20
		marginB: 20,       //（可选项）数字类型；内容文本底端与 left/right 顶端的距离，如果 left/right 都不存在，则是到对话框底端的距离；默认：20
		color: '#eee',     //（可选项）字符串类型；内容文本字体颜色，支持 rgb、rgba、#；默认：#eee
		size: 12           //（可选项）数字类型：内容文本字体大小；默认：12
	},
	left:{                 //（可选项）JSON 对象；左边按钮样式配置，不传则不显示左边按钮
		marginB: 7,        //（可选项）数字类型；左边按钮的下边距；默认：7
		marginL: 20,       //（可选项）数字类型；左边按钮的左边距；默认：20
		w: 130,            //（可选项）数字类型；左边按钮的宽；默认：130
		h: 35,             //（可选项）数字类型；左边按钮的高；默认：35
		corner: 2,         //（可选项）数字类型；左边按钮圆角半径；默认：0.0
		bg: '#e0e',        //（可选项）字符串类型；左边按钮的背景，支持rgb、rgba、#、img；默认：'#e0e'
		color: '#007FFF',  //（可选项）字符串类型；左边按钮标题字体颜色，支持rgb，rgba、#；默认：'#007FFF'
		size: 12           //（可选项）数字类型；左边按钮标题字体大小；默认：12
	},
	right: {               //（可选项）JSON 对象；右边按钮样式配置，不传则不显示右边按钮
		marginB: 7,        //（可选项）数字类型；右边按钮的下边距；默认：7
		marginL: 10,      //（可选项）数字类型；右边按钮左边距；默认：10
		w: 130,            //（可选项）数字类型；右边按钮的宽；默认：130
		h: 35,             //（可选项）数字类型；右边按钮的高；默认：35
		corner: 2,         //（可选项）数字类型；右边按钮圆角半径；默认：0.0
		bg: '#e0e',        //（可选项）字符串类型；右边按钮的背景，支持rgb、rgba、#、img；默认：'#e0e'
		color: '#007FFF',  //（可选项）字符串类型；右边按钮标题字体颜色，支持rgb、rgba、#；默认：'#007FFF'
		size: 12           //（可选项）数字类型；右边按钮标题字体大小；默认：12
	}
}
```
##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	eventType: 'left',     //字符串类型；交互事件类型，取值范围如下：
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
	},
	styles:{
		bg: '#fff',
		w: 300,
		title:{   
			icon: 'widget://image/dialogBox/alert.png',  
			size: 16,      
			color: '#000'    
		},
		content:{  
			color: '#000',     	
			size: 14  		
		},
		left:{            
			marginB: 7,      
			marginL: 20,     
		    w: 130,           
		    h: 35,
		    corner: 2,       
		    bg: '#e0e',   
		    size: 12    
		},
		right:{            
			marginB: 7,      
			marginL: 10,      
		    w: 130,           
		    h: 35,
		    corner: 2,       
		    bg: '#e0e',   
		    size: 12    
		}
	}
},function(ret){
    api.alert({msg:JSON.stringify(ret)});
    if (ret.eventType == 'left') {
        var dialogBox = api.require('dialogBox');
        dialogBox.close ({
            dialogName: 'alert'
        });
    }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m2"></div>
#**sendMessage**

弹出 sendMessage 样式的对话框

sendMessage({params}, callback(ret, err))

##params

texts：

- 类型：JSON 对象
- 描述：（可选项）sendMessage 对话框模块可配置的文本
- 内部字段：

```js
{
	title: '昵称',               //（可选项）字符串类型；标题栏显示文本内容，若不传则不显示该文本
	hintText: '（请输入）',       //（可选项）字符串类型；标题栏输入框默认文本，若不传则不显示该文本  
	content: '内容文本',          //（可选项）字符串类型；对话框文本内容，该区域大小随文本内容多少自适应，若不传则不显示该文本
	leftBtnTitle: '取消',        //（可选项）字符串类型；左边按钮标题，若不传则不显示该文本
	rightBtnTitle: '发送'        //（可选项）字符串类型；右边按钮标题，若不传则不显示该文本
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
	title:{                     //（可选项）JSON 对象；弹窗的 title 样式配置，不传则不显示标题区域
		h: 60,                  //（可选项）数字类型；标题栏高度；默认：60
		show: {                 //（可选项）JSON 对象；标题栏显示文字样式配置
			marginL: 6,         //（可选项）数字类型；显示文本相对于标题栏左边的距离；默认：6
			titleSize: 14,      //（可选项）数字类型；标题字体大小；默认：14
			titleColor: '#000'  //（可选项）字符串类型；标题字体颜色，支持#、rgb、rgba；默认：#000
		},
		input:{                 //（可选项）JSON 对象；标题栏输入文本框样式配置
			marginL: 6,         //（可选项）数字类型；输入文本框相对于显示文本的距离，若显示文本不存在，则是与标题栏左边的距离；默认：6
			textSize: 14,       //（可选项）数字类型；输入文本框文本字体大小；默认：14
			textColor: '#000'   //（可选项）字符串类型；输入文本框文本字体颜色，支持#、rgb、rgba；默认：#000
		}
	},
	content:{                   //（可选项）JSON 对象；文本内容配置，若不传则不显示该区域
		marginT: 20,            //（可选项）数字类型；内容文本顶端与标题栏底端的距离，如果标题栏不存在，则是到窗口顶端的距离；默认：20
		marginB: 20,            //（可选项）数字类型；内容文本底端与 left/right 顶端的距离，如果 left/right 都不存在，则是到对话框底端的距离；默认：20
		color: '#eee',          //（可选项）字符串类型；内容文本字体颜色，支持 rgb、rgba、#；默认：#eee
		size: 12                //（可选项）数字类型：内容文本字体大小；默认：12
	},
	left:{                      //（可选项）JSON 对象；左边按钮样式配置，不传则不显示左边按钮
		marginB: 7,             //（可选项）数字类型；左边按钮的下边距；默认：7
		marginL: 20,            //（可选项）数字类型；左边按钮的左边距；默认：20
		w: 130,                 //（可选项）数字类型；左边按钮的宽；默认：130
		h: 35,                  //（可选项）数字类型；左边按钮的高；默认：35
		corner: 2,              //（可选项）数字类型；左边按钮圆角半径；默认：0.0
		bg: '#e0e',             //（可选项）字符串类型；左边按钮的背景，支持rgb、rgba、#、img；默认：'#e0e'
		color: '#007FFF',       //（可选项）字符串类型；左边按钮标题字体颜色，支持rgb，rgba、#；默认：'#007FFF'
		size: 12                //（可选项）数字类型；左边按钮标题字体大小；默认：12
	},
	right: {                    //（可选项）JSON 对象；右边按钮样式配置，不传则不显示右边按钮
		marginB: 7,             //（可选项）数字类型；右边按钮的下边距；默认：7
		marginL: 10,            //（可选项）数字类型；右边按钮的左边距；默认：10
		w: 130,                 //（可选项）数字类型；右边按钮的宽；默认：130
		h: 35,                  //（可选项）数字类型；右边按钮的高；默认：35
		corner: 2,              //（可选项）数字类型；右边按钮圆角半径；默认：0.0
		bg: '#e0e',             //（可选项）字符串类型；右边按钮的背景，支持rgb、rgba、#、img；默认：'#e0e'
		color: '#007FFF',       //（可选项）字符串类型；右边按钮标题字体颜色，支持rgb、rgba、#；默认：'#007FFF'
		size: 12                //（可选项）数字类型；右边按钮标题字体大小；默认：12
	}
}
```
##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	eventType: 'left',        //字符串类型；交互事件类型，取值范围如下：
                              // left（表示用户点击了左边按钮）
                              // right（表示用户点击了右边按钮）
    text: ''                  //字符串类型；输入文本框当前的值
}
```

##示例代码

```js
var dialogBox = api.require('dialogBox');
dialogBox.sendMessage ({
	texts:{
		title: '你的昵称',
		hintText: '（点击此处修改昵称）',          
		content:'亲，送你一个80元大礼包，请查收！退订请回复TD',           
		leftBtnTitle: '取消',   
		rightBtnTitle: '发送'
	},
	styles:{
		bg: '#fff',
		w: 300,
		title:{                     
			h: 40,                
			show: {
				marginL: 6,
				titleSize: 14,
				titleColor: '#000'
			},
			input:{                
				marginL: 6,         
				textSize: 14,
				textColor: '#000'
			}
		},
		content:{  
			color: '#000',     	
			size: 12  		
		},
		left:{            
			marginB: 7,      
			marginL: 10,     
		    w: 130,           
		    h: 35,
		    corner: 2,       
		    bg: '#e0e',   
		    size: 12    
		},
		right:{            
			marginB: 7,      
			marginL: 10,      
		    w: 130,           
		    h: 35,
		    corner: 2,       
		    bg: '#e0e',   
		    size: 12    
		}
	}
},function(ret){
	api.alert({msg:JSON.stringify(ret)});
	if (ret.eventType == 'left') {
	    var dialogBox = api.require('dialogBox');
	    dialogBox.close ({
	        dialogName: 'sendMessage'
	    });
	}
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m3"></div>
#**scene**

弹出 scene 样式的对话框

scene({params}, callback(ret, err))

##params

rect:

- 类型：JSON 对象类型
- 描述：scene 对话框的尺寸配置, 上下左右居中对齐
- 内部字段：

```js
{
    w: 280,                     //（可选项）数字类型；弹出框的宽度；默认值：280
    h: 400                      //（可选项）数字类型；弹出框的高度；默认值：400
}
```
texts：

- 类型：JSON 对象
- 描述：（可选项）scene对话框模块可配置的文本
- 内部字段：

```js
{
	title: '确认',              //（可选项）字符串类型；标题内容，若不传则不显示该文本
	content:'场景',             //（可选项）字符串类型；对话框文本内容，若不传则不显示该文本
	okBtnTitle: '取消'          //（可选项）字符串类型；底部按钮标题，若不传则不显示该文本
}
```

styles:

- 类型：JSON 对象；
- 描述：scene 对话框样式设置
- 内部字段

```js
{
	bg: '#fff',                        //（可选项）字符串类型；对话框整体背景颜色配置，支持#、rgb、rgba、img；默认：#fff
	title:{                            //（可选项）JSON 对象；弹窗 title 样式配置，不传则不显示
		bg: '#aaa',                    //（可选项）字符串类型；标题栏背景颜色配置，支持 #、rgb、rgba；默认：#aaa
		h: 44,                         //（可选项）数字类型；标题栏高度，默认：44
		size: 14,        	           //（可选项）数字类型；标题字体大小；默认：14
		color: '#000'      	           //（可选项）字符串类型；标题字体颜色，支持#、rgb、rgba；默认：#000
	},
	sceneImg:{                         //（可选项）JSON 对象；场景图片样式配置，不传则不显示
		h: 150,                        //（可选项）场景图片高度；默认：150
		path: ''                       // 字符串类型；场景图片路径（要求本地路径（widget://、fs://	）
	},
	content:{                          //（可选项）JSON 对象；文本内容样式配置，不传则不显示该区域
		color: '#111',                 //（可选项）字符串类型；文本字体颜色,支持 rgb、rgba、#；默认：#111
		size: 12                       //（可选项）数字类型；文本字体大小；默认：12
	},
	cell: {                            //（可选项）JSON 对象；情景事件选项每一行的样式配置，与 optionDatas 搭配使用，若 optionDatas 不存在则此配置无效
    	bg: '#fff',                    //（可选项）字符串类型；情景事件选项每一行的背景，支持rgb、rgba、#、img；默认：#fff
    	h: 48,                         //（可选项）数字类型；情景事件选项每一行的高度；默认：48
    	icon: {                        //（可选项）JSON 对象；情景事件选项每一行图标的样式配置；与 optionDatas->icon 配合使用，若 optionDatas->icon 不存在则忽略此配置，不显示该行的图标区域
    		marginL: 15,               //（可选项）数字类型；图标相对于分组子项左端的间距大小；默认：15
    		marginT: 9,                //（可选项）数字类型；图标相对于分组子项顶端的间距大小；默认：9
    		w: 30,                     //（可选项）数字类型；图标的宽度；默认：30
    		h: 30,                     //（可选项）数字类型；图标的高度；默认：同 w
    		corner: 2                  //（可选项）数字类型；图标的圆角半径；默认：2
    	},
    	text: {                        //（可选项）JSON 对象；情景事件选项每一行文字样式配置，事件选项文字会自己上下居中显示，与 optionDatas->text 配合使用，若 optionDatas->text 不存在则忽略此配置，不显示该行的文本区域
	    	interval:10,               //（可选项）数字类型；事件选项文本与左边图标的间距；默认：10
	    	size: 14,                  //（可选项）数字类型；事件选项文本字体大小；默认：14
    		color: '#636363',          //（可选项）字符串类型；事件选项文本文字颜色，支持rgb、rgba、#；默认：#636363
    		align: 'left'              //（可选项）字符串类型；事件选项文本文字对齐方式，可为 left|center|right；默认：left
    	},
    	lineColor: '#eee'              //（可选项）字符串类型；分隔线的颜色，支持：rgb、rgba、#；默认：'#eee'
	},
	ok: {                              //（可选项）JSON 对象；底部确认按钮的样式配置，不传则不显示底部按钮
		h: 20,                         //（可选项）数字类型；底部按钮的高度；默认：20
		bg: '#89a',                    //（可选项）字符串类型；底部按钮的背景颜色，支持：rgb、rgba、#；默认：'#89a'
		titleColor: '#f00',            //（可选项）字符串类型；底部按钮 title 文字颜色，支持：rgb、rgba、#；默认：'#f00'     
		titleSize: 14                  //（可选项）数字类型；底部按钮 title 文字大小；默认：14
    }
}
```
optionDatas:

- 类型：数组类型
- 描述：（可选项）场景事件选项数据源，若为空则不显示
- 内部字段：

```js
[
	{                                //（可选项）数组类型；该场景每一项的数据
		icon: 'fs://creater.png',    //（可选项）字符串类型；图标地址，支持本地和网络资源路径（widget://、fs://），不传则不显示该行的图标
		text: '事件选项文字'           //（可选项）字符串类型；事件选项文字，不传则不显示该行文本
	}
]
```
##callback(ret, err)
ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    eventType: 'ok',    // 字符串类型；交互事件类型，取值范围如下：
                        // ok：用户点击了 ok 按钮
                        // cell：用户点击了 cell 按钮
	index: 1            // 数字类型；表示用户点击了的选项的索引
}
```

##示例代码

```js
var dialogBox = api.require('dialogBox');
dialogBox.scene ({
	rect: {                            
	    w: 280,                            
	    h: 400                             
	},
	texts: {
		title: '情景1',          
		content:'火车售票处前的队伍蜿蜒纵横，旁边一小伙一边张望，一边将手伸向前面买票人的口袋，啊，是小偷!',         
		okBtnTitle: '确定'
	},
	styles: {
		bg:'#fff',
		title:{     
			bg: '#aaa',     
			h: 44,       	 
			size: 14,        
			color: '#000'    
		},
		sceneImg: {
			h: 150,          
			path: 'widget://image/sceneImg.png'        
		},
		content:{
			color: '#111',         			
			size: 12        
		},
	    cell: {      
	    	bg: '#fff',                    
	    	h: 48,                         
	    	text: {                        
	    		color: '#636363',          
	    		size: 13                 
	    	},
	    	icon: {                       
	    		marginL: 15,              
	    		marginT: 9,                
	    		w: 30,                     
	    		h: 30,                     
	    		corner: 2                 
	    	}
		},
		ok: {
	    	bg: '#89a',                
			titleColor: '#f00'    
    	}
	},
	optionDatas: [
		{           
		    icon: 'widget://image/scene1.png',                
		    text: '1、拿出手机偷拍'            
		},
		{       
		    icon: 'widget://image/scene2.png',
		    text: '2、见义勇为抓小偷'            
		},
		{       
		    text: '3、大声提醒买票的人'            
		}
	]
}, function(ret, err){
	if( ret ){
        alert(JSON.stringify(ret));
	}else{
        alert(JSON.stringify(err));
	}
});
```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m4"></div>
#**evaluation**

弹出 evaluation 样式的对话框

evaluation({params}, callback(ret, err))

##params

styles:

- 类型：JSON 对象
- 描述：evaluation 对话框样式配置
- 内部字段：

```js
{
	bg: '#fff',             //（可选项）字符串类型；标题字体颜色，支持#、rgb、rgba、img，默认：#fff
	w: 300,                 //（可选项）数字类型；对话框的宽；默认 300
	title:{                 //（可选项）JSON 对象；对话框标题栏样式配置，若不传则不显示标题区域
		marginT: 20,        //（可选项）数字类型；标题栏顶部与弹出框顶部距离；默认 20
		size: 14,           //（可选项）数字类型；标题字体大小；默认：14
		color: '#000',      //（可选项）字符串类型；标题字体颜色，支持 #、rgb、rgba；默认：#000
		bold: true          //（可选项）布尔类型；标题字体是否是粗体；默认：true
	},
	content:{               //（可选项）JSON 对象；文本内容样式配置；不传则不显示文本区域
		marginT: 20,        //（可选项）数字类型；文本顶端与标题栏底端的间距，如果标题栏不存在，则是到弹出框顶端的距离；默认20
		marginB: 20,        //（可选项）数字类型；文本底端与底端首个按钮的间距，若底部不存在按钮，则是到弹出框底端的距离；默认：20
		color: '#111',      //（可选项）字符串类型：文本字体颜色,支持 rgb、rgba、#；默认：#111
		size: 12            //（可选项）数字类型：文本数字类型；默认：12
	},
	buttons:[{              //（可选项）数组类型；JSON 对象组成的数组，和texts中buttons数组长度保持一致。按钮样式配置,不传则不显示 button 区域
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
	title: '确认',          //（可选项）字符串类型；标题内容，若不传则不显示该文本
	content:'场景',         //（可选项）字符串类型；对话框文本内容，文本区域大小随文本多少自适应，若不传则不显示该文本
	buttons: [{            //（可选项）数组类型；按钮显示文字组成的数组，和styles中buttons数组长度保持一致。由上往下排列（最上边的按钮索引为0）
		text: '取消'        //（可选项）字符串类型；按钮显示文字；默认：未设置时只显示背景
	}]
}
```
##callback(ret, err)
ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	index: 1           //数字类型；表示用户点击了的按钮的索引，由上往下排列（最上边的按钮索引为 0）
}
```

##示例代码
```js
var dialogBox = api.require('dialogBox');
dialogBox.evaluation ({
	styles: {
		bg: '#fff',
		w: 300,
		title:{
			marginT: 20,
			size: 15,
			color: '#000',
			bold: true
		},
		content:{               
			marginT: 20,     
			color: '#111',
			size: 12
		},
		buttons:[{
			marginB: 0,
			marginL: 0,
			w: 300,
			h: 35,
			bg: '#fff',
			color: '#007FFF',
			size: 12
		},
		{
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
		content:'亲，给个好评吧',         
		buttons: [
		{            
			text: '下次再说'
		},
		{
		   text: '残忍的拒绝'
		}]
	}
}, function(ret, err){
	if( ret ){
        alert(JSON.stringify(ret));
	}else{
        alert(JSON.stringify(err));
	}
});
```
##可用性

iOS系统，Android系统

可提供的 1.0.0 及更高版本

<div id="m5"></div>
#**raffle**

弹出 raffle 样式的对话框

raffle({params}, callback(ret, err))

##params

texts：

- 类型：JSON 对象
- 描述：（可选项）raffle 对话框模块可配置的文本
- 内部字段：

```js
{
	title: '确认',          //（可选项）字符串类型；标题内容，若不传则不显示该文本
	mainText: '收入囊中',    //（可选项）字符串类型；主文本内容，若不传则不显示该文本
	subText: '告诉好友',     //（可选项）字符串类型；副文本内容，若不传则不显示该文本
	leftTitle: '取消',      //（可选项）字符串类型；左边按钮标题，若不传则不显示该文本
	rightTitle: '确定'      //（可选项）字符串类型；左边按钮标题，若不传则不显示该文本
}
```
styles:

- 类型：字符串
- 描述：raffle 对话框样式设置
- 内部字段：

```js
{
	bg: '#fff',                //（可选项）字符串类型；标题字体颜色，支持#、rgb、rgba、img；默认：#fff
	w: 300,                    //（可选项）数字类型；对话框的宽；默认 300
	title:{                    //（可选项）JSON 对象；弹窗标题栏样式配置，若不传则不显示标题区域
		size: 14,              //（可选项）数字类型；标题字体大小；默认：14
		color: '#000'          //（可选项）字符串类型；标题字体颜色，支持#、rgb、rgba；默认：#000
	},
	icon:{                     //（可选项）JSON 对象；图标样式配置，不传则不显示该插图区域
		marginT: 20,           //（可选项）数字类型；图标顶端与标题栏底端的距离，图标左右居中显示；默认：20
		w: 40,                 //（可选项）数字类型；图标宽度；默认：40
		h: 40,                 //（可选项）数字类型；图标高度；默认：40
		iconPath: 'widget://'  // 字符串类型；图标路径，要求本地路径（widget://、fs://）；
	},
	main: {                    //（可选项）JSON 对象；主文本样式设置，主文本会左右居中显示，若不传则不显示主文本区域
		marginT: 20,           //（可选项）数字类型；主文本相对于 icon 底端的间距大小；默认：20
		color: '#636363',      //（可选项）字符串类型；主文本文字颜色，支持rgb、rgba、#；默认：#636363
		size: 13               //（可选项）数字类型；主文本字体大小；默认：13
	},
	sub: {                     //（可选项）JSON 对象；副文本样式设置，副文本会左右居中显示，若不传则不显示富文本区域
		marginT: 8,            //（可选项）数字类型；副文本和主文本之间的间隙大小；默认：8
		color: '#999999',      //（可选项）字符串类型；副文本文字颜色，支持 rgb、rgba、#；默认：#999999
		size: 12               //（可选项）数字类型；副文本字体大小；默认：12
	},
	left:{                     //（可选项）JSON 对象；左边按钮样式设置, 不传则不显示左边按钮
		marginB: 7,            //（可选项）数字类型；左边按钮的下边距；默认：7
		marginL: 18,           //（可选项）数字类型；左边按钮的左边距；默认：18
		w: 90,                 //（可选项）数字类型；左边按钮的宽；默认：90
		h: 35,                 //（可选项）数字类型；左边按钮的高；默认：35
		corner: 0.0,           //（可选项）数字类型；左边按钮圆角半径；默认：0.0
		bg: '#fff',            //（可选项）字符串类型；左边按钮的背景，支持rgb，rgba，#，img；默认：'#fff'
		color: '#007FFF',      //（可选项）字符串类型；左边按钮显示文字颜色，支持rgb，rgba,#；默认：'#007FFF'
		size: 12               //（可选项）数字类型；左边按钮显示文字的大小；默认：12
	},
	right: {                   //（可选项）JSON 对象；右边按钮样式设置，不传则不显示右边按钮
		marginB: 7,            //（可选项）数字类型；右边按钮的下边距；默认：7
		marginL: 18,           //（可选项）数字类型；右边按钮的左边距；默认：18
		w: 90,                 //（可选项）数字类型；右边按钮的宽；默认：90
		h: 35,                 //（可选项）数字类型；右边按钮的高；默认：35
		corner: 0.0,           //（可选项）数字类型；右边按钮圆角半径；默认：0.0
		bg: '#fff',            //（可选项）字符串类型；右边按钮的背景，支持rgb，rgba，#，img；默认：'#fff'
		color: '#007FFF',      //（可选项）字符串类型；右边按钮显示文字颜色，支持rgb，rgba,#；默认：'#007FFF'
		size: 12               //（可选项）数字类型；右边按钮显示文字的大小；默认：12
	}
}
```
##callback(ret, err)

ret：

- 类型：JSON 对象
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
		rightTitle: '告诉好友'   
	},
	styles: {
		bg: '#fff',               
		w: 300,                     
		title:{                    
			size: 14,             
			color: '#000'         
		},
		icon:{         
			marginT: 20,           
			w: 40,                 
			h: 40,               
			iconPath:'widget://image/raffle.png'           
		},
	    main: {                   
	        marginT: 20,          
	        color: '#636363',      
	        size: 13            
	    },
	    sub: {                     
	        marginT: 8,      
	        color: '#999999',
	        size: 12   
	    },
		left:{      
			marginB: 7,
			marginL: 18,
			w: 130,
			h: 35,
			corner: 2,        
			bg: '#fff',     
			color: '#007FFF',
			size: 12
		},
		right: {    
			marginB: 7,   
			marginL: 18,
			w: 130,  
			h: 35,   
			corner: 2,  
			bg: '#fff',
			color: '#007FFF',  
			size: 12              
		}
	}
}, function(ret, err){
	if( ret ){
        alert(JSON.stringify(ret));
	}else{
        alert(JSON.stringify(err));
	}
});
```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m6"></div>
#**taskPlan**

弹出 taskPlan 样式的对话框

taskPlan({params}, callback(ret, err))

##params

rect：

- 类型：JSON 类型
- 描述：（可选项）taskPlan 对话框的宽度配置
- 内部字段：

```js
{
    w: 300                    //（可选项）数字类型；对话框的宽度；默认值：300
}
```
texts：

- 类型：JSON 对象
- 描述：（可选项）taskPlan 对话框模块可配置的文本
- 内部字段：

```js
{
	mainTitle: '主标题',       //（可选项）字符串类型；主标题，若不传则不显示主标题内容
	subTitle: '副标题',        //（可选项）字符串类型；副标题，若不传则不显示副标题内容
	content: [{               //（可选项）数组类型；各行文本内容，若不传则不显示该文本
	   text: ''               // 字符串类型；每一行文本内容
	}],
	btnTitle: '确定'           //（可选项）字符串类型；底部按钮标题，若不传则底部按钮不显示标题
}
```
styles:

- 类型：JSON 对象类型
- 描述：taskPlan 对话框样式设置
- 内部字段：

```js
{
	bg: '#fff',                //（可选项）字符串类型；标题字体颜色，支持#、rgb、rgba、img，默认：#fff
	main: {                    //（可选项）JSON 对象；主标题样式设置，主文本会左右居中显示，若不传则不显示主标题区域
        marginT: 20,           //（可选项）数字类型；主标题相对于弹出框顶部的间距大小；默认：20
        color: '#636363',      //（可选项）字符串类型；主标题文字颜色，支持rgb、rgba、#；默认：#636363
        size: 13,              //（可选项）数字类型；主标题字体大小；默认：13
        bold: true             //（可选项）布尔类型；主标题字体粗体显示，true | false；默认：true
    },
    sub: {                     //（可选项）JSON 对象；副标题样式设置，副文本会左右居中显示，若不传则不显副标题区域
        marginT: 8,            //（可选项）数字类型；副标题和主文本之间的间隙大小；默认：8
        color: '#999999',      //（可选项）字符串类型；副标题文字颜色，支持 rgb、rgba、#；默认：#999999
        size: 12,              //（可选项）数字类型；副标题字体大小；默认：12
    },
    content: [{                //（可选项）数组类型；每一行内容的样式组成的数组，从上往下排列，若不传则不显示内容区域
		bg: '#fff',            //（可选项）字符串类型；文本内容背景颜色，支持rgb，rgba,#；默认：'#fff'
		marginT: 10,           //（可选项）数字类型；文本相对于弹出框顶端的间距大小；默认：10
		w: 280,                //（可选项）数字类型；文本宽度；默认：280
		h: 30 ,                //（可选项）数字类型；文本高度；默认：30
		align: 'left',         //（可选项）字符串类型；文本对齐方式，left | center | right；默认：left
		color: '#007FFF',      //（可选项）字符串类型；按钮显示文字颜色，支持rgb，rgba,#；默认：'#007FFF'
		size: 12               //（可选项）数字类型；按钮显示文字的大小；默认：12
	}],
	ok: {                      // JSON 对象；底部按钮样式设置
		marginT: 10,           //（可选项）数字类型；按钮的上边距；默认：10
		marginB: 10,           //（可选项）数字类型；按钮的下边距；默认：10
		marginL: 20,           //（可选项）数字类型；按钮的左边距；默认：20
		w: 280,                //（可选项）数字类型；按钮的宽；默认：280
		h: 35,                 //（可选项）数字类型；按钮的高；默认：35
		bg: '#fff',            //（可选项）字符串类型；按钮的背景，支持rgb，rgba，#，img；默认：'#fff'
		color: '#007FFF',      //（可选项）字符串类型；按钮显示文字颜色，支持rgb，rgba,#；默认：'#007FFF'
		size: 12               //（可选项）数字类型；按钮显示文字的大小；默认：12
	}
}
```
##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	eventType: 'ok'               // 字符串类型；交互事件类型，取值范围如下：
                                  // ok（表示用户点击了底部按钮）
}
```
##示例代码
```js
var dialogBox = api.require('dialogBox');
dialogBox.taskPlan ({
    rect: {
        w: 300    
    },
    texts:{
        mainTitle: '昨天玩的不够努力哦',
        subTitle: '今天没有获得任务次数奖励呢',       
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
            marginT: 20,           
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
            bg: '#f00', 
            marginT: 10,         
            w: 280,                
            h: 30,                
            align: 'center',         
            color: '#007FFF',      
            size: 12               
        },
        {                
            bg: '#fff',  
            marginT: 10,         
            w: 280,                
            h: 30,                
            align: 'left',         
            color: '#007FFF',      
            size: 12               
        }],
        ok: {                 
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
    if (ret.eventType == 'ok') {
        var dialogBox = api.require('dialogBox');
        dialogBox.close ({
            dialogName: 'taskPlan'
        });
    }
});
```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m7"></div>
#**receipt**

弹出 receipt 样式的对话框

receipt({params}

##params

rect:

- 类型：JSON 数组类型
- 描述：（可选项）对话框的宽高设置
- 内部字段：

```js
{            
	 w:200,               //（可选项）数字类型；弹出框的宽度；默认值：200
	 h:300                //（可选项）数字类型；弹出框的宽度；默认值：300
}
```

texts:

- 类型：JSON 数组类型
- 描述：对话框按钮或标题的文本设置
- 内部字段：

```js
{
	 title:'标题',        //（可选项）字符串类型；标题内容；不传则不显示该文本
	 cancel:'取消',       //（可选项）字符串类型；取消按钮文本配置；不传则不显示该文本
}
```

items:

- 类型：JSON 数组类型
- 描述：对话框列表的显示数据
- 内部字段：

```js
[
	{
		key   :  '起步价', // 字符串类型；列表标题内容；不传则不显示该文本
		value :  '0.00'   // 字符串类型；列表描述内容；不传则不显示该文本
	}
]
```

styles:

- 类型：JSON 对象类型
- 描述：（可选项）对话框样式设置
- 内部字段：

```js
{
	 bg:'#FFF',                 //（可选项）字符串类型；对话框的背景色，支持#、rgb、rgba、img；默认：#FFF
	 title:{                    //（可选项）JSON对象类型；对话框标题设置，若不传则不显示标题区域
		 textColor:'#000',      //（可选项）字符串类型；标题的字体颜色；支持#、rgb、rgba；默认值：#000
		 textSize:18,           //（可选项）数字类型；标题的字体大小；默认值：18
		 marginT:18             //（可选项）数字类型；标题的距离对话框顶部的距离；默认值：18
	 },
	 topBorder:{                //（可选项）JSON对象类型；上分割线的设置
		 borderColor:'#000',    //（可选项）字符串类型；边界线颜色，支持#、rgb、rgba；默认：#000
		 borderWidth: 2,        //（可选项）数字类型；边界线的粗细，默认值：2
		 marginT: 10            //（可选项）数字类型；边界线的距离标题的下边距的距离，默认值：10
	 },
	 listHeight: 200,           //（可选项）数字类型；列表的高度；默认值：200
	 item:{                     //（可选项）JSON对象类型；列表项的设置
		 textColor: '#000',     //（可选项）字符串类型；列表的字体颜色，支持#、rgb、rgba；默认值：#000
		 textSize : 18,         //（可选项）数字类型；列表的字体大小；默认值：18
		 marginL:10,            //（可选项）数字类型；列表key值距离列表左边的距离；默认值：10
		 marginT:10,            //（可选项）数字类型；key,value值距离每项顶部的距离；默认值：10
		 marginB:10,            //（可选项）数字类型；key,value值列表距离每项底部的距离；默认值：10
		 marginR:10,            //（可选项）数字类型；value值距离列表右边的距离；默认值：10
		 bgColor:'#FFF'         //（可选项）字符串类型；列表项的背景颜色，支持#、rgb、rgba；默认值：#FFF
	 },
	 bottomBorder:{             //（可选项）JSON对象类型；下分割线的设置
		 borderColor:'#000',    //（可选项）字符串类型；边界线颜色，支持#、rgb、rgba；默认值：#000
		 borderWidth: 2         //（可选项）数字类型；边界线的粗细；默认值：2
	 },
	 cancel:{                   //（可选项）取消按钮样式设置
		h: 35,                  //（可选项）数字类型；取消按钮高度；默认值：35
		textSize: 18,           //（可选项）数字类型；取消按钮字体大小；默认值：18
		textColor:'#000',       //（可选项）字符串类型；取消按钮字体颜色，支持#、rgb、rgba；默认值：#000
		marginT: 10 ,           //（可选项）数字类型；取消按钮距离弹框下分割线的距离；默认值：10
		normal: '#ffffff',      //（可选项）字符串类型；取消按钮的背景设置，支持rgb、rgba、#、img；默认：#ffffff
		highlight: '#696969'    //（可选项）字符串类型；取消按钮的背景高亮设置，支持rgb、rgba、#、img；默认：#696969
	 }
}
```

##callback(ret, err)

ret:

- 类型：JSON 对象
- 内部字段：

```js
{
	eventType : 'cancel'        // 字符串类型；返回的事件类型, 用户点击了底部的 cancel 按钮
}
```

##示例代码
```js
var dialogBox = api.require('dialogBox');
dialogBox.receipt({
    rect:{
         w:300,
         h:360
    },
    items:[
        {
            key   : '起步价',
            value : '15.00'
        },
        {
            key   : '15公里',
            value : '50.10'
        },
        {
            key   : '9.98分钟',
            value : '19'
        },
        {
            key   : '小计',
            value : '69'
        },
        {
            key   : '优惠',
            value : '10'
        },
        {
            key   : '已消费',
            value : '69.0'
        }
    ],
    texts:{
         title:'我的打车收据',        
         cancel:'取消'
    },
    styles:{
         bg:'#FFF',
         title:{
             textColor:'#000',
             textSize:18,
             marginT:10
         },
         topBorder:{  
             borderColor:'#000',
             borderWidth: 2,
             marginT: 10
         },
         listHeight: 260,
         item:{                                     
             textColor: '#000',     
             textSize: 14,        
             marginL: 10,            
             marginT: 5,  
             marginB: 5,         
             bgColor: '#FFF'  
         },
         bottomBorder:{
             borderColor:'#000',
             borderWidth: 2,
         },
         cancel:{
            textSize: 18,
            textColor:'#f00',
            marginT: 10,
            highlight: '#696969'  
         }
    }
}, function(ret, err){
	if( ret ){
        alert(JSON.stringify(ret));
	}else{
        alert(JSON.stringify(err));
	}
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m8"></div>
#**tips**

弹出 tips 样式的对话框

tips({params}

##params

rect:

- 类型：JSON 对象类型
- 描述：（可选项）对话框的宽高设置
- 内部字段：

```js
{
	 w:200                      //（可选项）数字类型；弹出框的宽度；默认值：200
}
```

texts:

- 类型：JSON 对象类型
- 描述：对话框标题和按钮的文本设置
- 内部字段：

```js
{
	title  : '这里是标题文本',    //（可选项）字符串类型；标题文本，不传则不显示该文本
	content: '这里是内容'        //（可选项）字符串类型；内容文本；不传则不显示该文本
}
```

buttons:

- 类型：JSON 数组类型
- 描述：底部按钮的文本设置
- 内部字段：

```js
[{
	 normal : 'widget://image/icon.png',      // 字符串类型；按钮常态图标的路径，支持 widget:// fs://
	 highlight : 'widget://image/icon.png',   // 字符串类型；按钮高亮图标的路径，支持 widget:// fs://
	 text :  '微信'                            //（可选项）字符串类型；按钮文本，不传则不显示该文本
}]
```

styles:

- 类型：JSON 对象类型
- 描述：对话框的样式设置
- 内部字段：

```js
{
	bg:'#FFF',                                //（可选项）字符串类型；对话框的背景色，支持#、rgb、rgba、img；默认：#FFF
	topImage:{                                //（可选项）顶部图标的样式设置，若不传则不显示顶部插图区域
		path:'widget://image/tipImage.png',   //（可选项）字符串类型；顶部图标的的路径，支持 (widget://、fs://)；不传则不显示该图片
		w: 200,                               //（可选项）数字类型；图标的宽度；默认值：200
		h: 80                                 //（可选项）数字类型；图标的高度；默认值：80
	},
	title:{                                   //（可选项）JSON对象类型；标题文本信息设置，若不传则不显示标题区域
		color: '#000',                        //（可选项）字符串类型；标题文本字体颜色，支持#、rgb、rgba；默认：#000
		size : 14,                            //（可选项）数字类型；标题文本字体大小；默认值：14
		marginT  : 15                         //（可选项）数字类型；距离顶部图标的上边距； 默认值：15
	},
	content:{                                 //（可选项）JSON对象设置；内容文本设置，该区域高度随内容大小自适应，若不传则不显示内容文本区域
		color : '#000',                       //（可选项）字符串类型；内容文本字体颜色，支持#、rgb、rgba；默认：#000
		size  : 12,                           //（可选项）数字类型；字体的大小；默认值：12
		marginT : 15                          //（可选项）数字类型；距离标题的上边距；默认值：15
	},
	border:{                                  // (可选项) 内容边框与下面按钮的分隔线设置
		color: '#eee',                        //（可选项）字符串类型；分割线的颜色，默认值：#eee
		width: 2,                             //（可选项）数字类型；分割线的粗细，默认值：2
		marginT: 15                           //（可选项）数字类型；距内容文本间的距离；默认值：15
	},
	buttons:[{                                //JSON对象类型；底部分享按钮设置
		iconSize : 30,                        //（可选项）数字类型；按钮图标的边长；默认值：30
		textColor:'#000',                     //（可选项）字符串类型 按钮文本字体颜色，字符串类型；标题文本字体颜色，支持#、rgb、rgba；默认：#000   
		textSize : 12,                        //（可选项）数字类型；按钮文本字体的大小；默认值：12
		marginT  : 15,                        //（可选项）数字类型；按钮与分割线间的距离；默认值：15  
		space    : 10                         //（可选项）数字类型；按钮之间的间隙；默认值：10
	}]
}
```
##callback(ret)

ret:

- 类型：JSON对象
- 内部字段：

```js
{
	index: 0               // 数字类型；点击按钮的索引（由左至右排列）
}
```

##示例代码
```js
var dialogBox = api.require('dialogBox');
dialogBox.tips({
	rect:{   
		 w:200
	},
	texts:{
		title  : '这里是标题文本',
		content: '这里是内容'
	},
	buttons:[
	{
		normal : 'widget://image/weixin.png',     
		highlight : 'widget://image/weixin.png',   
		text :  '微信' 
	},
	{
		normal : 'widget://image/circularMenu3.png',     
		highlight : 'widget://image/circularMenu3light.png',   
		text :  '奖杯'
	},
	{
		normal : 'widget://image/circularMenu4.png',     
		highlight : 'widget://image/circularMenu4light.png',   
		text :  '人民币'
	}],
	styles:{
		bg:'#FFF',
		topImage:{
			 path:'widget://image/top_image.png',
			 w: 200,
			 h: 80
		},
		title:{
			 color: '#000',
			 size : 14,
			 marginT  : 15
		},
		content:{
			 color:'#000',
			 size:12,
			 marginT:15
		},
		border:{    
			 color : '#eee',       
			 width: 2 ,
			 marginT: 10     
		},
		buttons:[
		{
			 iconSize : 30,
			 textColor: '#000',
			 textSize : 12,
			 marginT  : 15
		},
		{
			 iconSize : 30,
			 textColor: '#000',
			 textSize : 12,
			 marginT  : 15
		},
		{
			 iconSize : 30,
			 textColor: '#000',
			 textSize : 12,
			 marginT  : 15
		}]
	}
}, function(ret){
	alert(JSON.stringify(ret));
});
```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m9"></div>
#**discount**

弹出 discount 样式的对话框

discount({params}

##params

rect:

- 类型：JSON 对象类型
- 描述：（可选项）对话框的宽高设置
- 内部字段：

```js
{    
	 w:200,              //（可选项）数字类型；弹出框的宽度；默认值：200
	 h:300               //（可选项）数字类型；弹出框的高度；默认值：300
}
```

texts:

- 类型：JSON 对象类型
- 描述：（可选项）取消按钮的文本设置
- 内部字段：

```js
{
	 cancel: '取消'       //（可选项）字符串类型；取消按钮名称，若不传则不显示该文本
}
```

styles:

- 类型：JSON 对象类型
- 描述：对话框的样式设置
- 内部字段：

```js
{
	 bg:'#FFF',                                 //（可选项）字符串类型；对话框的背景色，支持#、rgb、rgba、img；默认：#FFF
	 image:{                                    // JSON 对象；显示图标的设置
		 path:'widget://image/image.png',       // 字符串类型；图片路径，支持 widget:// fs://
		 marginB:30                             //（可选项）数字类型；图片下边缘距离弹窗底部的距离；默认值：30
	 },
	 cancel:{                                   // JSON 对象；取消按钮配置，按钮位置在底部区域居中显示
		 icon:'widget://image/cancel_btn.png',  //（可选项）字符串类型；按钮图标路径，支持 widget:// fs:// ；不传则不显示该图标
		 w:50,                                  //（可选项）数字类型；按钮宽；默认值：50
		 h:50,                                  //（可选项）数字类型；按钮高；默认值：50
		 textSize: 12,                          //（可选项）数字类型；取消按钮文本字体大小；默认值：12
		 textColor: '#000'                      //（可选项）字符串类型；取消按钮的字体颜色，支持#、rgb、rgba；默认：#000   
	 }
}
```
##callback(ret)
ret:

- 类型：JSON对象
- 描述：返回参数
- 内部字段：

```js
{
	eventType : 'cancel'  // 字符串类型；回调事件类型
}
```

##示例代码
```js
var dialogBox = api.require('dialogBox');
dialogBox.discount({
	rect:{
		 w:200,
		 h:300  
	},
	styles:{
		bg:'#FFF',
		image:{
			path:'widget://image/image.png',
			marginB:30
		},
		cancel:{
			icon:'widget://image/cancel_btn.png',
			w:50,
			h:50  
		}
	}
}, function(ret){
    alert(JSON.stringify(ret));
    if (ret.eventType == 'cancel') {
	    dialogBox.close({
		    dialogName: 'discount'
	    });
    }
});
```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


<div id="m10"></div>
#**share**

弹出 share 样式的对话框

share({params})

##params

rect:

- 类型： JSON对象类型
- 描述：对话框的宽高设置
- 内部字段：

```js
{
	w: 300,         //（可选项）数字类型；对话框的宽；默认值：300
	h: 300          //（可选项）数字类型；对话框的高；默认值：300
}
```

items:

- 类型：JSON数组类型
- 描述：对话框数据
- 内部字段：

```js
[
	{
		text: '微信',                                 // 字符串类型；每一项的标题文字
		icon: 'widget://image/icon/weixin_icon.png'  // 字符串类型；每一项图片的路径 支持 fs:// widget://
	}
]
```

styles:

- 类型：JSON 对象类型
- 描述：对话框样式设置
- 内部字段：

```js
{
	 bg:'#FFF',              //（可选项）字符串类型；对话框的背景色，支持#、rgb、rgba、img；默认：#FFF
	 column: 3,              //（可选项）数字类型；支持的列数；默认值：3
	 horizontalSpace : 15,   //（可选项）数字类型；每一项的横向间隙，默认值：15
	 verticalSpace : 15,     //（可选项）数字类型；每一项的纵向间隙，默认值：15
	 itemText:{              //（可选项）JSON 对象；网格每一项文本设置
		 color: '#000',      //（可选项）字符串类型；每一项的文本字体颜色设置，支持#、rgb、rgba；默认：#000
		 size: 12,           //（可选项）字符串类型；每一项的文本字体大小设置；默认值：12
		 marginT: 8          //（可选项）数字类型；每一项的文本上边缘与图标的间距；默认值：8
	 },
	 itemIcon:{              //（可选项）JSON 对象；，每一项图片样式的设置
		 size: 80            //（可选项）数字类型；按钮图片的大小；默认值：80
	 }
}
```

##callback(ret)
ret:

- 类型：JSON对象
- 内部字段:

```js
{
	index: 0             // 数字类型；点击项的索引（由左至右，由上到下）
}
```

##示例代码
```js
var dialogBox = api.require('dialogBox');
dialogBox.share({
	rect:{
		w: 300,
		h: 300 
	},
	items:[
	{
		text: '微信',
		icon: 'widget://image/icon/weixin_icon.png'
	},
	{
		text: 'QQ',
		icon: 'widget://image/icon/qq_icon.png'
	},
	{
		text: 'QQZone',
		icon: 'widget://image/icon/QQZone.png'
	},
	{
		text: 'apiCloud',
		icon: 'widget://image/icon/apicloud.png'
	},
	{
		text: '微博',
		icon: 'widget://image/icon/weibo_icon.png'
	},
	{
		text: '短信',
		icon: 'widget://image/icon/shortmessage_icon.png'
	}
	],
	styles:{
		bg:'#FFF',
		column: 3,
		horizontalSpace : 15, 
		verticalSpace : 30,
		itemText: {
			color: '#000',
			size: 15,
			marginT: 10
		},
		itemIcon:{
			size:80
		}
    }
}, function(ret){
	alert(JSON.stringify(ret));
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m11"></div>
#**actionMenu**

弹出 actionMenu 样式的对话框

actionMenu({params})

##params

rect:

- 类型：JSON 对象
- 描述：对话框的宽高设置
- 内部字段：

```js
{
	h: 150         //（可选项）数字类型；对话框的高；默认值：150
}
```

texts:

- 类型：JSON 对象
- 描述：（可选项）取消按钮的文本设置
- 内部字段：

```js
{
	 cancel: '取消'  //（可选项）字符串类型；取消按钮名称，若不传则不显示该文本
}
```


items:

- 类型：JSON数组类型
- 描述：对话框内子按钮配置，多出屏幕的按钮可左右拖动查看，按钮和标题所占区域在弹框区域上下居中显示
- 内部字段：

```js
[
	{
		text: '微信',                                 // 字符串类型；每一项的标题文字
		icon: 'widget://image/icon/weixin_icon.png'  // 字符串类型；每一项图片的路径 支持 fs:// widget://
	}
]
```

styles:

- 类型：JSON 对象类型
- 描述：对话框样式设置
- 内部字段：

```js
{
	 bg:'#FFF',                 //（可选项）字符串类型；对话框的背景色，支持#、rgb、rgba、img；默认：#FFF
	 column: 3,                 //（可选项）数字类型；每屏显示的按钮个数；默认值：3
	 itemText:{                 //（可选项）JSON 对象；网格每一项文本设置
		 color: '#000',         //（可选项）字符串类型；每一项的文本字体颜色设置，支持#、rgb、rgba；默认：#000
		 size: 12,              //（可选项）字符串类型；每一项的文本字体大小设置；默认值：12
		 marginT: 8             //（可选项）数字类型；每一项的文本上边缘与图标的间距；默认值：8
	 },
	 itemIcon:{                 //（可选项）JSON 对象；每一项图片样式的配置
		 size: 30               //（可选项）数字类型；按钮图片的大小；默认值：30
	 },
	 cancel:{                   //（可选项）JSON 对象；底部按钮样式的配置
		 bg: 'fs://icon.png',   //（可选项）字符串类型：底部按钮的背景配置，支持rgb、rgba、#、img
		 color:'#000',          //（可选项）字符串类型；底部按钮标题字体颜色，支持rgb、rgba、#；默认：'#000'
		 h:44 ,                 //（可选项）数字类型；底部按钮高和宽；默认：44
		 size:  14              //（可选项）数字类型；按钮标题的字体大小；默认：14
	 }
}
```

##callback(ret)
ret:

- 类型：JSON对象
- 内部字段:

```js
{
	eventType: 'cancel',    // 字符串类型；交互事件类型，取值范围如下：
                            // cancel：点击取消按钮事件
                            // click：点击子按钮事件
	index: 0                // 数字类型；所点击的子按钮的索引（由左至右），仅当 eventType 为 click 时有值
}
```

##示例代码
```js
var dialogBox = api.require('dialogBox');
dialogBox.actionMenu ({
	rect:{
		h: 150
	},
	texts:{
		 cancel: '取消'
	},
	items:[
	{
		text: '微信',
		icon: 'widget://image/icon/weixin_icon.png'
	},
	{
		text: 'QQ',
		icon: 'widget://image/icon/qq_icon.png'
	},
	{
		text: '微博',
		icon: 'widget://image/icon/weibo_icon.png'
	},
	{
		text: '短信',
		icon: 'widget://image/icon/shortmessage_icon.png'
	}
	],
	styles:{
		bg:'#FFF',
		column: 3,
		itemText: {
			color: '#000',
			size: 12,
			marginT:8
		},
		itemIcon:{
			size:80
		},
		cancel:{  
			bg: 'fs://icon.png',   
			color:'#000',          
			h: 44 ,                 
			size: 14       
		}
	}
}, function(ret){
	alert(JSON.stringify(ret));
});
```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="m12"></div>
#**close**

关闭弹出的对话框

close ({params})

##params

dialogName:

- 类型：字符串类型
- 描述：上面所列各种对话框的样式名（接口）

##示例代码
```js
var dialogBox = api.require('dialogBox');
dialogBox.close ({
	dialogName: 'alert'
});
```
##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
