# Defining Methods

Methods allow you to smoothly display code examples in different languages.

{% method %}
## My first method

My first method exposes how to print a message in JavaScript and Go.

{% sample lang="js" %}
Here is how to print a message to `stdout` using JavaScript.

```js
public class SignUtil {
public static final String APPKEY = "appKey";
public static final String APPSECRET = "appSecret";
public static final String NONCE = "nonce";
public static final String TIMESTAMP = "timestamp";
public static final String SIGN = "sign";
/**
* 获取签名
* @param paramMap 包含业务参数，和appKey,nonce,timestamp这3个公共参数
* @param appSecret
* @return
*/
public static String getSign(Map<String, Object> paramMap, String appSecret) {
String text = getUrlText(paramMap);
text += "&appSecret=" + appSecret;
return MD5SHA256Util.md5(text).toUpperCase();
}
private static String getUrlText(Map<String, Object> beanMap) {
beanMap = getSortedMap(beanMap);
StringBuilder builder = new StringBuilder();
for (String key : beanMap.keySet()) {
String value = beanMap.get(key).toString();
builder.append(key);
builder.append('=');
builder.append(value);
builder.append('&');
}
String text = builder.toString();
return text.substring(0, text.length() - 1);
}
/**
* 对普通map进行排序
* @param paramMap
* @return
*/
private static Map<String, Object> getSortedMap(Map<String, Object> paramMap) {
SortedMap<String, Object> map = new TreeMap<String, Object>();
for (String key : paramMap.keySet()) {
if (key != null && !APPSECRET.equals(key)) {
Object value = paramMap.get(key);
if (value != null) {
String valueStr = String.valueOf(value);
if (valueStr != null && !"".equals(valueStr)) {
map.put(key, value);
}
}
}
}
return map;
}
}
```

{% sample lang="go" %}
Here is how to print a message to `stdout` using Go.

```go
fmt.Println("My first method")
```

{% common %}
Whatever language you are using, the result will be the same.

```bash
$ My first method
```
{% endmethod %}
