### 取消发薪

---

**简要描述：**

* 接入方取消当前批次的发薪流程。

**请求URL：**

* /api/bulkPayroll/cancelPayOrder

**请求方式：**

* POST 

**请求参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| batchNum | 是 | string | 批次号\(唯一\) |

**返回参数说明：**

| 参数名 | 类型 | 说明 |
| :--- | :--- | :--- |
| suceess | boolean | true：调用成功，false：调用失败 |

**返回参数格式示例**

```json
{
    "success": true
}
```

**备注**

* 仅支持按批次取消。取消后，整批作废（数据生命周期截至）。再次发起时，请更换批次号。一旦调用，整批撤销，请谨慎操作。

* 状态为“支付中”、“支付成功”、“已取消”的批次，不可取消。



