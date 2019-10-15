### 电签结果回调处理

---

**简要描述：**

* 电子合同回调

**请求URL：**

* `开发者信息提供的电子合同回调地址`

**请求方式：**

* POST 

**参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| name | 是 | string | 姓名 |
| mobile | 是 | string | 手机号 |
| identity | 是 | string | 身份证号码 |
| status | 是 | string | 合同状态（1、未签 2、已签） |
| workNumber | 否 | string | 工号 |
| extraParam | 否 | string | 附言参数，由传入方提供，回调时将原样返还，可以用来做用户数据标识 |
| salaryAccount | 是 | String | 银行卡（对应电签时的bankNum） |
| bankName | 是 | String | 银行名称 |

**返回参数说明**

已成功接收:请返回json格式的任何结果，非空即可.
如接受失败或者其他任何原因导致的回调失败，请不要返回任何结果，包括“error、fail”等，请返回null;

**备注**

* 如需要验签，请参照请求接口规范中的签名方式进行验证



