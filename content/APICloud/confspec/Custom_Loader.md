/*
Title: 自定义loader说明
Description: 自定义loader说明
Sort: 8
*/


#**一、应用自定义loader的作用**

一直以来，官方发布的AppLoader，只包含了官方模块。而其他开发者的自定义模块、付费模块、第三方SDK模块等都并未加入到loader中，这给开发者在开发调试过程中带来一些不便。其中原因很多，如：模块全编译进来Loader的Size会太大、多个同类的第三方模块一起编译会存在冲突等。针对此类问题，APICloud也一直在想办法解决，今天我们为开发者推出了为应用自定义Loader的功能。今后，开发者可以为自己的应用自定义AppLoader，通过自定义Loader，开发者可以自由选择本APP所需要的模块进行loader的编译。同时，自定义loader将与当前APP所有的配置最大限度的保持一致，保持开发调试的APP环境与正式上线的环境一致，保证如微信、微博、百度地图等第三方SDK模块，在loader中调试通过后，编译正式版本也不会出现问题。


#**二、自定义loader执行原理**

1、  每个APP项目对应一个自定义loader，开发过程中需要为每个APP项目单独编译自定义loader；如果APP项目对应的自定义loader不存在，则默认使用官方loader

2、  自定义loader完全使用当前APP的所有配置，包括APP名字、ICON图标、启动界面、包名、证书、开放平台SDK模块的各种KEY等

3、  自定义loader在运行之初，会根据所选择要“真机同步”APP项目的ID从设备的SD卡（Android平台）或者Document下（IOS平台）的固定目录中找到对应ID的项目的代码，并加载运行

4、  官方loader的更新，不影响自定义loader，二者相互独立，可同时存在于设备上


#**三、自定义loader与官方loader的区别**

1、  官方loader会随APICloud每周的版本发布而更新，自定义loader不会，自定义loader由开发者主动编译后更新

2、  官方loader中的微信、微博等第三方开放SDK模块的KEY等，是跟官方loader包名对应，属于官方loader的；而自定义loader的，则属于你当前APP的，等同于你的APP正式版

3、  官方loader可同时展示多个APP项目，并从中选择某APP项目运行；自定义loader只加载当前APP项目

4、  自定义loader可随自己的需求随时编译；官方loader需APICloud每周发版本

5、  官方loader只有一个；而每个APP项目对应一个自定义loader，如果你有10个APP项目，将对应10个自定义loader

6、  官方loader使用官方固定的包名、证书、ICON等；自定义loader使用当前APP项目的包名、证书、ICON、启动界面、APP名字等

7、	 【重要】IOS平台的自定义loader，所有app项目的自定义loader统一包名为“com.apicloud.customloader”，并且名称统一为“自定义Loader”，多个项目自定义loader进行真机同步时，将是覆盖安装的。如果您的某个APP项目已经上传了自己的IOS证书，则IOS自定义loader对应的包名将是你的证书对应的包名，自定义loader同步到IOS设备上时，均可在桌面看到。


#**四、自定义loader使用流程**

1、  在APICloud Studio中选中某APP项目，并且在该项目上右键鼠标

2、  在弹出的右键菜单中，选择“编译自定义loader”

3、  之后APICloud Studio会弹出编译等待框，稍等一段时间后，提示编译成功

4、  编译成功后，在该APP项目上“真机同步”时，APICloud Studio会默认选择自定义loader进行同步

5、  自定义loader的更新时机，请参考第五点：何时编译新的自定义loader


#**五、何时编译新的自定义loader**

1、  更换了APP的Android或者IOS证书时，需要重新编译自定义loader，同时如果项目中使用了微信、微博、百度地图等KEY值跟APP证书挂钩的第三方SDK模块，需要重新去这些开放平台申请新的KEY

2、  更换了APP的包名时，需要重新编译自定义loader，同时如果项目中使用了微信、微博、百度地图等KEY值跟APP包名挂钩的第三方SDK模块，需要重新去这些开放平台申请新的KEY

3、  勾选了新的模块或者config文件的feature、meta-data字段有更新时，需要重新编译loader，编译之前，需要将该项目的config文件同步至云端，云端编译自定义loader时将使用最新的config配置

4、  你的APP项目用到的模块中，某个或多个模块有更新时，需要重新编译自定义loader

5、	 官方每周发布新的版本时，如果有涉及到解决了与您项目有关的BUG或者做了新的适配工作时，需要重新编译自定义Loader



#**六、自定义loader使用注意事项**

1、  自定义loader有效期为30天，30天过后需要重新编译

2、  自定义loader不可用于商业用途

3、  切勿随意改动APP项目config文件中的ID值，否则会引起无法编译自定义loader，或者“真机同步时”因ID错误找不到widget而导致加载失败

4、  开发调试过程中，尽量将你的APP项目config中的<preference name="debug" value="true"/>字段置为true，当JS报错时，将会弹出提示到屏幕；发布正式上线版本时可关闭debug

5、  新建完APP项目后，最好登录网站，为该APP项目创建Android或者IOS证书，以保证证书是对应你的项目的。因为如果没有为该APP项目创建证书的情况下，使用的是官方的默认证书，那么自定义loader也将使用该证书，如果项目中用到了微信等与证书相关的模块，将带来调试的麻烦

6、  自定义loader只从设备SD卡或者document下加载APP项目，如果该项目被删除或者目录被篡改，将报找不到项目代码的错误

7、  使用IOS自定义loader时，如果已经上传了自己的IOS证书，并且是个人版证书（企业版证书则不受影响），那么，真机同步时，只能在越狱的手机上同步，或者需要在苹果的网站上将非越狱手机加成开发机，否则真机同步时将报类似“打开写文件服务失败”的错误而同步失败


#**七、自定义Loader对快速生成测试包是否有影响？**

自定义Loader与快速生成测试包没有任何关系。 APICloud Studio“快速生成测试包”时，仍然使用的是官方的loader，而不是自定义loader。因为，快速生成测试包的apk或者ipa安装包，其包名及签名证书等，使用的是APICloud的默认配置，将与你的APP配置的不一致，包括模块可能也并未包含，可能引起在自定义loader中调试通过的某些功能失效，如微信微博分享，百度地图等。使用时请格外注意！ “快速生成测试包”生成的apk或者ipa包仅仅用于简单的安装包输出，无法用于商业用途！

感谢大家对APICloud一直以来的关注和支持，我们会不断地优化产品，为开发这提供更好的服务。