# 配置文件
```
[
    {
        "UserName": "",
        "Password": "",
        "RefreshToken": "",
        "SubPath": "/CTCloud",
        "RootPathId": "-11", # Default Root: -11
        "HideItemId": "Num01|Num02",
        "RefreshURL": 1800, # Max: 1800; Allow Max: 2329
        "RefreshInterval": 900, # Max: Null, Global
    }
]
```

# 刷新策略
```
Cookie(保活): 60 * 60 * 24 * 5
Cookie(授权): 60 * 30
URL(下载链接): 60 * 30 （配置文件可改）
Folder(刷新目录): 60 * 15  （配置文件可改）
```
