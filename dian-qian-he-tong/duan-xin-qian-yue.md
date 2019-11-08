**简要描述：**

* 同步用户信息到工猫，返回同步状态。

**正式环境请求URL：**

* `/api/employee/syncInfo`

**测试环境请求URL：**

* `/api/employee/syncInfo`

**请求方式：**

* POST

**参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | :--- |
| name | 是 | String | 姓名 |
| mobile | 是 | String | 手机号 |
| workNumber | 否 | String | 工号 |
| certificateType | 是 | Integer | 证件类型（1:身份证 2:护照 3:军官证 4:港澳台身份证）目前仅支持身份证 |
| identity | 是 | String | 证件号码（目前仅支持大陆身份证） |
| salaryType | 否 | Integer | 工资卡类型（0:银行借记卡 1:支付宝） |
| salaryAccount | 否 | String | 工资卡账号 |

**返回示例**

```

```

**返回参数说明**

| 参数名 | 类型 | 说明 |
| :--- | :--- | :--- |
| success | Boolean | 请求结果，true：同步成功；false：同步失败 |
| errorCode | String | 错误码 |
| errorMsg | String | 失败原因 |

**返回错误码说明**

| 错误码 | 失败原因 |
| :--- | :--- |
| GM\_API\_BUS\_000024 | 实名不通过 |
| GM\_API\_BUS\_000025 | 三要素验证不通过 |
| GM\_API\_BUS\_000027 | 双方约定参数缺失，根据贵司个性化配置决定 |
| GM\_API\_BUS\_000030 | 数据同步失败，请联系技术支持 |
| GM\_API\_BUS\_000035 | 身份证图片附件缺失 |
| GM\_API\_BUS\_000039 | 提供的账号类型与约定账号类型不匹配 |







