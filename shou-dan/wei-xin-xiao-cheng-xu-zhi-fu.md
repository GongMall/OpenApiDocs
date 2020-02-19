* ### 微信小程序支付

---

**简要描述：**

* B端商户平台发起微信小程序支付请求

**请求URL：**

* /api/instant/pay/wxminiprogram

**请求方式：**

* POST 

**参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| bizContent | 是 | json格式 | 小程序支付请求信息 |

**业务参数bizContent格式：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| requestId | 是 | string | 客户请求标识,最长32位，由发起请求的商户平台生成，作为双方系统交互的唯一标识，商户平台需要确保该标识的唯一性|
| appId | 否 | string | 小程序appid，请填写已进件成功的APP\_ID。若以平台方名义进件，请填写平台方APP\_ID |
| terminalPayerId| 否 | string | 微信用户标识必填，小程序的openid |
| targetOrganization | 是 | string | 目标机构, WECHAT:微信 |
| payToken | 是 | string | 即时交易接口返回的支付token |

**返回参数说明**

| 参数名 | 类型 | 说明 |
| :--- | :--- | --- |
| requestId | string | 客户请求标识 |
| tradeResList | string | json（列表） |
| appId | string | 微信公众号ID，供JSAPI调用字段 |
| nonceStr | string | 随机字符串，供JSAPI调用字段 |
| timeStamp | string | 时间戳，供JSAPI调用字段 |
| prepayId | string | 预支付交易会话标识，预支付会话标识，该值有效期为20分钟，供JSAPI调用 |
| extPackage | string | 订单详情扩展字符串，供JSAPI调用字段，对应微信接口中的package字段 |
| signType | string | 签名，供JSAPI调用字段 |
| paySign | string | 签名，供JSAPI调用字段 |
| instAmount | string | 订单金额 |

**tradeResList参数**

| 参数名 | 类型 | 说明 |
| :--- | :--- | --- |
| outTradeNo | string | 商户订单号 |
| tradeNo | string | 平台订单号 |
| status | string | 处理状态，S-成功，P-处理中，F-失败 |

请求参数bizContent的格式示例

{

"bizProductCode": "20701",

```
"payMethod": {

    "amount": "122.89",

    "payProductCode": "65",

    "targetOrganization": "WECHAT"

},

"payerIp": "11.22.33.44",

"terminalInfo": {

    "terminal_type": "01"

},

"timeoutExpress": "30m",

"tradeInfo": [{

        "currency": "",

        "outTradeNo": "201910170001",

        "payeeIdentity": "100",

        "price": "11.23",

        "quantity": "3",

        "royaltyInfo": [{

            "amount": "12.45",

            "payeeIdentityType": "1",

            "payeeMemberId": "1000"

        }],

        "subject": "商品的标题",

        "totalAmount": "33.69"

}]
```

}

**返回示例**

```
 {
    "success"：true，
     "data" ：{
        "appId": "wx9236b1e84ffbf10a",
        "timeStamp": "1573029856",
        "nonceStr": "19a855c337bd4c14978899a560372a97",
        "prepayId": "wx061644162685653f3da37a5a1589465200",
        "extPackage": "prepay_id=wx061644162685653f3da37a5a1589465200",
        "signType": "RSA",
        "paySign":"tEwMVv5wrcgvrMG4U5kFgIyegLZArNeMwgyDwetmgsRXWT8asx1Jxgg0iVoJrTI5IR4tslK9w6mVXGeggv3GTZG8pXIJr9EfyBhR3wuTH0M9CJK0Y3+X0cRCOSvfviqrLkGzFSdFXWyE/K9XiVkQTtkLV/witiqjUI7sdEwSPwTtWnCzMaLn4iTUM2ER1mK5jcNpeRiiUOfyq78B21E3iqOtdAfYbb/jqhTPj7J5UQfw3/sHLcxi6luaWSpxdcZCstgQd0IDFDF/EqMQ6A9WJSPgzZ/inNFXA17u67b7YSjfIkdd1L3zQuoM4CQUFgCAvdnTCl40FjkUBpGBToxShg==",
        "instAmount": "0.10",
        "tradeResList": [{
            "outTradeNo": "201910170001",
            "status": "P",
            "tradeNo": "2019101700000001"
        }, {
            "outTradeNo": "201910170001",
            "status": "P",
            "tradeNo": "2019101700000001"
        }]
    }
}
```

**备注**

* 更多返回错误代码请看首页的异常码描述



