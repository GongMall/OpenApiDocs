### 分页查询提现记录

---

**简要描述：**

* 客户按月查看自己提现历史记录。

**请求URL：**

* [/api/withdraw/getWithdrawList](https://openApi-qa.gongmall.com/api/withdraw/getWithdrawList)

**请求方式：**

* POST

**参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | :--- |
| name | 是 | string | 员工姓名 |
| mobile | 是 | String | 员工手机号码 |
| identity | 是 | String | 员工身份证号码 |
| occurMonth | 否 | String | 提现月份（yyyy-MM）,若不传，查询月份所有记录 |
| pageSize | 否 | int | 每页显示数（默认值为10） |
| currentPage | 否 | int | 当前页数（默认为1） |

**返回参数说明**

| 参数名 | 类型 | 说明 |
| :--- | :--- | :--- |
| total | int | 提现总数 |
| totalPage | int | 提现记录页数 |
| pageSize | int | 每页展示数 |
| currentPage | int | 当前页码 |
| occurMonth | string | 提现月份 |
| list | List | 提现记录 |

**返回示例**

{

“total”：100，

“totalPage”：10，

“pageSize” ：10，

"currentPage"：1，

“occurMonth”：2018-07，

“list”：{

“requestId”: ”12304” ,//客户请求标识

“status”: 2 ,//失败

“failReason”: ”企业余额不足” //失败原因

“mobile”：“18500615259”，//手机号

“name”：“王鑫鑫”，//姓名

“amount”：“1000”//提现金额

“idNumber”：“620902198909280125”//身份证号

“salaryAccount”：“6214830100799682”//银行卡号

“dateTime”：“20160125132356”//申请时间

“payDate”：“20160125132556”//实际付款时间

}

}

**备注**

* 更多返回错误代码请看首页的异常码描述



