### 查询已电签员工银行卡

---

**简要描述：**

* 客户已电签成功后，查询该客户在工猫使用过的所有银行卡（该卡三要素验证正常）

**请求URL：**

* /api/employee/getBankAccount

**请求方式：**

* POST 

**参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| name | 是 | string | 姓名 |
| identity | 是 | string | 身份证号 |

**返回参数说明**

| 参数名 | 类型 | 说明 |
| :--- | :--- | --- |
| name | string | 姓名 |
| identity | string | 身份证号 |
| bankAccountList| json| 使用过的三要素验证通过的银行卡 |

**bankAccountList说明**

| 参数名 | 类型 | 说明 |
| :--- | :--- | --- |
| salaryType| string | 账号类型（0：银行卡 ：支付宝） |
| bankAccount| string | 账号（银行卡号或者支付宝账号） |
| bankName | string | 银行卡名称|

**返回示例**

```
 {
    “success”：true//查询成功
       “data” ：{
          “name”:“张三”//姓名
           “identity” :“412387199712071245” //身份证号
           “bankAccountList”：[{
 		   “salaryType”: 0 //0：银行卡  1：支付宝
  		   “bankAccount”：“5479146548985”//银行卡号
  		   “bankName”：“XX银行”//银行名称
	    } ]    
	 }
 } 

```

**备注**

* 更多返回错误代码请看首页的异常码描述



