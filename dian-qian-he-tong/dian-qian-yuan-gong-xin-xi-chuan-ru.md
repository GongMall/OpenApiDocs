### 员工电签信息传入

---

**简要描述：**

* 员工电签信息传入

**请求URL：**

* /api/employee/saveEmployee

**请求方式：**

* POST 

**参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| workNumber | 否 | String | 唯一工号（最大长度50），电签时传入（如果有唯一工号，则可以使用工号查询；如果没有唯一工号，可以不传工号则mobile、name、identity为必填字段，则需要使用mobile、name、identity共同查询，） |
| mobile | 是 | String | 手机号（用于收取电签成功之后短信，此参数必填） |
| name | 是 | String | 姓名（如果有唯一工号，使用唯一工号查询状态，此参数可以不填，否则为必填字段） |
| identity | 是 | String | 身份证号（如果有唯一工号，使用唯一工号查询状态，此参数可以不填，否则为必填字段） | idFront | 是 |String | 身份证正面（清晰的身份证正面图片，此参数必填） |
| idBackground | 是 |String | 身份证正面（清晰的身份证正面图片，此参数必填） |
| salaryType | 是 | String | 收款卡类型（0：银行卡，1：支付宝） |
| salaryAccount | 是 | String | 收款卡号（银行卡号和支付宝帐号都可以，根据公司配置进行收集） |
| positionId | 是 | String | 职位id（公司配置的职位）|

**返回参数说明**

| 参数名 | 类型 | 说明 |
| :--- | :--- | --- |
| templatePath| String | 合同模版pf文件地址 |

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
    }

 }
```

**备注**

* 更多返回错误代码请看首页的异常码描述



