* ### 交易退款

---

**简要描述：**

* B端商户平台发起交易退款请求

**请求URL：**

* /api/instant/refund

**请求方式：**

* POST 

**参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| bizContent | 是 | json格式 | 退款订单信息 |

**业务参数bizContent格式：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| requestId | 是 | string | 客户请求标识,最长32位\(用户提现时企业系统自动生成，每个requestId代表一个提现请求，工猫作为每笔提现记录的唯一标识\) |
| outTradeNo | 是 | string | 商户退款订单号 |
| origOutTradeNo | 是 | string | 原始订单号，针对该订单发起退款 |
| refundAmount | 是 | string | 退款金额，15位以内最大保留 2 位精度数字，支持部分退款，退款金额不能大于交易金额。如：50.00 |
| currency | 否 | string | 币种，默认人民币 CNY |
| royaltyInfo | 否 | json（列表） | 分润账号集，最多支持 10 个分润账号 |

royaltyInfo分润账号信息参数

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| payeeMemberId | 是 | string | 分账会员ID |
| amount | 是 | string | 分账金额 ，取值范围为\[0.01 ，100000000000.00\]，精确到小数点后两位。 |

**请求参数bizContent的格式示例**

```
{
   "requestId": "Req201910250001",
   "outTradeNo": "Out201910250001",
   "origOutTradeNo": "Ori201910250001",
   "refundAmount": "45.67",
   "currency": "CNY",
   "royaltyInfo": [{
    "amount": "12.34",
    "payeeMemberId": "123456"
   }]
}
```

**返回参数说明**

| 参数名 | 类型 | 说明 |
| :--- | :--- | --- |
| requestId | string | 客户请求标识 |
| outTradeNo | string | 扫码的url地址 |
| tradeNo | string | 平台订单号 |
| status | string | 处理状态，S-受理成功，P-处理中，F-失败 |

**返回示例**

```
 {
    "success"：true，
     "data" ：{
            "requestId " : "Req20191017001",
            "outTradeNo": "201910170001",
            "status": "P",
            "tradeNo": "2019101700000001"
    }
}
```

**备注**

* 更多返回错误代码请看首页的异常码描述



