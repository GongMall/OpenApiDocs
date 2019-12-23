### 算税结果回调

---

**简要描述：**

* 算税结果回调

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
| totalNum | integer | 总人数 |
| taxCount | integer | 算税条数 |
| canPay | integer | 是否可以支付\(0：否，1：是\) |
| taxCalculationDate | string | 算税日期 |
| failureTime | string | 失效时间 |
| actuallyPaidInAmount | string | 员工应到账总额 |
| taxAmount | string | 个税应付总金额 |
| addValueTaxAmount | string | 增值税应付总金额 |
| addTaxAmount | string | 附加税应付总金额 |
| manageFeeAmount | string | 管理费应付金额 |
| corporatePaymentAmount | string | 商户应支付总金额 |
| taxDetail | json数组 | 算税成功明细 |
| failDetail | json数组 | 算税失败明细 |

taxDetail字段明细

| 参数名 | 类型 | 说明 |
| :--- | :--- | :--- |
| customerOrderNum | string | 商户明细序号 |
| name | string | 员工姓名 |
| idNumber | string | 身份证号 |
| mobile | string | 手机号 |
| salaryAccount | string | 收款帐号 |
| salaryAmount | string | 传入的应发金额 |
| monthRealWageSum | string | 员工月到账已发累计金额 |
| corporatePaymentAmount | string | 企业支出金额 |
| taxAmount | string | 个税金额 |
| addTaxAmount | string | 附加税金额 |
| addValueTaxAmount | string | 增值税金额 |
| manageFeeAmount | string | 管理费金额 |
| actuallyPaidInAmount | string | 个人实际到账金额 |

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
    "bizContent": {
        "batchNum": "20191223",
        "totalNum": 3,
        "taxCount": 3,
        "canPay": 0,
        "taxCalculationDate": "2019-12-23",
        "failureTime": "2019-12-31",
        "actuallyPaidInAmount": 0,
        "taxAmount": 0,
        "addValueTaxAmount": 0,
        "addTaxAmount": 0,
        "manageFeeAmount": 0,
        "corporatePaymentAmount": 0,
        "taxDetail": [{
            "customerOrderNum": "003",
            "name": "周勇",
            "idNumber": "340826199511301419",
            "mobile": "15656597221",
            "salaryAccount": "6214835907152068",
            "salaryAmount": 0.25,
            "monthRealWageSum": 27.95,
            "corporatePaymentAmount": 0.25,
            "taxAmount": 0.00,
            "addTaxAmount": 0.00,
            "addValueTaxAmount": 0.00,
            "manageFeeAmount": 0.00,
            "actuallyPaidInAmount": 0.25
        }],
        "failDetail": []
    }
}
```

**备注**




