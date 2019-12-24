### 主动查询支付结果

---

**简要描述：**

* 接入方主动查询支付结果

**请求URL：**

* /api/bulkPayroll/queryPayInfo

**请求方式：**

* POST 

**请求参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| batchNum | 是 | string | 批次号\(唯一\) |

**返回参数说明**

| 参数名 | 类型 | 说明 |
| :--- | :--- | --- |
| batchNum | string | 批次号 |
| payStatus | integer | 支付状态\(-2:已撤销，5:计算税费中，0:待付款，1:付款中，2:付款完成\) |
| paySuccessDetails | json数组 | 付款成功集合 |
| payFailDetails | json数组 | 付款失败集合 |

taxDetail字段明细

| 参数名 | 类型 | 说明 |
| :--- | :--- | :--- |
| customerOrderNum | string | 商户明细序号 |
| name | string | 员工姓名 |
| idNumber | string | 身份证号 |
| mobile | string | 手机号 |
| salaryAccount | string | 收款帐号 |
| salaryAmount | string | 传入的应发金额 |
| corporatePaymentAmount | string | 企业支出金额 |
| taxAmount | string | 个税金额 |
| addTaxAmount | string | 附加税金额 |
| addValueTaxAmount | string | 增值税金额 |
| manageFeeAmount | string | 管理费金额 |
| actuallyPaidInAmount | string | 个人实际到账金额 |
| payDate | string | 支付时间 |

failDetail字段明细

| 参数名 | 类型 | 说明 |
| :--- | :--- | :--- |
| customerOrderNum | string | 商户明细序号 |
| name | string | 员工姓名 |
| idNumber | string | 身份证号 |
| mobile | string | 手机号 |
| salaryAccount | string | 收款帐号 |
| salaryAmount | string | 传入的应发金额 |
| failReason | string | 失败原因 |

**返回示例**

```json
{
	"success": true,
	"data": {
		"batchNum": "12231832",
		"companyId": 120,
		"payStatus": 2,
		"paySuccessDetails": [{
			"customerOrderNum": "001",
			"name": "纪玲",
			"idNumber": "420322199312037229",
			"mobile": "17557285044",
			"salaryAccount": "6214835892461078",
			"salaryAmount": 1.11,
			"corporatePaymentAmount": 1.12,
			"taxAmount": 0.00,
			"addTaxAmount": 0.00,
			"addValueTaxAmount": 0.00,
			"manageFeeAmount": 0.01,
			"actuallyPaidInAmount": 1.11,
			"payDate": "2019-12-23T10:47:50Z"
		}],
		"payFailDetails": []
	}
}
```

**备注**

* 更多返回错误代码请看首页的异常码描述



