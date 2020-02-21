### 查询电签结果

---

**简要描述：**

* 查询员工电签状态

* 查询电签合同地址：1、由于电子合同特性，电签成功后，当天不能使用该地址查看，               需待第二天才能查看
  2、该地址有效期为：1小时，1小时后，该地址失效，需重新生成。


**请求URL：**

* /api/employee/getContractStatus

**请求方式：**

* POST 

**参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| workNumber | 否 | string | 唯一工号（最大长度50），电签时传入（如果有唯一工号，则可以使用工号查询；如果没有唯一工号，可以不传工号则mobile、name、identity为必填字段，则需要使用mobile、name、identity共同查询，） |
| mobile | 否 | string | 手机号（如果有唯一工号，使用唯一工号查询状态，此参数可以不填，否则为必填字段） |
| name | 否 | string | 姓名（如果有唯一工号，使用唯一工号查询状态，此参数可以不填，否则为必填字段） |
| identity | 否 | string | 身份证号（如果有唯一工号，使用唯一工号查询状态，此参数可以不填，否则为必填字段） |

**返回参数说明**

| 参数名 | 类型 | 说明 |
| :--- | :--- | --- |
| mobile | String | 手机号 |
| name | string | 姓名 |
| identity | string | 身份证号 |
| workNumber | string | 工号 |
| bankAccount | string | 提现收款账号 |
| bankName | string | 账号名称 |
| status | string | 电签状态（0、未签  1、已签） |
| filePath | string | 合同地址 （一小时内有效，超过一小时，重新生成）|
**返回示例**

```
 {
    “success”：true//已电签
    “data” ：{
      “mobile”: “15246265523”, //手机号
      “name”:“张三”,//姓名
      “identity” :“412387199712071245” //身份证号
      “workNumber” : “1112121212” //工号
      “bankAccount”：“622848xxx”//提现收款账号
      “bankName”：“xxx银行”//账号名称
      “status”:“1”//电签状态（1：已签  0：未签）
      “filePath”:“httpXXXX”//合同查看地址
    }

 }
```

**备注**

* 更多返回错误代码请看首页的异常码描述



