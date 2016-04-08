/*
Title: Git 代码托管指南
Description: Git 代码托管指南
*/

#概述

您可以使用自己的公有或私有Git平台进行APICloud APP的代码管理。一切的代码相关操作均可以在第三方Git平台上完成，这样，开发者可以在不使用APICloud的SVN进行代码管理，也无需将代码上传至APICloud平台的情况下，一样可以开发APICloud应用。

#准备工作

1. 在APICloud 官网控制台新建一个应用，如newDemoGit。或是已经创建过的应用也可以，在第二步中建立与应用同名的repositorie即可。
2. [在GitHub官网](https://github.com/)或其他git服务器创建一个repositorie，命名为newDemoGit。
3. 编写自己的项目代码，即widget包。请参考[Widget包结构说明](http://docs.apicloud.com/APICloud/%E6%8A%80%E6%9C%AF%E4%B8%93%E9%A2%98/widget-package-structure-manual#1)。
    config.xml 中的 

       ```
         <widget id="A6903088550387" version="0.0.1">
        ```

   <strong>id 值要和您在APICloud网站创建的应用id保持一致。</strong>

#Git Bash的使用

1， 百度搜索git，打开[git官网](https://git-scm.com/download/)下载Git，也可在百度软件中心下载。下载后安装。

2， 运行Git Bash, 出现命令行界面。

3， 创建本地仓库newDemoGit，并初始化。 
     
   依次执行以下命令：
 
	 $ cd e:/

     $ mkdir newDemoGit

     $ cd newDemoGit

     $ git init

4， 将准备好的widget项目包，复制到newDemoGit目录下。如下图：

   ![git目录](/img/git/git1.jpg)
 
   <strong>注意目录结构必须是：项目名-> widget; </strong>

5， 将本地仓库newDemoGit与GitHub上的远程库newDemoGit建立连接。
    
   执行命令： 
      
      $ git remote add origin https://github.com/FeCheng/newDemoGit.git

   <strong>注意把命令中的远程库地址换成自己的。</strong>

6，将本地代码推送到远程库。

   依次执行以下命令：

      $ git add .

      $ git commit -m "commit message"

      $ git push -u origin master  

   会提示输入GitHub用户名，密码。填写您的用户名，密码即可。


# 将GitHub 的项目地址与APICloud 的应用关联。

  1，在GitHub 官网复制您的项目地址。

  ![复制git地址](/img/git/git2.jpg)

  2，把复制的项目地址填入APICloud网站控制台-代码相应处。如图：

  ![粘贴git地址](/img/git/git3.jpg)

  3，输入您Git服务器的用户名、密码。若无用户名，密码，则可省略不填。

  4，然后就可以云编译或自定义loader了。编译前请将本地代码推送到远程库，否则会看不到您最近修改代码的效果。



