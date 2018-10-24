# 自发薪接口文档

---

**简要描述：**  
    用于第三方调用工猫发薪接口.  
**请求地址**

* [/api/payroll/payrollReport]   

**请求参数**

| 参数 | 类型 | 必选 | 说明 |
| --- | --- | --- | --- |
| requestId | String | y | 当前请求唯一标识 |
| parameters | List | y | 工资单详情 |

**parameters**

|参数     | 类型 |必选 | 说明  |
|---------|------|-----|-------|
|orderId     |String|y    | 订单号全局唯一|
|name     |String|y    | 姓名      |
|mobile|String|y    |   手机号    |
|bankAccount|String|y    |   银行卡    |   
|workNumber|String|y    |  员工号     |
|amount|String|y    |   提现金额    |
|identity|String|y    |  身份证号码     |
|dateTime|String|y    |    发薪时间   |
|remark|String|n    |   单据描叙    |

**返回参数说明**

|参数     | 类型 | 说明  |
|---------|------|-------|
|requestId    |String|请求唯一标识     | 
|status    |String|处理状态     |
|msg    |String|失败原因     |  
|failDetails|List|    失败详情   | 

** failDetails**

|参数     | 类型 | 说明  
|---------|------|-------|
|orderId|String|   订单号全局唯一    |
|errormsg|String|     错误原因  | 

** 返回实例  **
 {“success”：true }
 
 **错误码**

  - [错误码链接] (https://opendoc.gongmall.com/overview/yi-chang-dai-ma.html)  

** 发薪回调（第三方提供回调地址）**

  |参数     | 类型 | 说明  |
|---------|------|-------|
|requestId    |String|  请求唯一标识     | 
|successNum |String|   成功笔数    |
|failNum|String|    失败笔数   |   
|failDetails|List|    失败详情   | 

** failDetails**

|参数     | 类型 | 说明  |
|---------|------|-------|
|orderId|String|   订单号    |
|errormsg|String|     错误原因  |
|dateTime|String|     发薪时间  |

** 回调返回实例  **

` {  “success”：true }` 

``` 
![](/assets/序列图.png) 

![](/assets/流程图.png)

