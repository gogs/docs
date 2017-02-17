---
name: Web 钩子
---

# Web 钩子

Gogs 支持针对仓库事件的 Web 钩子服务，您可以在仓库的设置相关页面中找到（`/:username/:reponame/settings/hooks`）。所有的事件推送均为 POST 请求，目前支持 Gogs 和 Slack 两种格式的内容。

### 事件信息

以下为 Gogs 向 Payload URL 发送的事件信息示例：

```json
{
  "secret": "",
  "ref": "refs/heads/develop",
  "before": "47df562ceddfaab3471e635e59039c03f47808e2",
  "after": "2cee0f84c0c62fa85382258705353c7d24eb7fee",
  "compare_url": "https://try.gogs.io/gogs/gogs/compare/47df562ceddfaab3471e635e59039c03f47808e2...2cee0f84c0c62fa85382258705353c7d24eb7fee",
  "commits": [
    {
      "id": "2cee0f84c0c62fa85382258705353c7d24eb7fee",
      "message": "Revert \"fix CI...\"\n\nThis reverts commit 94b2816446d1d700d1af0ec166e63375da6612f3.\n",
      "url": "https://try.gogs.io/gogs/gogs/commit/2cee0f84c0c62fa85382258705353c7d24eb7fee",
      "author": {
        "name": "Unknwon",
        "email": "u@gogs.io",
        "username": "unknwon"
      }
    },
    {
      "id": "94b2816446d1d700d1af0ec166e63375da6612f3",
      "message": "fix CI...\n",
      "url": "https://try.gogs.io/gogs/gogs/commit/94b2816446d1d700d1af0ec166e63375da6612f3",
      "author": {
        "name": "Unknwon",
        "email": "u@gogs.io",
        "username": "unknwon"
      }
    },
    {
      "id": "8411b50f5d4e3b30d7d601612ee2aa5e4921c968",
      "message": "work on #1882\n",
      "url": "https://try.gogs.io/gogs/gogs/commit/8411b50f5d4e3b30d7d601612ee2aa5e4921c968",
      "author": {
        "name": "Unknwon",
        "email": "u@gogs.io",
        "username": "unknwon"
      }
    },
    {
      "id": "8a87bee4346968e280e9b9a6e56373c1d2e1c357",
      "message": "what's wrong with go tip?\n",
      "url": "https://try.gogs.io/gogs/gogs/commit/8a87bee4346968e280e9b9a6e56373c1d2e1c357",
      "author": {
        "name": "Unknwon",
        "email": "u@gogs.io",
        "username": "unknwon"
      }
    },
    {
      "id": "1dfa693a5cd221fa43f10df3a9dc216753f82547",
      "message": "fix CI!!\n",
      "url": "https://try.gogs.io/gogs/gogs/commit/1dfa693a5cd221fa43f10df3a9dc216753f82547",
      "author": {
        "name": "Unknwon",
        "email": "u@gogs.io",
        "username": "unknwon"
      }
    }
  ],
  "repository": {
    "id": 140,
    "name": "gogs",
    "url": "https://try.gogs.io/gogs/gogs",
    "description": "Gogs is a painless self-hosted Git Service written in Go.",
    "website": "",
    "watchers": 6,
    "owner": {
      "name": "gogs",
      "email": "u@gogs.io",
      "username": "gogs"
    },
    "private": false
  },
  "pusher": {
    "name": "unknwon",
    "email": "u@gogs.io",
    "username": "unknwon"
  },
  "sender": {
    "login": "unknwon",
    "id": 1,
    "avatar_url": "https://try.gogs.io///1.gravatar.com/avatar/d8b2871cdac01b57bbda23716cc03b96"
  }
}
```
