### 上传发薪数据明细

---

**简要描述：**

* 接入方上传工资单发薪数据明细

**请求URL：**

* /api/bulkPayroll/uploadPayroll

**请求方式：**

* POST 

**请求参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| bizContent | 是 | json格式 | 发薪数据信息 |

**业务参数bizContent格式：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| batchNum | 是 | string | 批次号\(唯一\) |
| verifyContract | 是 | integer | 是否电签\(0:不电签，1:电签\) |
| month | 是 | string | 月份\(格式：yyyy-MM\) |
| detailList | 是 | json数组 | 具体发薪数据 |

detailList具体发薪数据参数

| 参数名 | 类型 | 说明 |
| :--- | :--- | --- |
| customerOrderNum | integer | 序列号\(批次内唯一\) |
| idNumber | string | 身份证 |
| name | string | 姓名 |
| mobile | string | 手机 |
| salaryAccount | string | 发薪账号 |
| salaryAmount | string | 发薪金额\(大于0.1\) |
| salaryType | string | 发薪类型\(默认是0，银行卡\) |
| incomeStatement | string | 备注 |

**请求参数bizContent的格式示例**

```json
{
    "batchNum": "0000000000",
    "verifyContract": 0,
    "detailList": [{
        "idNumber": "411421199202264840",
        "incomeStatement": "发薪",
        "mobile": "15280191063",
        "name": "郝琳",
        "salaryAccount": "6235756400000604185",
        "salaryAmount": "0.1",
        "salaryType": "0",
        "customerOrderNum": 1
    }],
    "month": "2019-18"
}
```

**返回参数说明**

| 参数名 | 类型 | 说明 |
| :--- | :--- | --- |
| success | boolean | true：调用成功，false：调用失败 |

**返回示例**

```json
{
    "success": true
}
```

**备注**

* 请确保相关字段的格式正确，如数字、中文字符等
* 入参字段说明中必填字段不能为空。某一行必填信息为空时，该条记录将不会被导入，会记录在导入失败的记录中；
* 批次号为本批次付款数据的唯一标识，全局唯一。商户订单号为每一笔付款数据在贵司的唯一标识，单个批次内不允许重复，主要用于后期对账时确定每一笔付款数据。填写时建议咨询下公司技术部门；
* 应付金额为企业应该发放给相关人员的款项，无需考虑管理费、服务费和增值附加税的金额以及承担方式。我们会根据双方业务合同中的约定计费标准，由系统自动计算得出；
* 企业可以根据自身需要，为每笔付款记录添加备注信息。备注内容将展示在工猫科技发送给相关人员的资金到账通知短信中；
* 须严格使用用户本人的姓名、身份证和收款账号信息，否则会导致用户信息校验失败，无法付款；
* 收入说明，为用户获得该笔收入的来源。如通过在线直播、外卖配送等


