# 自发薪接口文档

---

**简要描述：**  
    用于第三方调用工猫发薪接口.  
**请求地址**

* [/api/payroll/importPayroll]   

**请求方式**
* POST
**请求参数**

| 参数 | 类型 | 必选 | 说明 |
| --- | --- | --- | --- |
| batchNum | String | y |上传批次号(全局唯一，最大长度32位) |
| payrollContent| String| y | 工资单详情（json字符串，最大笔数1000笔） |

**payrollContent**

|参数     | 类型 |必选 | 说明  |
|---------|------|-----|-------|
|requestId |String|y    | 单笔请求标识(全局唯一，最大长度32位)|
|name     |String|y    | 姓名      |
|salaryAccount|String|y    |   银行卡 |   
|amount|String|y    |   提现金额    |
|identity|String|y    |  身份证号码   |
|dateTime|String|y    |    发薪时间（yyyyMMddHHmmss）   |

**返回参数说明**

|参数     | 类型 | 说明  |
|---------|------|-------|
|success|boolean|请求是否成功    | 
|data|Object|如果成功，成功数据     |
|errorCode|String|如果失败，错误码     |  
|errorMsg|String|    如果失败：失败原因（1、数据量过大，大于 1000 条 2、批次号已存在 3、输入参数格式不正确：工资单详情有空白值）   | 

** data**

|参数     | 类型 | 说明  
|---------|------|-------|
|batchNum|String|   上传批次号(全局唯一，最大长度32位    |
|status |String|     0:处理中 1:处理完成  | 

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

