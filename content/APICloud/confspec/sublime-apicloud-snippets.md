/*
Title: Sublime APICloud 语法提示
Description: Sublime APICloud 语法提示
Sort: 8
*/

> 用户根据本文档可以学习自定义语法提示文件，存放在官方插件下面即可。

# 文件名
```
filename.sublime-snippet
```

注意事项：
1. 理论上文件名随意，但是尽量和文件内容的 `tabTrigger` 保持一致，做到见名知意
2. 文件格式必须是 `sublime-snippet`

可以新建自己的文件夹，把自己的提示文件都放在该文件夹下，文件名可以使用自己的前缀，以和官方片段区别开

# 文件结构
```xml
<snippet>
    <content><![CDATA[
// 其中存放需要显示的内容
]]></content>
    <tabTrigger>fs-read</tabTrigger>
    <scope>source.js</scope>
    <description>读取文件</description>
</snippet>
```

## 光标位置
```
${1:fd}
```
冒号后面的是该位置的默认输入

光标位置从1开始，每次加1

## 触发输入
```xml
<tabTrigger>fs-read</tabTrigger>
```

`tabTrigger` 标签中的内容就是触发该代码片段的指令，格式为： `模块名-方法名`

所以使用的时候只要记得当前模块名和方法名，即可补全对应的代码

![snippet tabTrigger](http://i.imgur.com/ikzj2Hp.png)

注意事项：
1. '$' 和 '.' 无法触发自动补全
2. 只能用 '-' 代替

## 适用范围
```
<scope></scope>
```

sublime支持几十种适用范围，但是在本插件中固定为 `source.js`



## 片段描述
```
<description></description>
```

在补全的时候会有弹出框，显示在右边的信息就是该代码片段的描述

![snippet description](http://i.imgur.com/tqZsyzN.png)

# 示例
以下演示如何编写一个 fs 模块的 rename 接口的步骤
## 1. 找到该接口的文档
[fs 模块 rename 接口](http://docs.apicloud.com/%E7%AB%AFAPI/%E5%8A%9F%E8%83%BD%E6%89%A9%E5%B1%95/fs#15)

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

## 3. 将示例代码放入语法提示模板的内容区
```xml
<snippet>
    <content><![CDATA[
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
]]></content>
    <tabTrigger></tabTrigger>
    <scope>source.js</scope>
    <description></description>
</snippet>
```

## 4. 替换需要输入的参数为光标提示
```xml
<snippet>
    <content><![CDATA[
fs.rename({
    oldPath: '${1:old_file_path}',
    newPath: '${2:new_file_path}'
},function(ret,err){
    var status = ret.status;
    if (status) {
        api.alert({msg:'重命名文件成功'});
    }else {
        api.alert({msg:err.msg});
    }
});
]]></content>
    <tabTrigger></tabTrigger>
    <scope>source.js</scope>
    <description></description>
</snippet>
```

## 5. 输入触发代码

在 `<tabTrigger></tabTrigger>` 中输入 `fs-rename`
```xml
<snippet>
    <content><![CDATA[
fs.rename({
    oldPath: '${1:old_file_path}',
    newPath: '${2:new_file_path}'
},function(ret,err){
    var status = ret.status;
    if (status) {
        api.alert({msg:'重命名文件成功'});
    }else {
        api.alert({msg:err.msg});
    }
});
]]></content>
    <tabTrigger>fs-rename</tabTrigger>
    <scope>source.js</scope>
    <description></description>
</snippet>
```

## 6. 输入描述信息

在 `<description></description>` 中输入 `重命名`
```xml
<snippet>
    <content><![CDATA[
fs.rename({
    oldPath: '${1:old_file_path}',
    newPath: '${2:new_file_path}'
},function(ret,err){
    var status = ret.status;
    if (status) {
        api.alert({msg:'重命名文件成功'});
    }else {
        api.alert({msg:err.msg});
    }
});
]]></content>
    <tabTrigger>fs-rename</tabTrigger>
    <scope>source.js</scope>
    <description>重命名</description>
</snippet>
```

## 7. 保存文件
保存文件名为 `fs-rename.sublime-snippet`
存放位置为 **Windows** `%AppData%\Roaming\Sublime Text 3\Packages` 文件夹下就行，最好是在其中新建自己的文件夹存放，便于管理。


