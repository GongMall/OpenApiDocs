\# 代发薪接口文档  

  

用于第三方调用工猫发薪接口

  

  

\# 工资单上报接口  

  

\#\#  请求地址  

  

- /\[api/salary/payrollReport\]\(t\]\(https://contract-qa.gongmall.com/api/salary/payrollReport\)  



  



\#\#  公共参数  

  

\|参数名\|类型  \|长度  \|必选  \|描述 \|

\|----------\|--\|--\|--\|--\|

\|appKey    \|string \| 是 \|  \| 开发者唯一标识 \|

\|nonce     \|string \| 是 \| 不大于32位 \| 随机数，请每次随机产生，保证随机数不可预测 \|

\|timestamp \|string \| 是 \|  \| 当前毫秒时间戳 \|

\|sign      \|string \|  是\|  见备注  \|签名 \|



\#\# 请求参数  

  

\|参数     \| 类型 \|必选 \| 说明  \|

\|---------\|------\|-----\|-------\|

\|batchno    \|String\|y    \| 批次号      \| 

\|parameters\| Object\|y    \|  工资单详情     \| 



\#\# parameters

\|参数     \| 类型 \|必选 \| 说明  \|

\|---------\|------\|-----\|-------\|

\|name     \|String\|y    \| 姓名      \|

\|mobile\|String\|y    \|   手机号    \|

\|bankAccount\|String\|y    \|   银行卡    \|   

\|workNumber\|String\|y    \|  员工号     \|

\|amount\|String\|y    \|   提现金额    \|

\|identity\|String\|y    \|  身份证号码     \|

\|dateTime\|String\|y    \|       \|

\|remark\|String\|n    \|   单据描叙    \|



\#请求地址 POST

 

\` 

\` https://contract-qa.gongmall.com/api/salary/payrollReport?appKey=appKey&nonce=nonce&timestamp =ti =timestamp&sign=sign    \`

  

\#\# 返回参数说明  

  



\|参数     \| 类型 \| 说明  \|

\|---------\|------\|-------\|

\|batchno    \|String\|  批次号     \| 

\|successNum \|String\|   成功笔数    \|

\|failNum\|String\|    失败笔数   \|   

\|failDetails\|Object\|    失败详情   \| 



\#\# failDetails

\|参数     \| 类型 \| 说明  \|

\|---------\|------\|-------\|

\|workNumber\|String\|   员工号    \|

\|errormsg\|String\|     错误原因  \|

\|dateTime\|String\|     发薪时间  \|  



\#\# 返回实例  

\` {  

 “success”：true }\` 

 

\#\#  错误码



  - \[错误码链接\]\(接\]\(https://opendoc.gongmall.com/overview/yi-chang-dai-ma.html\)

  

  耿耿:



