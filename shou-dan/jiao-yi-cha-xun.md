* ### 交易查询

---

**简要描述：**

* B端商户平台发起交易明细查询

**请求URL：**

* /api/instant/query

**请求方式：**

* POST 

**输入参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| outTradeNo | 否 | string | 商户订单号，与tradeNo 二选一 |
| tradeNo | 否 | string | 平台订单号，与outTradeNo 二选一 |

**返回参数说明：**

| 参数名 | 是否必填 | 类型 | 说明 |
| :--- | :--- | :--- | :--- |
| outTradeNo | 是 | string | 商户订单号 |
| tradeNo | 是 | string | 平台订单号 |
| subject | 是 | string | 商品名称，商品的标题/交易标题/订单标题/订单关键字等 |
| price | 是 | string | 商 品 单 价 ， 取 值 范 围 为 \[0.01 ，100000000000.00\]，精确到小数点后两位 |
| quantity | 是 | string | 商品数量必须为大于0的整数 |
| totalAmount | 是 | string | 交易金额=\(商品单价×商品数量\)，取值范围为\[0.01 ，100000000000.00\]，精确到小数点后两位。 |
| payeeIdentity | 是 | string | 卖家会员 ID |
| payeeName | 是 | string | 卖家会员名称 |
| partnerFee | 否 | string | 平台手续费 |
| payeeFee | 否 | string | 卖家手续费 |
| payerFee | 否 | string | 买家手续费 |
| status | 是 | string | 交易状态 |
| royaltyInfo | 否 | json（列表） | 分润账号集，最多支持 10 个分润账号 |

royaltyInfo分润账号信息参数

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| payeeMemberId | 是 | string | 分账会员ID |
| payeeName | 是 | string | 分账会员名称 |
| amount | 是 | string | 分账金额 ，取值范围为\[0.01 ，100000000000.00\]，精确到小数点后两位。 |

**返回参数格式示例**
```

{
	"outTradeNo": "201910170001",
	"tradeNo": "P201910170001",
	"subject": "商品的标题",
	"totalAmount": "33.69",
	"payeeIdentity": "100",
	"payeeName": "收单方姓名",
	"partnerFee": "0.00",
	"payeeFee": "0.50",
	"payerFee": "0.00",
	"status": "待付款",
	"price": "11.23",
	"quantity": "3",
	"royaltyInfo": [{
		"amount": "12.45",
		"payeeName": "分账方姓名",
		"payeeMemberId": "1000"
	}]
}
```


**备注**

* 更多返回错误代码请看首页的异常码描述



