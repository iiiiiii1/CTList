# 配置文件
#### 无特殊需要,只需要填写账号密码即可.
#### `CaptchaMode` 可填写为 `"https://api.moeclub.org/SampleCode"` 用于识别登陆验证码. 默认: "0"。
```
[
    {
        "Enable": 1,                                    # 0: Disable, 1: Enbale.
        "UserName": "",                                 # Input Phone Number.
        "Password": "",                                 # Input Password.
        "CaptchaMode": "0",                             # Captcha Mode. 0: Auto Reject, 1: Manual Input, other: API URL. 
        "RefreshToken": "",                             # Token, Not modify.
        "SubPath": "/CTCloud",                          # Index Path 
        "RootPathId": "-11",                            # Default Root: -11
        "HideItemId": "0|-16",                    # Allow Folder and File.
        "RefreshURL": 1800,                             # Max: 1800; Allow Max: 2329
        "RefreshInterval": 900,                         # Max: Null, Min Global Value
    }
]
```

# 刷新策略
```
Token(保活): 60 * 60 * 24 * 1
Cookie(授权): 60 * 30
URL(下载链接): 60 * 30 （配置文件可改 <RefreshURL>）
Folder(刷新目录): 60 * 15  （配置文件可改, 全局最小值生效 <RefreshInterval>）
```

# 天翼云网盘登陆验证码识别API(基于开源OCR识别)
```
# 目前去噪算法只支持天翼云网盘登陆的验证码(其他类型根本识别不出来)
# 使用时可多次尝试下载不同的验证图片进行提交(目前准确率不算高,但可用.)
# 下载天翼云验证码需要添加请求头 "Referer: https://open.e.189.cn/"

# 接口: https://api.moeclub.org/SampleCode
# 方式: POST
# 参数: Base64=<IMAGE_BASE64_CODE>&Type=CTCloud
# 返回: 状态码:200, 显示识别结果. 状态码:404, 识别错误或结果不符合预设规则, 显示为空.
```

# 使用说明
```
Usage of CTList:
  -bind string
        Bind Address (default "127.0.0.1")
  -port string
        Port (default "5189")
  -a string
        Auth Token.
  -c string
        Config file. (default "config.json")
  -t string
        Index file. (default "index.html")
  -json
        Output json.
```

# 使用示例
```
# 默认启动监听 127.0.0.1, 一般用于反代.
# ./CTList -a "<TOKEN>"
# 
# ./CTList -a "<TOKEN>" -bind 0.0.0.0 -port 80

```
