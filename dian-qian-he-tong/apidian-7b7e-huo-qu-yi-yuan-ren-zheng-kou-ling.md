**简要描述：**

* 获取电签意愿认证唯一口令。
* **如果公司已配置不需要意愿认证，不调用此接口。**

**正式环境请求URL：**

* `/api/employee/sendContractSms`

**测试环境请求URL：**

* `/api/employee/sendContractSms`

**请求方式：**

* POST

**参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | :--- |
| name | 是 | String | 姓名 |
| mobile | 是 | String | 手机号 |
| identity | 是 | String | 证件号码（目前仅支持大陆身份证） |
| extraParam | 否 | String | 附言参数 |

**返回示例**

```
 {
    "success": true,
    "data":1
  }
```

**返回参数说明**

| 参数名 | 类型 | 说明 |
| :--- | :--- | :--- |
| success | Boolean | 请求结果，true：成功；false：失败 |
| data | Integer | 合同状态，0：未签；1：已签 |
| errorCode | String | 错误码 |
| errorMsg | String | 失败原因 |

**返回错误码说明**

| 错误码 | 失败原因 |
| :--- | :--- |
| GM\_API\_BUS\_000031 | 操作频繁，请明日再试 |
| GM\_API\_BUS\_000038 | 口令发送失败，请联系技术支持 |
| GM\_API\_BUS\_000032 | 用户未同步 |



