
# 代发薪接口文档  
---
  
**简要描述：**
    用于第三方调用工猫发薪接口.
**请求地址**
- [/api/salary/payrollReport](https://contract-qa.gongmall.com/api/salary/payrollReport)  

**公共参数**  
  
|参数名|类型  |长度  |必选  |描述 |
|----------|--|--|--|--|
|appKey    |string | 是 |  | 开发者唯一标识 |
|nonce     |string | 是 | 不大于32位 | 随机数，请每次随机产生，保证随机数不可预测 |
|timestamp |string | 是 |  | 当前毫秒时间戳 |
|sign      |string |  是|  见备注  |签名 |

**请求参数**
  
|参数     | 类型 |必选 | 说明  |
|---------|------|-----|-------|
|batchno    |String|y    | 批次号      | 
|parameters| Object|y    |  工资单详情     |


|参数     | 类型 |必选 | 说明  |




