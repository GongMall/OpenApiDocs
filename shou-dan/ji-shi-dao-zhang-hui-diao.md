### 即时到账回调

---

**简要描述：**

* 交易成功或者交易关闭之后，工猫平台异步通知商户平台处理结果，需要商户平台提供该接口

**请求URL：**

* `开发者信息提供的即时到账回调地址`

**请求方式：**

* POST

**参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | :--- |
| out\_trade\_no | 是 | string | 商户订单号 |
| inner\_trade\_no | 是 | string | 平台订单号 |
| trade\_status | 是 | string | 交易状态，TRADE\_SUCCESS 交易支付成功，TRANSFER\_FAIL 交易失败，TRADE\_CLOSED 交易关闭 |
| trade\_amount | 是 | string | 交易金额 |
| gmt\_payment | 否 | string | 交易支付时间 |
| gmt\_close | 否 | string | 交易关闭时间 |
| failReason | 否 | string | 交易失败原因 |

**返回参数说明**

| 参数名 | 类型 | 说明 |
| :--- | :--- | :--- |
| status | int | 1处理成功，2处理失败 |

**返回示例**

{

“status” ：1

}

**备注**

* 更多返回错误代码请看首页的异常码描述



