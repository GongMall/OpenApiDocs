**简要描述：**

* 客户接收到验证码后，在贵司平台输入验证码完成签约。并请贵司同步保存合同签署完成的状态。

**正式环境请求URL：**

* `/api/employee/signContract`

**测试环境请求URL：**

* `/api/employee/signContract`

**请求方式：**

* POST

**参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | :--- |
| name | 是 | String | 姓名 |
| mobile | 是 | String | 手机号 |
| idNumber | 是 | String | 证件号码 |
| workNumber | 否 | String | 工号 |
| captcha | 是 | String | 验证码 |

**返回示例**

```
{
    "success": true
}
```

**返回参数说明**

| 参数名 | 类型 | 说明 |
| :--- | :--- | :--- |
| success | Boolean | 请求结果，true：成功；false：失败 |
| errorCode | String | 错误码 |
| errorMsg | String | 失败原因 |

**返回错误码说明**

| 错误码 | 失败原因 |
| :--- | :--- |
| GM\_API\_BUS\_000032 | 未提交合同参数 |
| GM\_API\_BUS\_000033 | 验证码错误或已过期 |
| GM\_API\_BUS\_000034 | 合同签约失败 |

**备注**

* 更多返回错误代码请看首页的错误代码描述



