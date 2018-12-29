# 根据批次号查询上传工资单信息

---

**简要描述：**  
    客户工资单通过接口传入后，可以使用上传批次号查询工资单处理信息。  
**请求地址**

* /api/payroll/getImportResult   

**请求方式**

* POST

**请求参数**

| 参数 | 类型 | 必选 | 说明 |
| --- | --- | --- | --- |
| batchNum | String | y | 批次号\(最长32 位，全局唯一\) |

** 返回参数**

| 参数 | 类型 | 说明 |
| --- | --- | --- |
| success | boolean | 请求是否成功 |
| data | Object | 返回信息主体 |

** data**

| 参数 | 类型 | 说明 |
| --- | --- | --- |
| batchnum | String | 上传批次号 |
| status | String | 处理状态\(0:系统处理中 1:处理完成\) |
| responseData | Object | 返回详细信息 |

** responseData**

| 参数 | 类型 | 说明 |
| --- | --- | --- |
| requestId | String | 单笔请求标识 |
| status | String | 单笔处理状态\(-1:失败 ，1:成功\) |
| failReason | String | 如果数据验证失败，失败原因 |

** 返回示例**

```
{
"success": true,
"data": {
"batchNum": "20180410044",//批次号
"status": "1"//处理完成时
"responseData": [
{
"requestId": "123456",//单笔请求标识
"status": "1"//成功
},
{
"requestId": "456456",
"status": "-1",//失败
"failReason": "员工未签约"
    }]
  }
}
```



