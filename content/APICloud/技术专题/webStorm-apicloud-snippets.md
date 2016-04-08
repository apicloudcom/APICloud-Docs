/*
Title: webStorm APICloud代码提示插件编写
Description: webStorm APICloud代码提示插件编写
Sort: 8
*/

> 用户根据本文档可以学习编写自定义语法提示文件

# 文件名
```
filename.jar
```

注意事项：
1. 理论上文件名随意，但是尽量和插件内容的保持一致，做到见名知意
2. 文件格式必须是 `jar`

可以新建自己的插件，把自己的提示文件都放在该插件下，插件名可以使用自己的前缀，以和官方片段区别开

# 文件结构

![图片说明](/img/docImage/webstorm_l5.png)

## 光标位置
```
$offset$
```
$符号中间是该位置的默认输入

## 触发输入

![图片说明](/img/docImage/webstorm_l1.png)

`Abbreviation` 输入框中的内容就是触发该代码片段的指令，格式为： `模块名.方法名`

所以使用的时候只要记得当前模块名和方法名，即可补全对应的代码

![snippet tabTrigger](/img/docImage/webstorm_l3.png)

## 片段描述

![图片说明](/img/docImage/webstorm_l2.png)

在补全的时候会有弹出框，显示在右边的信息就是该代码片段的描述

![图片说明](/img/docImage/webstorm_l4.png)


# 示例
以下演示如何编写一个 fs 模块的 rename 接口的步骤
## 1. 找到该接口的文档
[fs 模块 rename 接口](http://docs.apicloud.com/%E7%AB%AFAPI/%E5%8A%9F%E8%83%BD%E6%89%A9%E5%B1%95/fs#6)

## 2. 找到该接口的示例代码
```js
fs.rename({
    oldPath: 'fs://a.txt',
    newPath: 'fs://b.txt'
},function(ret,err){
    var status = ret.status;
    if (status) {
        api.alert({msg:'重命名文件成功'});
    }else {
        api.alert({msg:err.msg});
    }
});
```

## 3. 编写插件步骤分解

打开`File --> Settings`，`mac`是找到`Preference`。

![图片说明](/img/docImage/webstorm_l6.png)

点击进入`Settings`页面，选择`Editor --> Live Templates` 右侧出现的就是本地已安装的插件，新建插件组点击`'+'`，选择`Template Group....`点击，为新建的插件组命名。

![图片说明](/img/docImage/webstorm_l7.png)

![图片说明](/img/docImage/webstorm_l8.png)

选中新建的插件组`apicloud-module-fs`,点击`'+'`，选择`Live Template`编写新的插件。

![图片说明](/img/docImage/webstorm_l9.png)

依图填写相应内容：`Abbreviation`是插件提示关键字，`Description`是相应的描述，`Template text`是生成的代码片段，相对的变量用`$$`包括，`Edit variables`是插件代码中的变量映射关系，`Change`是选择代码提示的作用域，这里我们选择的是`JavaScript`，`Options`默认选项也要进行相应勾选。

![图片说明](/img/docImage/webstorm_l10.jpg)

![图片说明](/img/docImage/webstorm_l11.png)

如图`fs.rename`是有变量的，需点击`Edit variables`对变量进行配置，在这里我们选择的是`snakeCase()`函数，他的参数是字符串类型的，对应代码片段中的参数值。

![图片说明](/img/docImage/webstorm_l12.png)

![图片说明](/img/docImage/webstorm_l13.png)

注意：
* snakeCase(“argu”) 参数如果是驼峰写法 大写自动转成小写，并在前面加下划线。
* 参数不要出现特殊字符,(比如数字、标点和汉字的组合 )都会将两种类型字符用下划线（_）自动分割 。
* 颜色的16位值因为有特殊字符，建议就使用color来代替 snakeCase(“color”) 。
* 这个函数的参数值必须是字符串 ，如果是数字类型的，例子snakeCase(“123”) 。

## 4. 插件导出

打开`File --> Export Settings`，在弹出的对话框中选择`Live templates`即可。

![图片说明](/img/docImage/webstorm_l14.png)

![图片说明](/img/docImage/webstorm_l15.png)