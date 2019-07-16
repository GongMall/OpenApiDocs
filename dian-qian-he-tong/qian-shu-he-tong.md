### 签署合同

---

**简要描述：**

* 合同签署

**请求URL：**

* /api/employeeContract/doSign

**请求方式：**

* POST

**参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | :--- |
| mobile | 是 | String | 手机号（用于收取电签成功之后短信，此参数必填） |
| name | 是 | String | 姓名（如果有唯一工号，使用唯一工号查询状态，此参数可以不填，否则为必填字段） |
| identity | 是 | String | 身份证号（如果有唯一工号，使用唯一工号查询状态，此参数可以不填，否则为必填字段） |
| 

**返回参数说明**

| 参数名 | 类型 | 说明 |
| :--- | :--- | :--- |
| templatePath | String | 合同模版pdf文件地址 |

**返回示例**

```
 {
    “success”：true//员工信息校验通过
    “data” ：{
      “templatePath”: “https://contract-qa.gongmall.com/?companyId=DPYWkz
&
positionId=AVRLeM
&
channel=kPxJzx” //合同模版地址
    }
 }
```

**备注**

* 更多返回错误代码请看首页的异常码描述



