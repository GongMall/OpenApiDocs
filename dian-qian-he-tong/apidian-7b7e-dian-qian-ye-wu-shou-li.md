**简要描述：**

* 客户接收到意愿认证口令后，在贵司平台输入口令发起签约。返回受理状态。

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
| identity | 是 | String | 证件号码（目前仅支持大陆身份证） |
| captcha | 是 | String | 验证码 |
| extraParam | 否 | String | 附言参数 |

**返回示例**

```
{
    "success": true
  }
```

**返回参数说明**

| 参数名 | 类型 | 说明 |
| :--- | :--- | :--- |
| success | Boolean | 请求结果，true：受理成功；false：受理失败 |
| errorCode | String | 错误码 |
| errorMsg | String | 失败原因 |

**返回错误码说明**

| 错误码 | 失败原因 |
| :--- | :--- |
| GM\_API\_BUS\_000032 | 用户未同步 |
| GM\_API\_BUS\_000033 | 口令错误 |
| GM\_API\_BUS\_000034 | 业务受理失败，请联系技术支持 |



