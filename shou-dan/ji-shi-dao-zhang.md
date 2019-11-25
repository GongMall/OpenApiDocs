* ### 即时到账

---

**简要描述：**

* B端商户平台发起收单交易请求

**请求URL：**

* /api/instant/trade

**请求方式：**

* POST 

**参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| bizContent | 是 | json格式 | 订单信息 |

**业务参数bizContent格式：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| requestId | 是 | string | 客户请求标识,最长32位\(用户提现时企业系统自动生成，每个requestId代表一个提现请求，工猫作为每笔提现记录的唯一标识\) |
| tradeInfo | 是 | json（列表） | 交易信息 |
| payerIp | 是 | string | 买家ip地址 |
| payMethod | 是 | json | 支付方式，根据不同的业务场景选择合适的支付方式 |
| bizProductCode | 是 | string | 业务产品码，20701（即时到账-先分账后结算） |
| cashierType| 是 | string | 收银台类型，API（接口形式），SDK（app集成sdk模式） |
| timeoutExpress | 否 | string | 逾期时间，取值范围：0或10m～7d。m-分钟，h-小时，d-天。 |
| terminalInfo | 是 | json | 终端信息域，terminal\_type终端类型 |

**terminalInfo终端信息域参数**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| terminal\_type | 是 | string | 终端类型，00-电脑，01-手机，02-平板设备，03-可穿戴设备，04-数字电视，99-其他，只需要填写类型的代码，例如01 |

**tradeInfo交易信息参数**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| outTradeNo | 是 | string | 商户订单号 |
| subject | 是 | string | 商品名称，商品的标题/交易标题/订单标题/订单关键字等 |
| currency | 否 | string | 币种，默认人民币 CNY |
| price | 是 | string | 商 品 单 价 ， 取 值 范 围 为 \[0.01 ，100000000000.00\]，精确到小数点后两位 |
| quantity | 是 | string | 商品数量必须为大于0的整数 |
| totalAmount | 是 | string | 交易金额=\(商品单价×商品数量\)，取值范围为\[0.01 ，100000000000.00\]，精确到小数点后两位。 |
| payeeIdentity | 是 | string | 卖家会员 ID |
| royaltyInfo | 否 | json（列表） | 分润账号集，最多支持 10 个分润账号 |

**royaltyInfo分润账号信息参数**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| payeeMemberId | 是 | string | 分账会员ID |
| amount | 是 | string | 分账金额 ，取值范围为\[0.01 ，100000000000.00\]，精确到小数点后两位。 |

**payMethod支付方式参数**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| payProductCode | 是 | string | 支付产品码，64表示主扫-借记卡，65表示主扫-综合，只需要填写产品码，例如65 |
| amount | 是 | string | 应付金额， 取值范围为\[0.01 ，100000000000.00\]，精确到小数点后两位。 |
| targetOrganization | 是 | string | 目标机构, WECHAT:微信, ALIPAY:支付宝, UPOP:银联 |
| appId | 否 | string | 公众号appid，请填写已进件成功的APP\_ID。若以平台方名义进件，请填写平台方APP\_ID |
| openId | 否 | string | 微信用户标识必填 |
| buyerId | 否 | string | 支付宝用户标识必填 |

**返回参数说明**

| 参数名 | 类型 | 说明 |
| :--- | :--- | --- |
| requestId | string | 客户请求标识 |
| returnUrl | string | 扫码的url地址 |
| tradeResList| string | json（列表） |
| appId| string  | 微信公众号ID，供JSAPI调用字段|
| nonceStr| string | 随机字符串，供JSAPI调用字段|
| timeStamp| string | 时间戳，供JSAPI调用字段 |
| prepayId| string | 预支付交易会话标识，预支付会话标识，该值有效期为20分钟，供JSAPI调用|
| extPackage| string | 订单详情扩展字符串，供JSAPI调用字段，对应微信接口中的package字段|
| signType| string | 签名，供JSAPI调用字段|
| paySign| string | 签名，供JSAPI调用字段|
| instAmount| string | 订单金额 |

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
        "returnUrl": "weixin://wxpay/bizpayurl?pr=fEyU393",
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



