### 提交付款请求回调

---

**简要描述：**

* 提交付款请求回调

**请求URL：**

* `开发者信息提供的交易退款回调地址`

**请求方式：**

* POST

**参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| bizContent | 是 | json格式 | 算税结果数据 |

bizContent字段明细

| 参数名 | 类型 | 说明 |
| :--- | :--- | --- |
| batchNum | string | 批次号 |
| payStatus | integer | 支付状态 |
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
| name | integer | 员工姓名 |
| idNumber | string | 身份证号 |
| mobile | string | 手机号 |
| salaryAccount | string | 收款帐号 |
| salaryAmount | string | 传入的应发金额 |
| failReason | string | 失败原因 |

**返回参数说明**

| 参数名 | 类型 | 说明 |
| :--- | :--- | --- |
| status | int | 0处理成功，1处理失败 |

**返回示例**

```json
{
	"success": true,
	"data": {
		"batchNum": "12241540",
		"payStatus": 2,
		"paySuccessDetails": [{
			"customerOrderNum": "12-2401",
			"name": "纪玲",
			"idNumber": "420322199312037229",
			"mobile": "17557285044",
			"salaryAccount": "6214835892461078",
			"salaryAmount": 8.88,
			"corporatePaymentAmount": 8.97,
			"taxAmount": 0.53,
			"addTaxAmount": 0.02,
			"addValueTaxAmount": 1.06,
			"manageFeeAmount": 0.09,
			"actuallyPaidInAmount": 7.27,
			"payDate": "2019-12-24 16:04:51"
		}],
		"payFailDetails": []
	}
}
```

**备注**

