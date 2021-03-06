### 交易退款回调

---

**简要描述：**

* 交易退款之后，工猫平台异步通知商户平台处理结果，需要商户平台提供该接口

**请求URL：**

* `开发者信息提供的交易退款回调地址`

**请求方式：**

* POST

**参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | :--- |
| orig\_outer\_trade\_no | 是 | string | 原商户订单号，需要针对该笔订单发起退款 |
| out\_trade\_no | 是 | string | 商户退款订单号 |
| inner\_trade\_no | 是 | string | 平台订单号 |
| refund\_status | 是 | string | 退款状态，REFUND\_SUCCESS 退款成功，REFUND\_FAIL退款失败 |
|  |  |  |  |
| refund\_amount | 是 | string | 退款金额 |
| gmt\_refund | 否 | string | 退款时间，只有交易成功该字段才有值 |

**返回参数说明**

| 参数名 | 类型 | 说明 |
| :--- | :--- | :--- |
| status | int | 0处理失败，1处理成功 |

**返回示例**

{

“status” ：1

}

**备注**

* 更多返回错误代码请看首页的异常码描述



