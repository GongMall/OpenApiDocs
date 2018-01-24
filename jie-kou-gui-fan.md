** 接口规范：**
支持http协议通讯，全部使用post方式，utf-8编码，请求参数为queryString方式，返回值为json格式


**接口网关：**
正式环境：`http://openapi.gongmall.com `
测试环境：`http://openapi-qa.gongmall.com `
**请求方式：**
- POST

**调用规则：**
- 请求过期时间：5分钟
- 调用周期：60秒
- 一个调用周期内，最大可调用次数：200

**共通的输入输出参数定义：**

输入参数

|参数名|必选|类型|描述|长度范围|
|:---- |:---|:----- |:----- |----- |
|appKey |是 |string |开发者唯一标识 ||
|nonce |是 |string | 随机数，请每次随机产生，保证随机数不可预测 |不大于32位|
|timestamp |是 |string | 当前毫秒时间戳| |
|sign |是 |string | 签名 |见备注|

{% method %}
## My first method

签名生成的通用步骤如下：
第一步，设所有发送或者接收到的数据为集合M，将集合M内非空参数值的参数按照参数名ASCII码从小到大排序（字典序），使用URL键值对的格式（即key1=value1&key2=value2…）拼接成字符串stringA。
第二步，在stringA最后拼接上appSecret得到stringSignTemp字符串，并对stringSignTemp进行MD5运算，再将得到的字符串所有字符转换为大写，得到sign值signValue。

假设传递的参数如下：
appKey: gmd930ea5d5a258f4f
nonce: 76e71d31590d44f2aaa55fed6b3e267c
timestamp: 1490063145767
processNum: wi123456789

第一步：对参数按照key=value的格式，并按照参数名ASCII字典序排序如下：
stringA="appKey=gmd930ea5d5a258f4f&nonce=76e71d31590d44f2aaa55fed6b3e267c&processNum=wi123456789&timestamp=1490059287869";

第二步：拼接API密钥：
stringSignTemp="stringA&appSecret=192006250b4c09247ec02edce69f6a2d"
sign=MD5(stringSignTemp).toUpperCase()="93E1D6AF003B1061DF01CEB93523F142"


输出参数:

|参数名|类型|描述|
|:---- |:---|:----- |----- |
|success |boolean |业务请求是否成功(true:成功,false:失败) |
|errorCode |string |返回错误码(success为true时为空) |
|errorMsg |string | 返回错误消息(success为true时为空) |
|data |Object | 返回数据(success为false时为空) |

{% sample lang="js" %}
Here is how to print a message to `stdout` using JavaScript.

```js
console.log('My first method');
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
