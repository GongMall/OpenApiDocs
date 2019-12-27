### 日对账单查询

---

**简要描述：**

* 接入方查询日对账单，目前仅支持批次账单，明细帐可通过支付查询（按批）接口获取。

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
| batchNum | string | 批次号 |
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
    "success": true,
    "data": {
        "billDate": "2019-12-23",
        "batchCount": 3,
        "payeeCount": 5,
        "batchStatementList": [{
            "batchNum": "12231832",
            "payeeCount": 1
            "payDate": "2019-12-23 18:47:49",
            "corporatePaymentAmount": "1.12",
            "taxAmount": "0.00",
            "addTaxAmount": "0.00",
            "addValueTaxAmount": "0.00",
            "manageFeeAmount": "0.01",
            "actuallyPaidInAmount": "1.11"
        }],
        "corporatePaymentAmount": "0",
        "taxAmount": "0",
        "addTaxAmount": "0",
        "addValueTaxAmount": "0",
        "manageFeeAmount": "0",
        "actuallyPaidInAmount": "0"
    }
}
```

**备注**

* t+1 日即可调用对账接口获取t日支付成功交易明细数据，满足对手方日对账的需要。



