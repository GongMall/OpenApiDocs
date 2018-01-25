### 查询提现结果
---  
**简要描述：** 

- 提现结果查询
    根据企业所提供的回调地址，银行转账处理成功后，系统会通过回调地址返回提现结果。也可通过如下接口自主查询。
    

**请求URL：** 
- ` /api/withdraw/getWithdrawResult `
  
**请求方式：**
- POST 

**参数：** 

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
|requestId |是  |string |客户请求标识(流水号)   |


 **返回参数说明** 

|参数名|类型|说明|
|:-----  |:-----|-----                           |
|requestId |String   |客户请求标识  |
|status |Integer   |1：成功 2：失败 4：处理中 |
|failReason |String   |失败原因  |
|mobile |string | 手机号    |
|name     |string | 姓名    |
|amount |BigDecimal |提现金额   |
|identity |string |身份证号码   |
|bankName |string |银行名称   |
|bankAccount |string |银行卡号  |
|dateTime |string |申请时间(yyyyMMddHHmmss)   |
|payTime |string |实际付款时间(yyyyMMddHHmmss)   |
|remark |string |单据描述   |

 **返回示例**

``` 
{
	“success”：false，
		“data”：{
		“requestId”: ”12304” ,//客户请求标识
		“status”: ”2” ,//失败
		“failReason”: ”企业余额不足” //失败原因
		“mobile”：“18500615259”，//手机号
		“name”：“王鑫鑫”，//姓名
		“amount”：“1000”//提现金额
		“identity”：“620902198909280125”//身份证号
		“bankAccount”：“6214830100799682”//银行卡号
		“dateTime”：“2016-01-25 13:23:56”//申请时间
		“payTime”：“2016-01-25 13:25:56”//实际付款时间
	}
}
```

 **备注** 

- 更多返回错误代码请看首页的异常码描述


