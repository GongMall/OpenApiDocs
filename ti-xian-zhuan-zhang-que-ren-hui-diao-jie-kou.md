### 提现转账确认回调

---

**简要描述：**

* 用户提交提现请求后，工猫在给用户转账之前，需查询确认客户此笔请求是否有效，当工猫确认此次请求有效再进行转账打款。若为无效数据，则工猫不予打款转账，并通过提现结果回调处理

**请求URL：**

* `开发者信息提供的实时提现结果回调地址`

**请求方式：**

* POST 

**参数：**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| requestId | 是 | string | 客户请求标识，最长32位（用户提现时企业系统自动生成，每个requestId代表一个提现请求，工猫作为每笔提现记录的唯一标识） |
| name | 是 | string | 姓名 |
| mobile | 是 | string | 手机号 |
| amount | 是 | string | 提现金额 |
| identity | 是 | string | 身份证号码 |
| bankAccount | 是 | string | 银行卡 |
| dateTime | 是 | string | 申请时间\(yyyyMMddHHmmss\) |
| remark | 否 | string | 单据描叙 |

**返回参数说明**

| 参数名 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | --- |
| requestId | 是 | string | 客户请求标识，最长32位（用户提现时企业系统自动生成，每个requestId代表一个提现请求，工猫作为每笔提现记录的唯一标识） |
| status | 是 | Integer | 此笔请求是否有效（1：有效  2：无效） |

**返回示例**  
请返回json格式的结果。

```
有效示例：
{
    "requestId": "123",//提现请求标识
    "status": 1  //此笔请求有效，提交银行正常进行转账 
}
无效示例：
{
    "requestId": "123",//提现请求标识
    "status": 2  //此笔请求无效，通过提现结果回调处理，回调提现结果（https://opendoc.gongmall.com/shi-shi-ti-xian/ti-xian-jie-guo-hui-diao.html回调提现结果失败，回调状态status=2）
}
```

**备注**

* 如需要验签，请参照请求接口规范中的签名方式进行验证



