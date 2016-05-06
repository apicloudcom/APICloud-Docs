/*
Title: 云修复
Description: 云修复
*/

#概述

云修复可以实现快速版本迭代，快速修复bug。绕过苹果应用商店及安卓应用市场的版本审核。不用发布新的apk或者ipa版本既可对你的app进行更新，即增量更新。您改动了哪个或者哪几个html/css/js文件，那么只更新这几个文件即可。


##参考视频  

入门概念篇第七节（如何使用APICloud云端应用服务）：http://docs.apicloud.com/APICloud/videos-and-codes



#注意事项

1， config.xml配置smartUpdate为true：

    ```js
        
  		  <preference name="smartUpdate" value="true" /> 
 
    ```
2， app必须是编译的正式版。
 


#操作步骤

1， 准备更新的zip文件包。

   原项目文件结构如图：
 
   ![原项目文件结构](/img/smartUpdate/smartUpdate1.png)

  例如您需要更新 html 文件夹下的 main.html 文件。 那么您可以新建一个widget文件夹，
  把新的main.html 文件放入widget 下的 html 目录。更新包结构如图：

  ![更新包结构](/img/smartUpdate/smartUpdate2.png)

  然后选中widget根目录，右键，选择压缩为zip文件。

  ![更新包结构](/img/smartUpdate/smartUpdate3.jpg)

2， 在控制台->云修复->添加云修复页面上传widget.zip 文件

   首先点击导航进入云修复页面， 如图：

   ![导航图](/img/smartUpdate/smartUpdate4.jpg)

   然后点击“添加云修复”， 如图：

   ![添加云修复](/img/smartUpdate/smartUpdate5.png)

   <strong>注意，云修复是指定版本进行修复的。首先要选择要修复的版本。</strong>

   有两种修复方式可以选择，<strong>提示修复</strong> 和 <strong>静默修复</strong>。 提示修复会有弹出框，提示用户下载更新包、重启app。 静默修复不会有提示信息，下次重启，自动生效。
  
   选中“上传更新文件”， 点击“选择zip包”按钮上传制作好的widget.zip 更新包。 最后点击“更新”按钮即可。如下图：

   ![添加云修复](/img/smartUpdate/smartUpdate6.jpg)

   
   如果有自己的服务器，也可将制作好的widget.zip 更新包，上传到您自己的服务器。选中“输入更新地址”，然后将文件下载地址填入， 如图： 
	
   ![添加云修复](/img/smartUpdate/smartUpdate7.jpg)

   最后，点击“更新”按钮。


3， 使用提示修复时，在手机上打开app, 即可收到更新提示。 点击确定更新后，App自动重启，即可看到更新效果。

4， 对于静默修复，也可利用[smartupdatefinish](http://docs.apicloud.com/端API/api#c20)事件，和[rebootApp()](http://docs.apicloud.com/端API/api#92)方法，实现热更新效果，无需用户手动重启App。

	

   

   


  


   
