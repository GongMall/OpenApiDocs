### 查询员工合同状态
---
**简要描述：** 

- 员工合同状态查询

**请求URL：** 
- ` /api/employee/getContractStatus `
  
**请求方式：**
- POST 

**参数：** 

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
|mobile |是  |string |手机号   |
|name |是  |string | 姓名    |
|identity     |是  |string | 身份证号    |


 **返回参数说明** 

|参数名|类型|说明|
|:-----  |:-----|-----                           |
|success |boolean   |请求结果，true：成功；false：失败  |
|errorCode |string   |错误码  |
|errorMsg |string   |失败原因  |

 **返回示例**

``` 
 {
	“success”：true
 }
```
 **备注** 

- 更多返回错误代码请看首页的异常码描述
