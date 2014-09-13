---
name: Webhook
sort: 0
---

# Webhook

Gogs supports web hooks for repository events, you can find it in settings page(`/:username/:reponame/settings/hooks`). All event pushes are POST requests, and we currently support two versions of formats: Gogs and Slack.

### Parameters

- `Payload URL` is the URL address that receives the event push information.
- `Secret` helps your server identify.
- Only support `git push` event hook currently.
- `Active` indicates whether the hook is enabled or not.

### Event information

Following shows an example of event information that will be sent by Gogs to Payload URL:

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