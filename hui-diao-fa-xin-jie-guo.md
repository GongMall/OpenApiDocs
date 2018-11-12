# 回调单笔发薪结果

---

**简要描述：**  
        按照工资单进行工资发放后，回调给客户发薪信息。 
**请求地址**

* 开发者信息提供的工资发放信息回调地址  

**请求方式**
* POST

**返回参数说明**

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

返回参数说明：
请返回 json 格式的任何结果，表明已成功接收
