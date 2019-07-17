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
| workNumber | 否 | String | 唯一工号（最大长度50），电签时传入（如果有唯一工号，则传入工号；如果没有唯一工号，可以不传工号） |
| sourceId | 是 | String | 员工唯一标识
| mobile | 是 | String | 手机号（用于收取电签成功之后短信，此参数必填） |
| name | 是 | String | 姓名（如果有唯一工号，使用唯一工号查询状态，此参数可以不填，否则为必填字段） |
| identity | 是 | String | 身份证号（如果有唯一工号，使用唯一工号查询状态，此参数可以不填，否则为必填字段） | 
| idFront | 是 |String | 身份证正面（清晰的身份证正面图片，此参数必填） |
| idBackground | 是 |String | 身份证正面（清晰的身份证正面图片，此参数必填） |
| salaryType | 是 | String | 收款卡类型（0：银行卡，1：支付宝） |
| salaryAccount | 是 | String | 收款卡号（银行卡号和支付宝帐号都可以，根据公司配置进行收集） |
| positionName| 是 | String | 职位名称（公司配置的职位）|

**返回参数说明**

| 参数名 | 类型 | 说明 |
| :--- | :--- | --- |
| sourceId | String | 员工唯一标识 |
| templatePath| String | 合同模版pdf文件地址 |

**返回示例**

```
 {
    “success”：true//员工信息校验通过
    “data” ：{
       “sourceId ”: “123456”，//员工唯一标识
       “templatePath”: “https://contract-qa.gongmall.com/?companyId=DPYWkz&positionId=AVRLeM&channel=kPxJzx” //合同模版地址
    }
 }
```

**备注**

* 更多返回错误代码请看首页的异常码描述



