### 提现结果回调处理

---

**简要描述：**

* 提现结果回调，银行处理完成后系统进行回调；回调的时间会晚于银行实际到账的时间

**请求URL：**

* `开发者信息提供的实时提现结果回调地址`

**请求方式：**

* POST 

**参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| requestId | 是 | string | 客户请求标识，最长32位（用户提现时企业系统自动生成，每个requestId代表一个提现请求，工猫作为每笔提现记录的唯一标识） |
| status | 是 | string | 状态\(1:成功 2:失败\) |
| failReason | 否 | string | 如果失败，失败原因 |
| name | 是 | string | 姓名 |
| mobile | 是 | string | 手机号 |
| amount | 是 | string | 提现金额 |
| currentTax| 是 | string | 当次缴纳个税 |
| currentRealWage | 是 | string | 实发金额 |
| currentManageFee | 是 | string | 当次提现管理费 |
| addTaxBearType| 是 | string | 增值税附加税承担方式（0:公司 1:个人） |
| currentAddTax| 是 | string | 当次提现附加税 |
| currentAddValueTax| 是 | string | 当次提现增值税 |
| identity | 是 | string | 身份证号码 |
| bankName | 是 | string | 银行名称 |
| bankAccount | 是 | string | 银行卡 |
| dateTime | 是 | string | 申请时间\(yyyyMMddHHmmss\) |
| payTime | 是 | string | 实际付款时间\(yyyyMMddHHmmss\) |
| remark | 否 | string | 单据描叙 |

**返回参数说明**

回调response
结果（status=200 && isNotEmpty(responseBody)）为成功，
其他情况（status !=200 || isEmpty(responseBody))为失败
**返回示例**

成功：
```
成功：
{
    “success”：true
}
```

**备注**

* 如需要验签，请参照请求接口规范中的签名方式进行验证



