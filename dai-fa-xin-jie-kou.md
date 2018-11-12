# 批量上传工资单

---

**简要描述：**  
    用于第三方调用工猫发薪接口.返回请求结果  
**请求地址**

* /api/payroll/importPayroll

**请求方式**

* POST

**请求参数**

| 参数 | 类型 | 必选 | 说明 |
| --- | --- | --- | --- |
| batchNum | String | 是 | 上传批次号\(全局唯一，最大长度32位\) |
| payrollContent | String | 是 | 工资单详情（json字符串，最大笔数1000笔） |

**payrollContent**

| 参数 | 类型 | 必选 | 说明 |
| --- | --- | --- | --- |
| requestId | String | 是 | 单笔请求标识\(全局唯一，最大长度32位\) |
| name | String | 是 | 姓名 |
| salaryAccount | String | 是 | 银行卡 |
| amount | String | 是 | 提现金额 |
| identity | String | 是 | 身份证号码 |
| dateTime | String | 是 | 发薪时间（yyyyMMddHHmmss） |

**返回参数说明**

| 参数 | 类型 | 说明 |
| --- | --- | --- |
| success | boolean | 请求是否成功 |
| data | Object | 如果成功，成功数据 |
| errorCode | String | 如果失败，错误码 |
| errorMsg | String | 如果失败：失败原因（1、数据量过大，大于 1000 条 2、批次号已存在 3、输入参数格式不正确：工资单详情有空白值） |

** data**

| 参数 | 类型 | 说明 |
| --- | --- | --- |
| batchNum | String | 上传批次号\(全局唯一，最大长度32位） |
| status | String | 0:处理中 1:处理完成 |

** 返回实例  **

```
{
"success": true,
"data": {
    "batchNum": "20180410044",
    "status": "0"
    }
}
```



