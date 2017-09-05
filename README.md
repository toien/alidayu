# alidayu
阿里大鱼短信接口，python3 版本

# 用法
与 TOP（淘宝开放平台）提供的 SDK 用法差不多，实现代码大幅简化，只支持 python3。


```python
# encoding: utf-8
from alidayu import AlibabaAliqinFcSmsNumSendRequest

# 其中 appkey 和 secret 是必须的参数
# url 可选，默认为沙箱的URL，正式应用请传入 http://gw.api.taobao.com/router/rest
# partner_id 为可选，其值为下载的 TOP SDK 中的top/api/base.py 里的 SYSTEM_GENERATE_VERSION
req = AlibabaAliqinFcSmsNumSendRequest(appkey, secret, url, partner_id)

req.extend = "123456"                  # 默认扩展参数，回调时透传给我们
req.sms_type = "normal"                # 短信类型：正常
req.sms_free_sign_name = "a"           # 必须在平台内审核通过的签名，否则可能发送成功但是手机收不到
req.sms_param = json.dumps(params)     # 填充模版的参数
req.rec_num = "13000000000"            # 手机号，多个可用逗号分隔
req.sms_template_code = "SMS_5410290"  # 模版 ID
try:
    resp= req.get_response()
    print(resp)
except Exception as e:
    print(e)
```


# 依赖
需要 requests
