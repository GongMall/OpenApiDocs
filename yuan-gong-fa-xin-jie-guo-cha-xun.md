# 员工发薪结果查询

---

**简要描述：**  
   工资单导入进行发薪操作后，查询发薪结果。 
**请求地址**

* [/api/payroll/getPayResult](https://openapiqa.gongmall.com/api/payroll/getPayResult)   

**请求方式**

* POST

**请求参数**

|参数     | 类型 | 必选 | 说明  |
|---------|----|---|-------|
|requestId|String|y|单笔请求标识(全局唯一，最大长度32位)   | 

** 返回参数**

|参数     | 类型 | 说明  |
|---------|------|-------|
|success|boolean|   请求是否成功    |
|data|Object| 返回信息主体  | 

** data**

|参数     | 类型 | 说明  |
|---------|------|-------|
|requestId|String|   单笔请求标识    |
|name|String| 姓名  | 
|salaryAccount|String| 银行卡号 |
|amount|BigDecimal|   提现金额    |
|tax|BigDecimal| 个税  | 
|manageFee|BigDecimal| 管理费|
|realWage|BigDecimal|实际到账金额   |
|status|String| 单笔处理状态(-1:处理失败 -2:已撤销0:待处理 1:处理中 2:处理成功) | 
|failReason|String| 如果失败，失败原因 |

** 返回示例**
```
{
"success": true,
"data": {
"requestId": "123456",
"status": "1"
}
```







