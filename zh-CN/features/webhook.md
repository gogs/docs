---
name: Web 钩子
sort: 0
---

# Web 钩子

Gogs 支持针对仓库事件的 Web 钩子服务，您可以在仓库的设置相关页面中找到（`/:username/:reponame/settings/hooks`）。所有的事件推送均为 POST 请求。

### 设置参数

- 参数 `Payload URL` 表示事件信息推送的 URL 地址。
- 目前仅支持 JSON 格式的事件信息。
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
			"id": "629f7209a26c6879092bddf36a21312d346480ab",
			"message": "new file\n",
			"url": "http://localhost:3000/unknown/gogs/commit/629f7209a26c6879092bddf36a21312d346480ab",
			"author": {
				"name": "Unknown",
				"email": "joe2010xtmf@163.com"
			}
		}
	],
	"repository": {
		"id": 2,
		"name": "gogs",
		"url": "http://localhost:3000/unknown/gogs",
		"description": "Gogs(Go Git Service) is a Self Hosted Git Service in the Go Programming Language.",
		"website": "http://gogs.io",
		"watchers": 0,
		"author": {
			"name": "unknown",
			"email": "joe2010xtmf@163.com"
		},
		"private": false
	},
	"pusher": {
		"name": "unknown",
		"email": "joe2010xtmf@1638.com"
	}
}
```