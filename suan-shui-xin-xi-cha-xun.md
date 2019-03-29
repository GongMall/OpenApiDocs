### 算税信息

---

**简要描述：**

* 已签约员工在企业客户端发起提现请求前，查看其所需要缴纳的个税、管理费及实际到账金额等信息。(查询个税及管理费是在用户前一笔成功的前提下计算得出，若前一笔提现失败或正在处理中，则不包含在内。)

**请求URL：**

* /api/withdraw/getTaxInfo

**请求方式：**

* POST 

**参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | :--- |
| requestId | 是 | string | 客户请求标识,最长32位（用户提现时企业系统自动生成，每个requestId代表一个提现请求，工猫作为每笔提现记录的唯一标识） |
| mobile | 是 | string | 手机号 |
| name | 是 | string | 姓名 |
| amount | 是 | BigDecimal | 提现金额 |
| identity | 是 | string | 身份证号码 |
| bankAccount | 是 | string | 银行卡/支付宝 |
| dateTime | 是 | string | 申请时间\(yyyyMMddHHmmss\) |
| remark | 否 | string | 单据描叙，最长200位 |

**返回参数说明**

| currentRealWage | BigDecimal | 实发金额 |
| :--- | :--- | :--- |
| currentManageFee | BigDecimal | 管理费金额 |
| manageFeeBearType | int | 管理费承担（0：企业 1：个人） |
| currentTax | BigDecimal | 个税金额 |
| taxBearType | int | 个税承担（0：企业 1：个人） |

**返回示例**

```
 {
    “success”：true，
     “data” ：{
      “currentRealWage”: 123 //实发金额
      “currentManageFee”: 10 //管理费金额
      “manageFeeBearType”: 0 //企业承担
      “currentTax”: 10 //个税金额
      “taxBearType”：1//个人承担
    }
}
```

**备注**

* 更多返回错误代码请看首页的异常码描述



