# 代发薪接口文档

---

**简要描述：**  
    用于第三方调用工猫发薪接口.  
**请求地址**

* [/api/salary/payrollReport](https://contract-qa.gongmall.com/api/salary/payrollReport)  

**公共参数**

| 参数名 | 类型 | 长度 | 必选 | 描述 |
| --- | --- | --- | --- | --- |
| appKey | string | 是 |  | 开发者唯一标识 |
| nonce | string | 是 | 不大于32位 | 随机数，请每次随机产生，保证随机数不可预测 |
| timestamp | string | 是 |  | 当前毫秒时间戳 |
| sign | string | 是 | 见备注 | 签名 |

**请求参数**

| 参数 | 类型 | 必选 | 说明 |
| --- | --- | --- | --- |
| batchno | String | y | 批次号 |
| parameters | Object | y | 工资单详情 |

**parameters**

|参数     | 类型 |必选 | 说明  |
|---------|------|-----|-------|
|name     |String|y    | 姓名      |
|mobile|String|y    |   手机号    |
|bankAccount|String|y    |   银行卡    |   
|workNumber|String|y    |  员工号     |
|amount|String|y    |   提现金额    |
|identity|String|y    |  身份证号码     |
|dateTime|String|y    |       |
|remark|String|n    |   单据描叙    |

**返回参数说明**

|参数     | 类型 | 说明  |
|---------|------|-------|
|batchno    |String|  批次号     | 
|successNum |String|   成功笔数    |
|failNum|String|    失败笔数   |   
|failDetails|Object|    失败详情   | 

** failDetails**

|参数     | 类型 | 说明  |
|---------|------|-------|
|workNumber|String|   员工号    |
|errormsg|String|     错误原因  |
|dateTime|String|     发薪时间  |  

** 返回实例  **
 {“success”：true }
 
 **错误码**

  - [错误码链接] (https://opendoc.gongmall.com/overview/yi-chang-dai-ma.html)  

** 发薪回调（第三方提供回调地址）**

  |参数     | 类型 | 说明  |
|---------|------|-------|
|batchno    |String|  批次号     | 
|successNum |String|   成功笔数    |
|failNum|String|    失败笔数   |   
|failDetails|Object|    失败详情   | 

** failDetails**

|参数     | 类型 | 说明  |
|---------|------|-------|
|workNumber|String|   员工号    |
|errormsg|String|     错误原因  |
|dateTime|String|     发薪时间  |

** 回调返回实例  **

` {  “success”：true }` 
 
** 序列图  ** 

``` 
sequenceDiagram  

第三方 ->> 开放平台: 组装参数调用上报工资单接口  
开放平台->> 开放平台: 验证参数  
开放平台--x 第三方: 返回调用接口处理结果(上报成功或失败原因)! 
开放平台->> 算税服务: 异步调用算税处理 
算税服务->> 后台系统: 人工审核
后台系统->> 后台系统: 审核失败通知相关业务人员
后台系统->> 支付服务: 审核成功发薪请求
支付服务->> 银行网关服务: 发薪
银行网关服务 --x 支付服务: 返回发薪结果!
支付服务--x 第三方: 回调弟三方接口返回发薪结果!  
Note left of 第三方: 只需关注接口的<br/>入参和返回即可，<br/>不必关注工猫支付流程<br/>.
  
``` 
st=>start:as
``` 

[第三方] -- 提交工资单 --> B(开放平台)    
B --> C{是否提交成功}
C --参数效验成功--> D(算税服务)
C -.返回成功或失败消息.-> A
D -->E(管理后台)
E -->F{人工审核}
F --审核成功--> G(支付服务)
F --审核失败 -->H[业务方人工处理]
G --调用银行支付-->I(银行服务)
I -.支付结果回调第三方接口.-> A
```



