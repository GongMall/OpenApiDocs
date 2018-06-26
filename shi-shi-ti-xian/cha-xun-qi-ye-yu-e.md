### 查询企业当前余额

---

**简要描述：**

* 查询企业当前余额

**请求URL：**

* `/api/company/getBalance`

**请求方式：**

* POST 

**参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |


**返回参数说明**

| 参数名 | 类型 | 说明 |
| :--- | :--- | --- |
| name | String | 公司名称 |
| amount | BigDecimal | 总金额 |
| availableAmount | BigDecimal | 可用金额 |

**返回示例**

```
 {
    “success”：true，
     “data” ：{
          “name”: ”浙江**科技网络有限公司”, //企业名称 
          “amount”：“100020.36”,//总金额
          “availableAmount” : ”100011.23” //可用余额
    }
 }
```

**备注**

* 更多返回错误代码请看首页的异常码描述



