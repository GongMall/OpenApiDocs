**简要描述：**

* 贵司提交客户合同参数到工猫，工猫将客户合同参数入库后发送短信给客户。如提交相同姓名和身份证在已有合同的情况下，共享一份合同，且合同状态一致。

**正式环境请求URL：**

* `/api/employee/submitContractInfo`

**测试环境请求URL：**

* `/api/employee/submitContractInfo`

**请求方式：**

* POST

**参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | :--- |
| name | 是 | String | 姓名 |
| mobile | 是 | String | 手机号 |
| workNumber | 否 | String | 工号 |
| certificateType | 是 | Integer | 证件类型（1:身份证 2:护照 3:军官证 4:港澳台身份证）目前仅支持身份证 |
| idNumber | 是 | String | 证件号码 |
| salaryType | 否 | Integer | 工资卡类型（0:银行借记卡 1:支付宝） |
| salaryAccount | 否 | String | 工资卡账号 |
| identityFrontFile | 否 | String | 证件正面图片可访问地址（个人信息面） |
| identityBackgroundFile | 否 | String | 证件反面图片可访问地址（国徽面） |
| extraParam | 否 | String | 附言参数 |

**返回示例**

```
 {
    "data": 1,
    "success": true
  }
```

**返回参数说明**

| 参数名 | 类型 | 说明 |
| :--- | :--- | :--- |
| success | Boolean | 请求结果，true：成功；false：失败 |
| data | Integer | 合同状态，0：未签约，1：已签约 |
| errorCode | String | 错误码 |
| errorMsg | String | 失败原因 |

**返回错误码说明**

| 错误码 | 失败原因 |
| :--- | :--- |
| GM\_API\_BUS\_000024 | 实名不通过 |
| GM\_API\_BUS\_000025 | 三要素验证不通过 |
| GM\_API\_BUS\_000026 | 非空参数缺失 |
| GM\_API\_BUS\_000027 | 双方约定参数缺失，根据贵司个性化配置决定 |
| GM\_API\_BUS\_000028 | 图片获取失败 |
| GM\_API\_BUS\_000029 | 图片OCR识别失败，请联系技术支持 |
| GM\_API\_BUS\_000030 | 数据提交发生错误，请联系技术支持 |
| GM\_API\_BUS\_000031 | 短信操作频繁，请明日重试 |
| GM\_API\_BUS\_000035 | 实名认证的用户信息与身份证图片识别信息不符 |
| GM\_API\_BUS\_000036 | 请上传jpg/png图片文件 |
| GM\_API\_BUS\_000037 | 图片文件不能大于3M |

**备注**

* 更多返回错误代码请看首页的错误代码描述



