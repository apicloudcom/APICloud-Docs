/*
Title: 统计云API
Description: 统计云API
Sort: 2
*/

[接口验证KEY生成规则说明](#1)

[应用统计信息获取接口](#2)

[应用各版本统计信息获取接口](#3)

[应用地理分布统计信息获取接口](#4)

[应用设备分布统计信息获取接口](#5)

[应用异常错误统计信息获取接口](#6)

[应用异常错误详细信息获取接口](#7)


#**接口验证KEY生成规则说明：**<div id="1"></div>

**生成规则**

当调用 APICloud 统计相关接口时，我们需要对头部信息中X-APICloud-AppKey 进行验证，X-APICloud-AppKey 的生成规则如下：

```js
your app key = SHA1(你的应用ID + 'UZ' + 你的应用KEY + 'UZ' + 当间时间毫秒数).当间时间毫秒数
```

例如：你的应用ID是A6968565094002，而你的应用KEY是62FB16B2-0ED6-B460-1F60-EB61954C823B，则你在请求头部信息X-APICloud-AppKey中设置的值应为
'A6968565094002'+'UZ'+'62FB16B2-0ED6-B460-1F60-EB61954C823B'+'UZ'+当前时间戳组合字符串后通过SHA1加密后返回字符串再加上’.当前时间毫秒数’。

示例代码如下：

```js
var now = Date.now();

varappKey = sha1("A6968565094002"+"UZ"+ "62FB16B2-0ED6-B460-1F60-EB61954C823B"+"UZ"+now)+"."+now;
```

#**接口名称：应用统计信息获取接口**<div id="2"></div>

**接口说明**

该接口主要用于获取用户指定应用ID及时间范围内的相关应用统计数据信息。

**调用地址**

https://r.apicloud.com/analytics/

**调用方法**

getAppStatisticDataById

**请求方式**

POST

**请求头部设置说明**

	相关接口调用需要在发送的请求头部设置相关应用ID及应用KEY。相关请求头部设置定义如下：
	X-APICloud-AppId : {your app id}
	X-APICloud-AppKey : {you app key}

**接口接收参数**

	startDate – 开始时间 格式：YYYY-MM-DD 例如：2014-10-10
	endDate – 结束时间 格式：YYYY-MM-DD

**接口返回数据**

	调用成功则返回相关应用统计数据信息，失败则返回错误信息，相关数据信息均以JSON数据格式返回。
	接口返回状态（st） ： 1－成功 0－失败
	接口返回信息（msg）：－成功为相关应用统计数据信息，失败则为错误信息。

**返回数据示例**

![图片说明](/img/docImage/202.jpg)

**返回字段说明**

<table>
    <tr>
        <th>字段名称</th>
        <th>字段说明</th>
    </tr>
    <tr>
        <td>id</td>
        <td>数据ID</td>
    </tr>
    <tr>
        <td>appid</td>
        <td>应用ID</td>
    </tr>
    <tr>
        <td>devicesCount</td>
        <td>设备总数</td>
    </tr>
    <tr>
        <td>newRegsCount</td>
        <td>当天新注册用户数</td>
    <tr>
        <td>newUpdateCount</td>
        <td>当天新升级用户数</td>
    <tr>
        <td>activeCountInToday</td>
        <td>当天活跃用户数</td>
    <tr>
        <td>activeCountInSevenDays</td>
        <td>七日内活跃用户数</td>
    <tr>
        <td>activeCountInThirtyDays</td>
        <td>三十日内活跃用户数</td>
    <tr>
        <td>totalUseTime</td>
        <td>应用累计使用时长</td>
    <tr>
        <td>totalOperationCount</td>
        <td>应用累计使用次数</td>
    <tr>
        <td>totalUseTimeInSevenDays</td>
        <td>七日内累计使用时长</td>
    <tr>
        <td>totalUseTimeInThirtyDays</td>
        <td>三十日内累计使用时长</td>
    <tr>
        <td>totalOperationCountInSevenDays</td>
        <td>七日内累计使用次数</td>
    <tr>
        <td>totalOperationCountInThirtyDays</td>
        <td>三十日内累计使用次数</td>
    <tr>
        <td>reportDate</td>
        <td>统计数据生成时间</td>
</table>



#**接口名称：应用各版本统计信息获取接口**<div id="3"></div>

**接口说明**

该接口主要用于获取用户指定应用ID及时间范围内相关应用各版本的统计数据信息。

**调用地址**

https://r.apicloud.com/analytics/

**调用方法**

getVersionsStatisticDataById

**请求方式**

POST

**请求头部设置说明**

	相关接口调用需要在发送的请求头部设置相关应用ID及应用KEY。相关请求头部设置定义如下：
	X-APICloud-AppId : {your app id}
	X-APICloud-AppKey : {you app key}

**接口接收参数**

	startDate – 开始时间 格式：YYYY-MM-DD 例如：2014-10-10
	endDate – 结束时间 格式：YYYY-MM-DD

**接口返回数据**

	调用成功则返回相关应用各版本统计数据信息，失败则返回错误信息，相关数据信息均以JSON数据格式返回。
	接口返回状态（st） ： 1－成功 0－失败
	接口返回信息（msg）：－成功为相关应用各版本统计数据信息，失败则为错误信息。

**返回数据示例**
 
![图片说明](/img/docImage/203.jpg)

**返回字段说明**

<table>
    <tr>
        <th>字段名称</th>
        <th>字段说明</th>
    </tr>
    <tr>
        <td>id</td>
        <td>数据ID</td>
    </tr>
    <tr>
        <td>appid</td>
        <td>应用ID</td>
    </tr>
    <tr>
        <td>versionCode</td>
        <td>应用版本号</td>
    </tr>
    <tr>
        <td>devicesCount</td>
        <td>该版本下设备总数</td>
    <tr>
        <td>newRegsCount</td>
        <td>该版本下当天新注册用户数</td>
    <tr>
        <td>newUpdateCount</td>
        <td>该版本下当天新升级用户数</td>
    <tr>
        <td>activeCountInToday</td>
        <td>该版本下当天活跃用户数</td>
    <tr>
        <td>totalUseTime</td>
        <td>该版本下应用累计使用时长</td>
    <tr>
        <td>totalOperationCount</td>
        <td>该版本下应用累计使用次数</td>
    <tr>
        <td>reportDate</td>
        <td>统计数据生成时间</td>
</table>



#**接口名称：应用地理分布统计信息获取接口**<div id="4"></div>

**接口说明**

该接口主要用于获取用户指定应用ID及时间范围内的应用下各版本地理分布统计数据信息。

**调用地址**

https://r.apicloud.com/analytics/

**调用方法**

getGeoStatisticDataById

**请求方式**

POST

**请求头部设置说明**

	相关接口调用需要在发送的请求头部设置相关应用ID及应用KEY。相关请求头部设置定义如下：
	X-APICloud-AppId : {your app id}
	X-APICloud-AppKey : {you app key}

**接口接收参数**

	startDate – 开始时间 格式：YYYY-MM-DD 例如：2014-10-10
	endDate – 结束时间 格式：YYYY-MM-DD
	versionCode – 版本

**接口返回数据**

	调用成功则返回相关应用各版本地理分布统计数据信息，失败则返回错误信息，相关数据信息均以JSON数据格式返回。
	接口返回状态（st） ： 1－成功 0－失败
	接口返回信息（msg）：－成功为相关应用地理分布统计数据信息，失败则为错误信息。

**返回数据示例**

![图片说明](/img/docImage/204.png)
 

**返回字段说明**

<table>
    <tr>
        <th>字段名称</th>
        <th>字段说明</th>
    </tr>
    <tr>
        <td>id</td>
        <td>数据ID</td>
    </tr>
    <tr>
        <td>appid</td>
        <td>应用ID</td>
    </tr>
    <tr>
        <td>versionCode</td>
        <td>版本号</td>
    </tr>
    <tr>
        <td>geoNewRegsResult</td>
        <td>该版本下新增用户地理分布JSON数据集合</td>
    <tr>
        <td>geoDevicesCountResult</td>
        <td>该版本下全部用户地理分布JSON数据集合</td>
    <tr>
        <td>geoStartupCountResult</td>
        <td>该版本下全部启动次数地理分布JSON数据集合</td>
    <tr>
        <td>geoActiveCountResult</td>
        <td>该版本下全部活跃用户地理分布JSON数据集合</td>
    <tr>
        <td>reportDate</td>
        <td>统计数据生成时间</td>
</table>


**特别说明**

geoNewRegsResult、geoDevicesCountResult、geoStartupCountResult、geoActiveCountResult相关数据均为JSON格式数据集合，单个数据对象由city及count属性构成，其中city为城市名城而count 则为对应省份（或城市）相关统计数据信息。



#**接口名称：应用设备分布统计信息获取接口**<div id="5"></div>

**接口说明**

该接口主要用于获取用户指定应用ID及时间范围内的应用下各版本设备信息分布统计数据信息。


**调用地址**

https://r.apicloud.com/analytics/

**调用方法**

getDeviceStatisticDataById

**请求方式**

POST

**请求头部设置说明**

	相关接口调用需要在发送的请求头部设置相关应用ID及应用KEY。相关请求头部设置定义如下：
	X-APICloud-AppId : {your app id}
	X-APICloud-AppKey : {you app key}

**接口接收参数**

	startDate – 开始时间 格式：YYYY-MM-DD 例如：2014-10-10
	endDate – 结束时间 格式：YYYY-MM-DD

**接口返回数据**

	调用成功则返回相关应用各版本设备分布统计数据信息，失败则返回错误信息，相关数据信息均以JSON数据格式返回。
	接口返回状态（st） ： 1－成功 0－失败
	接口返回信息（msg）：－成功为相关应用各版本设备分布统计数据信息，失败则为错误信息。

**返回数据示例**
 
![图片说明](/img/docImage/205.png)

**返回字段说明**

<table>
    <tr>
        <th>字段名称</th>
        <th>字段说明</th>
    </tr>
    <tr>
        <td>id</td>
        <td>数据ID</td>
    </tr>
    <tr>
        <td>appid</td>
        <td>应用ID</td>
    </tr>
    <tr>
        <td>versionCode</td>
        <td>版本号</td>
    </tr>
    <tr>
        <td>modelNewRegsResult</td>
        <td>当前版本下按型号区分新增用户数（JSON数据集合）</td>
    <tr>
        <td>resolutionNewRegsResult</td>
        <td>当前版本下按分辨率区分新增用户数（JSON数据集合）</td>
    <tr>
        <td>osNewRegsResult</td>
        <td>当前版本下按手机操作系统区分新增用户数（JSON数据集合）</td>
    <tr>
        <td>connTypeResult</td>
        <td>当前版本下按手机联网方式区分连接次数数据（JSON数据集合）</td>
    <tr>
        <td>modelNewActiveResult</td>
        <td>当前版本下按型号区分活跃用户数（JSON数据集合）</td>
    <tr>
        <td>resolutionNewActiveResult</td>
        <td>当前版本下按分辨率区分活跃用户数（JSON数据集合）</td>
    </tr>
    <tr>
        <td>osNewActiveResult</td>
        <td>当前版本下按手机操作系统区分活跃用户数（JSON数据集合）</td>
    <tr>
        <td>modelTotalResult</td>
        <td>当前版本下按型号区分用户总数（JSON数据集合）</td>
    <tr>
        <td>resolutionTotalResult</td>
        <td>当前版本下按分辨率区分用户总数（JSON数据集合）</td>
    <tr>
        <td>osTotalResult</td>
        <td>当前版本下按手机操作系统区分用户总数（JSON数据集合）</td>
    <tr>
        <td>connTypeTotalResult</td>
        <td>当前版本下按手机联网方式区分连接总次数数据（JSON数据集合）</td>
    <tr>
        <td>reportDate</td>
        <td>统计数据生成时间</td>
</table>


**特别说明**
modelNewRegsResult、resolutionNewRegsResult、osNewRegsResult、connTypeResult、modelNewActiveResult、resolutionNewActiveResult、osNewActiveResult、modelTotalResult、resolutionTotalResult、osTotalResult、connTypeTotalResult相关数据均为JSON格式数据集合，相关集合集合内各数据对象定义详见下表：

<table>
    <tr>
        <th>数据集合名称</th>
        <th>数据对象属性</th>
        <th>属性说明</th>
    </tr>
    <tr>
        <td>modelNewRegsResult、modelNewActiveResult、modelTotalResult</td>
        <td>model、count</td>
        <td>model – 手机型号、count – 统计数据</td>
    </tr>
    <tr>
        <td>resolutionNewRegsResult、resolutionNewActiveResult、resolutionTotalResult</td>
        <td>resolution、count</td>
        <td>resolution – 分辨率、count – 统计数据</td>
    </tr>
    <tr>
        <td>osNewRegsResult、osNewActiveResult、osTotalResult</td>
        <td>os、count</td>
        <td>os – 手机操作系统、count – 统计数据</td>
    </tr>
    <tr>
        <td>connTypeResult、connTypeTotalResult</td>
        <td>connType、count</td>
        <td>connType – 联网方式 、count – 统计数据</td>
</table>


#**接口名称：应用异常错误统计信息获取接口**<div id="6"></div>

**接口说明**

该接口主要用于获取用户指定应用ID及时间范围内的应用下各版本异常错误统计数据信息。

**调用地址**

https://r.apicloud.com/analytics/

**调用方法**

getExceptionsStatisticDataById

**请求方式**

POST

**请求头部设置说明**

	相关接口调用需要在发送的请求头部设置相关应用ID及应用KEY。相关请求头部设置定义如下：
	X-APICloud-AppId : {your app id}
	X-APICloud-AppKey : {you app key}

**接口接收参数**

	startDate – 开始时间 格式：YYYY-MM-DD 例如：2014-10-10
	endDate – 结束时间 格式：YYYY-MM-DD

**接口返回数据**

	调用成功则返回相关应用各版本异常统计数据信息，失败则返回错误信息，相关数据信息均以JSON数据格式返回。
	接口返回状态（st） ： 1－成功 0－失败
	接口返回信息（msg）：－成功为相关应用各版本异常统计数据信息，失败则为错误信息。

**返回数据示例**
 
![图片说明](/img/docImage/206.png)

**返回字段说明**

<table>
    <tr>
        <th>字段名称</th>
        <th>字段说明</th>
    </tr>
    <tr>
        <td>id</td>
        <td>数据ID</td>
    </tr>
    <tr>
        <td>appid</td>
        <td>应用ID</td>
    </tr>
    <tr>
        <td>versionCode</td>
        <td>版本号</td>
    </tr>
    <tr>
        <td>model</td>
        <td>异常信息涉及机型</td>
    <tr>
        <td>systemVersion</td>
        <td>异常信息系统版本</td>
    <tr>
        <td>excepTitle</td>
        <td>异常摘要</td>
    <tr>
        <td>excepCount</td>
        <td>异常发生数量</td>
    <tr>
        <td>reportDate</td>
        <td>统计数据生成时间</td>
</table>



#**接口名称：应用异常错误详细信息获取接口**<div id="7"></div>

**接口说明**

该接口主要用于根据应用异常错误摘要获取异常错误详细信息。

**调用地址**

https://r.apicloud.com/analytics/

**调用方法**

getExceptionsDetailByTitle

**请求方式**

POST

**请求头部设置说明**

	相关接口调用需要在发送的请求头部设置相关应用ID及应用KEY。相关请求头部设置定义如下：
	X-APICloud-AppId : {your app id}
	X-APICloud-AppKey : {you app key}

**接口接收参数**

	title – 错误摘要信息

**接口返回数据**

	调用成功则返回指定异常错误摘要的详细信息，失败则返回错误信息，相关数据信息均以JSON数据格式返回。
	接口返回状态（st） ： 1－成功 0－失败
	接口返回信息（msg）：－成功为指定异常错误摘要的详细信息，失败则为错误信息。

**返回数据示例**

![图片说明](/img/docImage/207.png)

**返回字段说明**

<table>
    <tr>
        <th>字段名称</th>
        <th>字段说明</th>
    </tr>
    <tr>
        <td>content</td>
        <td>异常错误具体信息</td>
</table>
