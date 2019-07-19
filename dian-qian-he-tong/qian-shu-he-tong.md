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
| sourceId | 是 | String | 员工唯一标识 |
| positionName | 是 | String | 职位名称（公司配置的职位） |

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



