### H5提现信息接入

---

**简要描述：**

·已签约员工在企业客户端发起提现请求，企业将提现信息加密，传给工猫，工猫进行解密，进入提现信息界面进行确认，确认信息无误后，将指定金额转入员工指定的已绑定银行卡。

**请求URL：**

·/api/withdraw/decodeUrl

**请求方式：**

·POST

**参数：**

| **参数名** | **必选** | **类型** | **说明** |
| :--- | :--- | :--- | :--- |
| requestId | 是 | string | 客户请求标识\(流水号\),最长32位 |
| mobile | 是 | string | 银行卡预留手机号 |
| name | 是 | string | 姓名 |
| amount | 是 | BigDecimal | 提现金额 |
| identity | 是 | string | 身份证号码 |
| bankAccount | 是 | string | 银行卡号 |
| dateTime | 是 | string | 申请时间\(yyyyMMddHHmmss\) |
| remark | 否 | string | 单据描叙 |

**请求示例：**

·加密前[https://contract-qa.gongmall.com/url\_contract.html?appKey=14e1bcd1c8a14f70a4c5ce4f1cbe487c&requestId=12304&name=王星星&mobile=15212345678&identity=620402198709215456&amount=100&bankAccount=6214830100799652&dateTime=20180612141054&remark=单据描述](https://contract-qa.gongmall.com/url_contract.html?companyId=xMEQMG&name=王星星&mobile=15212345678&idNumber=620402198709215456&bankName=招商银行&bankNum=6214830100799652)

·加密后[https://contract-qa.gongmall.com/url\_contract.html?appKey=14e1bcd1c8a14f70a4c5ce4f1cbe487c&data= J9h1r4BBIeZCjFbF2vkYU0Mts5TQ+7OgibcyIy27ZY61A/FLJLglcUIZBiLdPi6mEYMA/NrMIflZNhkdk6e5RNwzhVd9JSpZsfgEKX0aDyhZ211R9YkCa4YAj9fTVH9DBTfg+0hA5BlN+41IFwH8XrSZQns/oJKf6mmdRr7wUf5oHlpCwXZ9nDcLtWBFTDC+6e6x/u9x6F1Vw0aCUOMmu5JhHEClN0OO3HMMlOKM3HFt28g2v3lv0niS4RaFWcI4](https://contract-qa.gongmall.com/url_contract.html?companyId=xMEQMG&data=lbrMBX7iME/iutEdBZKq/+dzI6EBnU0WwKQU1r5NEJ42evQt+RuqSa+8rk9BvRuYbT9jWJBQOo3kUw+48+MHVLv3SDWIFEgT6DNhKVQaEwmcOe2rhPtgF4NLALMkoGfoFglg57fJgmnUnLjIoyRGYQ==)

·备注[https://contract-qa.gongmall.com/url\_contract.html?appKey=14e1bcd1c8a14f70a4c5ce4f1cbe487c](https://contract-qa.gongmall.com/url_contract.html?companyId=xMEQMG)是我们根据系统生成的公司的唯一请求地址。&之后的参数根据appkey+appSecret组合MD5大写作为秘钥，采用AES加密算法\(算法中初始化向量IV采用16位的0\)，最后将加密后的字符串作为data的值拼接在url请求到工猫，加密算法请参照不同语言示例

**测试数据：**

\[1\]appkey+appsecret: 14e1bcd1c8a14f70a4c5ce4f1cbe487cc59a1163e3d360a2a0eb442bda42df52  
 \[2\]md5\(32位\): 61CC5DF78D360167F8618237DAF643EA  
 \[3\]待加密内容: requestId=12304&name=王星星&mobile=15212345678& identity =620402198709215456&amount=100&bankAccount= 6214830100799652&dateTime=20180612141054&remark=单据描述\[4\]加密结果：J9h1r4BBIeZCjFbF2vkYU0Mts5TQ+7OgibcyIy27ZY61A/FLJLglcUIZBiLdPi6mEYMA/NrMIflZNhkdk6e5RNwzhVd9JSpZsfgEKX0aDyhZ211R9YkCa4YAj9fTVH9DBTfg+0hA5BlN+41IFwH8XrSZQns/oJKf6mmdRr7wUf5oHlpCwXZ9nDcLtWBFTDC+6e6x/u9x6F1Vw0aCUOMmu5JhHEClN0OO3HMMlOKM3HFt28g2v3lv0niS4RaFWcI4

**加密算法试例（见接入指南）**

**返回示例**

更多返回错误代码请看首页的异常码描述

