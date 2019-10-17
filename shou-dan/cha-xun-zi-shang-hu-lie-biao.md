### 查询子商户列表

---

**简要描述：**

* B端商户平台查询该企业在工猫平台注册的子商户

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
| merchants | json | 子商户列表 |





**返回示例**

{

“total”：100，

“totalPage”：10，

“pageSize” ：10，

"currentPage"：1，

“occurMonth”：2018-07，

“list”：{

“merchantId”: ”12304” ,//子商户Id

“merchantName”: ”子商户名称” //子商户名称

“registerStatus”：“18500615259”，//审核状态

“employeeName”：“王鑫鑫”，//姓名

“amount”：“1000”//提现金额

“idNumber”：“620902198909280125”,//身份证号

“salaryAccount”：“6214830100799682”//银行卡号

“dateTime”：“2016-01-25 13:25:56”//申请时间

“payDate”：“2016-01-25 13:25:56”//实际付款时间

}

}

**备注**

* 更多返回错误代码请看首页的异常码描述



