### 提交付款请求

---

**简要描述：**

* 接入方提交付款请求

**请求URL：**

* /api/bulkPayroll/payPayroll

**请求方式：**

* POST 

**输入参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| batchNum | 是 | string | 批次号 |
| captcha | 是 | string | 短信验证码 |
| corporatePaymentAmount | 是 | string | 发薪总金额 |
| payCount | 是 | integer | 发薪总笔数 |

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

* 更多返回错误代码请看首页的异常码描述



