### 生成合同

---

**简要描述：**

* 生成合同

**请求URL：**

* /api/employee/createContract

**请求方式：**

* POST 

**参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| workNumber | 否 | String | 员工在贵公司唯一标识（最大长度50） |
| mobile | 是 | String | 手机号（用于收取电签成功之后短信，此参数必填）（最大长度50） |
| name | 是 | String | 姓名（员工姓名，最大长度50） |
| identity | 是 | String | 身份证号（最大长度50） |
| idFront | 是 | String | 身份证正面地址（地址必须可访问，此参数必填） |
| idBackground | 是 | String | 身份证正面地址（地址必须可访问，此参数必填，此参数必填） |
| salaryType | 是 | Integer | 收款卡类型（0：银行卡，1：支付宝，最大长度4 ） |
| salaryAccount | 是 | String | 收款卡号（银行卡号和支付宝帐号都可以，根据公司配置进行收集，最大长度50） |
| positionName | 是 | String | 职位名称（必须为贵公司配置的工猫平台的职位，最大长度50） |

**返回参数说明**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| workNumber | 是 | String | 员工在贵公司唯一标识 |
| mobile | 是 | String | 手机号（用于收取电签成功之后短信，此参数必填）（最大长度50） |
| name | 是 | String | 姓名（员工姓名） |
| identity | 是 | String | 身份证号（最大长度50） |
| contractStatus | 否 | Integer | 电签状态（0：未签，1：已签）（最大长度4） |
| signDate | 否 | String | 电签成功时间\(电签状态为已电签返回此参数，yyyy-MM-dd HH：mm：ss) |
| contractPath | 否 | String | 电签合同pdf地址（如果电签状态为已电签返回此地址） |
| templatePath | 是 | String | 合同模版pdf文件地址（如果电签状态为未电签返回此地址） |

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



