### 查询子商户列表

---

**简要描述：**

* B端商户平台查询该企业在工猫平台注册成功的子商户

**请求URL：**

* /api/instant/trade

**请求方式：**

* POST

**参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | :--- |
| merchantName | 否 | string | 根据子商户名称模糊查询 |
| pageSize | 否 | int | 每页显示数（默认值为10） |
| currentPage | 否 | int | 当前页数（默认为1） |

**返回参数说明**

| 参数名 | 类型 | 说明 |
| :--- | :--- | :--- |
| total | int | 总数 |
| totalPage | int | 总页数 |
| pageSize | int | 每页展示数 |
| currentPage | int | 当前页码 |
| merchants | json（列表） | 子商户列表 |



merchants**参数说明**

| 参数名 | 类型 | 说明 |
| :--- | :--- | :--- |
| merchantId | int | 子商户Id |
| merchantName | int | 子商户名称 |



**返回示例**

{

“total”：100，

“totalPage”：10，

“pageSize” ：10，

"currentPage"：1，

“occurMonth”：2018-07，

“merchants”：{

“merchantId”: ”12304” ,//子商户Id

“merchantName”: ”子商户名称” //子商户名称

}

}

**备注**

* 更多返回错误代码请看首页的异常码描述



