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
| workNumber | 是 | String | 员工在贵公司唯一标识（最大长度50） |

**返回参数说明**

| 参数名 | 类型 | 说明 |
| :--- | :--- | :--- |
| contractStatus | 是 | Integer | 电签状态（0：未签，1：已签） |
| signDate | 是 | String | 电签成功时间\(电签状态为已电签返回此参数，yyyy-MM-dd HH：mm：ss) |
| contractPath | 是 | String | 电签合同pdf地址（如果电签状态为已电签返回此地址） |


**返回示例**

```
 {
    “success”：true//签署成功
    “msg”：“签署成功”  
    “data” ：{
    “contractStatus”：1，//已签
    “signDate”：“2019-07-18 15：36：05”
      “contractPath ”: “http://gongmall-file.oss-cn-hangzhou.aliyuncs.com/gmmanager-test/电签合同.pdf?” //合同模版地址
    }
 }
```

**备注**

* 更多返回错误代码请看首页的异常码描述



