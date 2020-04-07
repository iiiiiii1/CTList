# CTList介绍
- 支持多账户
- 支持每天自动签到
- 支持异步缓存
- 支持隐藏指定文件夹和文件
- 支持自定义根目录

# 配置文件
#### 无特殊需要,只需要填写账号密码即可 (前4项). 
#### `CaptchaMode` 可填写为 `"https://api.moeclub.org/SampleCode"` 用于识别登陆验证码. 默认: "0"。
```
[
    {
        "Enable": 1,                                    # 0: Disable, 1: Enbale.
        "UserName": "",                                 # Input Phone Number.
        "Password": "",                                 # Input Password.
        "CaptchaMode": "0",                             # Captcha Mode. 0: Auto Reject, 1: Manual Input, other: API URL. 
        "RefreshToken": "",                             # Token. * Do Not Modify It.
        "SubPath": "/CTCloud",                          # Index Path. * Unique Per Account.
        "RootPathId": "-11",                            # Default Root: -11
        "HideItemId": "0|-16",                          # Allow Folder and File.
        "RefreshURL": 200,                              # Min: 180, Max: 1800; Allow Max: 2329
        "RefreshInterval": 900,                         # Max: Null, Min: 300
    }
]
```

# 准备工作
#### `CTList`皮肤文件与`OneList`皮肤文件完全兼容.
#### 可实现在线浏览图片,在线观看视频等其他功能 [点此前往下载](https://github.com/MoeClub/OneList/tree/master/Rewrite/@Theme)
- 授权码
- 主程序 (CTList)
- 配置文件 (config.json)
- 皮肤文件 (index.html)


# 刷新策略
```
Token(保活): 60 * 60 * 12
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
# ./CTList -a "<AUTH_TOKEN_32>"
# 直接监听公网.
# ./CTList -a "<AUTH_TOKEN_32>" -bind 0.0.0.0 -port 80
```
