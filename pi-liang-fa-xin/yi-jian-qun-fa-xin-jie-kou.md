### 提交付款请求

---

**简要描述：**

* 接入方提交付款请求

**请求URL：**

* /api/bulkPayroll/payPayroll

**请求方式：**

* POST 

**请求参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| batchNum | 是 | string | 批次号\(唯一\) |
| captcha | 是 | string | 短信验证码 |
| corporatePaymentAmount | 是 | string | 企业支出金额，该参数取自算税回调结果中的corporatePaymentAmount；税费实时结算时，帐户余额需大于等于该金额。 |
| actuallyPaidInAmount | 是 | string | 个人实际到账金额，该参数取自算税回调结果中的actuallyPaidInAmount；税费月结时，帐户余额需大于等于该金额。 |
| payCount | 是 | integer | 支付明细条数 |

**返回参数说明：**

| 参数名 | 类型 | 说明 |
| :--- | :--- | :--- |
| suceess | boolean | true：调用成功，false：调用失败 |

**返回参数格式示例**

```json
{
    "success": true
}
```

**备注**

* 仅支持在确认工猫算税结果情况下，进行支付。如对算税结果不认可，可以申请取消发薪订单，作废整个批次。



