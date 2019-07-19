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
| contractPath | String | 签署成功合同pdf文件地址 |

**返回示例**

```
 {
    “success”：true//签署成功
    “data” ：{
      “contractPath ”: “http://gongmall-file.oss-cn-hangzhou.aliyuncs.com/gmmanager-test/电签合同.pdf?” //合同模版地址
    }
 }
```

**备注**

* 更多返回错误代码请看首页的异常码描述



