---
name: Web 钩子
---

# Web 钩子

Gogs 支持针对仓库事件的 Web 钩子服务，您可以在仓库的设置相关页面中找到（`/:username/:reponame/settings/hooks`）。所有的事件推送均为 POST 请求，目前支持 Gogs 和 Slack 两种格式的内容。

### 事件信息

以下为 Gogs 向 Payload URL 发送的事件信息示例：


```
X-Gogs-Delivery: f6266f16-1bf3-46a5-9ea4-602e06ead473
X-Gogs-Event: push
X-Gogs-Signature: 1921679ed6274399b6514721056337f6913b6ff1cb35a24d340e983745d637f1
```

```json
{
  "ref": "refs/heads/develop",
  "before": "28e1879d029cb852e4844d9c718537df08844e03",
  "after": "bffeb74224043ba2feb48d137756c8a9331c449a",
  "compare_url": "http://localhost:3000/unknwon/webhooks/compare/28e1879d029cb852e4844d9c718537df08844e03...bffeb74224043ba2feb48d137756c8a9331c449a",
  "commits": [
    {
      "id": "bffeb74224043ba2feb48d137756c8a9331c449a",
      "message": "!@#0^%\u003e\u003e\u003e\u003e\u003c\u003c\u003c\u003c\u003e\u003e\u003e\u003e\n",
      "url": "http://localhost:3000/unknwon/webhooks/commit/bffeb74224043ba2feb48d137756c8a9331c449a",
      "author": {
        "name": "Unknwon",
        "email": "u@gogs.io",
        "username": "unknwon"
      },
      "committer": {
        "name": "Unknwon",
        "email": "u@gogs.io",
        "username": "unknwon"
      },
      "timestamp": "2017-03-13T13:52:11-04:00"
    }
  ],
  "repository": {
    "id": 140,
    "owner": {
      "id": 1,
      "login": "unknwon",
      "full_name": "Unknwon",
      "email": "u@gogs.io",
      "avatar_url": "https://secure.gravatar.com/avatar/d8b2871cdac01b57bbda23716cc03b96",
      "username": "unknwon"
    },
    "name": "webhooks",
    "full_name": "unknwon/webhooks",
    "description": "",
    "private": false,
    "fork": false,
    "html_url": "http://localhost:3000/unknwon/webhooks",
    "ssh_url": "ssh://unknwon@localhost:2222/unknwon/webhooks.git",
    "clone_url": "http://localhost:3000/unknwon/webhooks.git",
    "website": "",
    "stars_count": 0,
    "forks_count": 1,
    "watchers_count": 1,
    "open_issues_count": 7,
    "default_branch": "master",
    "created_at": "2017-02-26T04:29:06-05:00",
    "updated_at": "2017-03-13T13:51:58-04:00"
  },
  "pusher": {
    "id": 1,
    "login": "unknwon",
    "full_name": "Unknwon",
    "email": "u@gogs.io",
    "avatar_url": "https://secure.gravatar.com/avatar/d8b2871cdac01b57bbda23716cc03b96",
    "username": "unknwon"
  },
  "sender": {
    "id": 1,
    "login": "unknwon",
    "full_name": "Unknwon",
    "email": "u@gogs.io",
    "avatar_url": "https://secure.gravatar.com/avatar/d8b2871cdac01b57bbda23716cc03b96",
    "username": "unknwon"
  }
}
```