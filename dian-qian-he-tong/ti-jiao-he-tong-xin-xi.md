**简要描述：**

* 根据业务需要进行身份证文件上传

**正式环境请求URL：**

* `/api/attachment/uploadIndentityFile`

**测试环境请求URL：**

* `/api/attachment/uploadIndentityFile`

**请求方式：**

* POST

**参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | :--- |
| name | 是 | String | 姓名 |
| identity | 是 | String | 证件号码（目前仅支持大陆身份证） |
| identityFrontBase64 | 是 | String | 证件正面图片base64（个人信息面） |
| identityBackgroundBase64 | 是 | String | 证件反面图片base64（国徽面） |

**注：图片base64字串原样输出即可，不需要进行任何编码处理。同时支持带data:image/jpeg;base64,等图片相关前缀。**

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
| GM\_API\_BUS\_000024 | 实名不通过 |
| GM\_API\_BUS\_000028 | 实名认证的用户信息与身份证图片识别信息不符 |
| GM\_API\_BUS\_000029 | 图片OCR识别失败，请联系技术支持 |
| GM\_API\_BUS\_000030 | 数据同步失败，请联系技术支持 |
| GM\_API\_BUS\_000036 | 请上传jpg/png图片文件 |
| GM\_API\_BUS\_000037 | 图片文件不能大于3M |



