### 提现结果回调处理
---
**简要描述：** 

- 提现结果回调，银行处理完成后系统进行回调；回调的时间会晚于银行实际到账的时间

**请求URL：** 
- `开发者信息提供的实时提现结果回调地址`
  
**请求方式：**
- POST 

**参数：** 

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
|requestId |是  |string |客户请求标识(流水号)   |
|status |是  |string | 状态(1:成功 2:失败)    |
|failReason  |否  |string | 如果失败，失败原因    |
|name  |是  |string | 姓名    |
|mobile  |是  |string | 手机号    |
|amount  |是  |string | 提现金额    |
|identity  |是  |string | 身份证号码    |
|bankName  |是  |string | 银行名称    |
|bankAccount  |是  |string | 银行卡    |
|dateTime  |是  |string | 申请时间(yyyyMMddHHmmss)    |
|payTime  |是  |string | 实际付款时间(yyyyMMddHHmmss)    |
|remark  |否  |string | 单据描叙    |

 **返回参数说明** 

请返回json格式的任何结果，表明已成功接收

 **备注** 

- 如需要验签，请参照请求接口规范中的签名方式进行验证