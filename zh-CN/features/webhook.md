---
name: Web 钩子
sort: 0
---

# Web 钩子

Gogs 支持针对仓库事件的 Web 钩子服务，您可以在仓库的设置相关页面中找到（`/:username/:reponame/settings/hooks`）。所有的事件推送均为 POST 请求，目前支持 Gogs 和 Slack 两种格式的内容。

### 设置参数

- 参数 `Payload URL` 表示事件信息推送的 URL 地址。
- 参数 `Secret` 可让您对事件推送者进行身份验证。
- 目前仅支持仓库 `git push` 事件的钩子。
- 参数 `Active` 表示您当前是否希望激活该钩子。

### 事件信息

以下为 Gogs 向 Payload URL 发送的事件信息示例：

```
{
    "secret": "",
    "ref": "refs/heads/master",
    "commits": [
        {
            "id": "5f69e7cedd45fcce5ea8f3116e9e20f15e90dafb",
            "message": "hi\n",
            "url": "http://localhost:3000/unknwon/macaron/commit/5f69e7cedd45fcce5ea8f3116e9e20f15e90dafb",
            "author": {
                "name": "Unknwon",
                "email": "joe2010xtmf@163.com",
                "username": "Unknwon"
            }
        }
    ],
    "repository": {
        "id": 1,
        "name": "macaron",
        "url": "http://localhost:3000/unknwon/macaron",
        "description": "",
        "website": "",
        "watchers": 1,
        "owner": {
            "name": "Unknwon",
            "email": "joe2010xtmf@163.com",
            "username": "Unknwon"
        },
        "private": false
    },
    "pusher": {
        "name": "Unknwon",
        "email": "joe2010xtmf@163.com",
        "username": "unknwon"
    },
    "before": "f22f45d79a2ff050f0250a7df41f4944e6591853",
    "after": "5f69e7cedd45fcce5ea8f3116e9e20f15e90dafb",
    "compare_url": "http://localhost:3000/unknwon/macaron/compare/f22f45d79a2ff050f0250a7df41f4944e6591853...5f69e7cedd45fcce5ea8f3116e9e20f15e90dafb"
}
```