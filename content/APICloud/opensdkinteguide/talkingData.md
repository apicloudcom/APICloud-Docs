/*
Title: talkingData平台接入
Description: talkingData平台接入
Sort: 11
*/
TalkingData是一套针对移动应用的数据统计分析平台，旨在满足移动应用数据统计、渠道评估等日常运营数据需求。我们致力于帮助移动开发者收集、处理、分析第一方数据，透析全面运营指标，掌握用户行为，改善产品。
<div id="method"></div>

#步骤

<div class="outline">
    <a href="#addSDK">如何集成</a>
    <a href="#howtoStart">初始化配置</a>
    <a href="#howtoData">如何查看数据</a>
    <a href="#oDatacontent">数据概览</a>
</div>

<div id="addSDK"></div>

##如何集成

经过TalkingData和Apicloud的共同努力，Apicloud的开发者只需在添加模块时添加第三方开放平台-TalkingData模块，并顺利完成云编译，则自动完成TalkingData App Analytics的基础集成。

![添加模块](/img/docImage/talkingData1.jpg)

<div id="howtoStart"></div>

##初始化配置

默认时，我们将关闭log，自动捕获app异常，且所有渠道ID均为默认值。

关闭log时您将无法通过log方式验证统计是否准确。

自动捕获app异常时，我们会在错误报告模块为您提供错误采集分析。

渠道ID均为默认值时，您将无法从我们的报表中 “渠道统计”模块看到具体渠道的数据。如果您需要分不同渠道进行统计，则需要您针对每个渠道单独修改渠道ID，且分别云编译。

如果您需要修改以上设置，使用此模块之前需先配置config文件的Feature，具体说明详见：TalkingData SDK接口文档。

<div id="howtoData"></div>

##如何查看数据

完成TalkingData SDK集成并成功云编译后，您在ApiCloud平台按以下步骤查看数据：

1）	点击添加了TalkingData SDK的app；

2）	从以下两个位置点击“云编译”：

![查看数据步骤1](/img/docImage/talkingData2.png) 

3）  进入到“云编译”模块后，在云编译按钮下的“第三方服务”或者编译记录后的“第三方服务”会引导您跳转到TalkingData查看该App的数据：

![查看数据步骤1](/img/docImage/talkingData3.png)

A）如果您点击云编译按钮下的第三方服务部分出现的Talkingdata按钮，直接跳转到TalkingData查看该App的数据，见上图；

B）如果您通过“编译记录”，在对应的记录后点击的“第三方服务”，则从弹窗中看到TalkingData图标，点击“查看详情”，则跳转到TalkingData查看该App的数据，见下图。

![查看数据步骤1](/img/docImage/talkingData4.png)

<div id="oDatacontent"></div>

##数据概览  

通过我们的平台，您可以看到关于您app的以下数据：

![查看数据步骤1](/img/docImage/talkingData5.png)

如果您仅仅完成基础集成，将无法看到“页面访问”、“事件和管理”的统计数据。

如果您需要这两部分的统计分析，可以调用页面统计、自定义事件统计等方法，获取以上数据，了解更为详细的用户行为。具体方法的说明详见：TalkingData SDK接口文档。

关于指标的详细说明，请参考TalkingData官网文档中**数据分析**部分：
https://www.talkingdata.com/app/document_web/index.jsp?statistics
