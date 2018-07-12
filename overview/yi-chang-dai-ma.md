### 异常码

- 通用异常

|异常码|异常说明|
|:----    |:-------    |
|	CO_MSG_000001  | 输入参数格式不正确    |
|	CO_MSG_000002  |  数据操作失败   |
|	CO_MSG_000003  |  服务器中断，请联系客服   |
|	CO_MSG_000004  |  appKey不存在   |
|	CO_MSG_000005  |  签名错误   |
|	CO_MSG_000006  |  请求已过期   |
|	CO_MSG_000007  |  调用频率超限   |
|	CO_MSG_000008  |  appKey已经失效   |
|	CO_MSG_0000011 |  token失效，请重新登录   |
|	CO_MSG_0000012  |  提现消息回调失败   |
|	CO_MSG_0000015  |  不支持的请求媒体类型[%1$s],请选择支持的请求媒体类型[%2$s]   |
|	CO_MSG_0000016  |  不支持的请求类型[%1$s],请选择支持的请求类型[%2$s]   |
|	CO_MSG_0000017  |  ip地址非法   |


-  业务异常

|异常码|异常说明|
|:----    |:-------    |
|	GM_API_BUS_000001  |   非法的提现金额  |
|	GM_API_BUS_000002  |  手机号码不正确   |
|	GM_API_BUS_000003  |   姓名不正确  |
|	GM_API_BUS_000004  |  员工未签约   |
|	GM_API_BUS_000005  |   请求标识为空  |
|	GM_API_BUS_000006  |   公司账户余额不足  |
|	GM_API_BUS_000007  |  客户请求标识已过期   |
|	GM_API_BUS_000008  |  身份证号码有误   |
|	GM_API_BUS_000009  |   所提供的的原始卡号与系统中的不匹配，请核对后重试  |
|	GM_API_BUS_0000010  |  申请时间为空   |
|	GM_API_BUS_0000011  |   银行卡号有误  |
|	GM_API_BUS_0000012  |   变更银行卡实名认证未通过，请核对后重试  |
|	GM_API_BUS_0000013  |   请求银行卡归属地查询接口出错  |
|	GM_API_BUS_0000014  |   公司虚拟帐户未开通，请核对平台后重试 |
|	GM_API_BUS_0000015  |   requestId重复，请确认后重试  |