/*
Title: key.xml文件配置说明
Description: key.xml文件配置说明
Sort: 11
*/

```js
<?xml version="1.0" encoding="UTF-8"?>
<security>
<item name="key0" value="value0"/>
<item name="key1" value="value1"/>
<item name="key2" value="value2"/>
<item name="key3" value="value3"/>
</security>
```

如上，您可以在res/key.xml中配置多个键值对，然后编译时，云服务器会自动加密 key.xml文件。
在应用内，您可以通过api.loadSecureValue方法，获取指定的 key 对应的值。
对于模块开发者，也可以在模块内通过iOS/Andorid相应方法获取。
