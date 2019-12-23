### 日对账单查询

---

**简要描述：**

* 接入方查询日对账单

**请求URL：**

* /api/bulkPayroll/queryDailyPayOrder

**请求方式：**

* POST 

**请求参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| date | 是 | string | 日期\(格式：yyyy-MM-dd\) |

**返回参数说明**

| 参数名 | 类型 | 说明 |
| :--- | :--- | --- |
| billDate | string | 账单日 |
| batchCount | integer | 批次数 |
| payeeCount | integer | 收款人次数 |
| corporatePaymentAmount | string | 企业支出金额 |
| taxAmount | string | 个税金额 |
| addTaxAmount | string | 附加税金额 |
| addValueTaxAmount | string | 增值税金额 |
| manageFeeAmount | string | 管理费金额 |
| actuallyPaidInAmount | string | 个人实际到账金额 |
| batchStatementList | json数组 | 批次账 |

batchStatementList字段明细

| 参数名 | 类型 | 说明 |
| :--- | :--- | :--- |
| batchNum | string | 日期\(格式：yyyy-MM-dd\) |
| payeeCount | integer | 收款人次 |
| payDate | string | 支付时间 |
| corporatePaymentAmount | string | 企业支出金额 |
| taxAmount | string | 个税金额 |
| addTaxAmount | string | 附加税金额 |
| addValueTaxAmount | string | 增值税金额 |
| manageFeeAmount | string | 管理费金额 |
| actuallyPaidInAmount | string | 个人实际到账金额 |

**返回示例**

```json
{
    "success": true
}
```

**备注**

* t+1 日即可调用对账接口获取t日支付成功交易明细数据，满足对手方日对账的需要。



