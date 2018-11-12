### 修改员工银行卡

---

**简要描述：**

* 根据业务需求，银行卡采集通过客户的系统，所以当用户银行卡发生变更时，客户需通知我们变更信息，保证双方系统信息同步，确保提现成功。

**请求URL：**

* /api/employee/syncBankAccount

**请求方式：**

* POST 

**参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| name | 是 | string | 姓名 |
| mobile | 是 | string | 手机号 |
| identity | 是 | string | 身份证号 |
| oldBankName | 否 | string | 原始银行名称 |
| oldBankAccount | 是 | string | 原始银行卡号 |
| newBankName | 否 | string | 变更银行名称 |
| newBankAccount | 是 | string | 变更银行卡号 |

**返回参数说明**

| 参数名 | 类型 | 说明 |
| :--- | :--- | --- |
| success | boolean | 请求结果，true：成功；false：失败 |
| errorCode | string | 错误码 |
| errorMsg | string | 失败原因 |

**返回示例**

```
 {
    “success”：true
 }
```

**备注**

* 更多返回错误代码请看首页的异常码描述



