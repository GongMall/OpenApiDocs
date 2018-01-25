### 提现
--- 
**简要描述：** 

- 已签约员工在企业客户端发起提现请求，企业调用提现接口提交请求，将指定金额转入员工账户。
    
**请求URL：** 
- ` /api/withdraw/doWithdraw `
  
**请求方式：**
- POST 

**参数：** 

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
|requestId |是  |string |客户请求标识(流水号),最长32位   |
|mobile |是  |string | 手机号    |
|name     |是  |string | 姓名    |
|amount |是  |BigDecimal |提现金额   |
|identity |是  |string |身份证号码   |
|bankAccount |是  |string |银行卡   |
|dateTime |是  |string |申请时间(yyyyMMddHHmmss)   |
|remark |否 |string |单据描叙   |


 **返回参数说明** 

|参数名|类型|说明|
|:-----  |:-----|-----                           |
|requestId |String   |客户请求标识  |
|opflag |Integer   |0：失败 1：成功 |
|identity |String   |身份证号码  |
|appmentTime |String   |提交成功时间(yyyyMMddHHmmss) |

 **返回示例**

``` 
 {
	“success”：true，
 	“data” ：{
  	“resultId”: ”12304” //提现流程实例号
	  “identity”：“620902198909280125”//身份证号
	}
}
```

 **备注** 

- 更多返回错误代码请看首页的异常码描述

