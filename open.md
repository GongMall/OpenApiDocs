### 合同接入指南
---

**简要描述：** 

- 业务背景
   因业务需求，企业的产品中需嵌入工猫管家电子签约功能，确认C端用户先签约（成为合法兼职员工），形成劳务关系，再提现（发薪）。

**电签功能对接：** 
- 业务对接完成后，需销售主管向工猫总部为该企业开通电签功能。

申请材料包括：
1）企业基本信息
 企业名称，企业简称，合作企业，地址信息（包括省，市，区，详细地址），企业联系人，联系电话，邮箱，税率，管理费
 
2）企业合同模板
 企业按要求填写劳务合同模板条款，交给销售主管，发送至总部邮箱support@gongmall.com申请开通电签功能。
 
  技术人员会根据邮件内容，为新公司上线合同功能做好准备工作，然后回复邮件。
  
**电签传参：**
- 说明
企业可通过将定制链接地址嵌入到产品流程中，打开地址，传入电子签约所需参数，直接进入合同信息采集页面，员工确认无误后，进入下一步，进行合同签署。

**请求地址示例：** 
- 加密前
https://contract-qa.gongmall.com/url_contract.html?companyId=xMEQMG&name=王星星&mobile=15212345678&idNumber=620402198709215456&bankName=招商银行&bankNum=6214830100799652

- 加密后
https://contract-qa.gongmall.com/url_contract.html?companyId=xMEQMG&data=lbrMBX7iME/iutEdBZKq/+dzI6EBnU0WwKQU1r5NEJ42evQt+RuqSa+8rk9BvRuYbT9jWJBQOo3kUw+48+MHVLv3SDWIFEgT6DNhKVQaEwmcOe2rhPtgF4NLALMkoGfoFglg57fJgmnUnLjIoyRGYQ==

- 备注
https://contract-qa.gongmall.com/url_contract.html?companyId=xMEQMG
是我们根据系统生成的公司的唯一请求地址，后面的参数信息需要调用方按名称传给我们，用于生成合同和提现匹配。&之后的参数根据appkey+appSecret组合MD5大写作为秘钥，采用AES加密算法(算法中初始化向量IV采用16位的0)，最后将加密后的字符串作为data的值拼接在url请求到工猫，加密算法请参照不同语言示例