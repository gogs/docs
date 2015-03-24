---
name: 迁移仓库
sort: 3
---

# 迁移外部仓库

Gogs 支持从外部 Git 托管源导入功能来帮助您通过 HTTP/HTTPS 协议迁移仓库，并为您提供了两种方法：通过 Web 节目迁移，或通过可脚本化的 API 迁移。

## 通过 Web 界面迁移

通过 URL 为 `/repo/migrate` 的界面，您可以输入远程 Git 仓库的 HTTP/HTTPS URL，以及必要的认证信息。在表单的下半部分，您可以像创建仓库一样输入仓库的基本信息。

示例：

![](/docs/images/migrate_repo.png)

## 通过 API 迁移

如果您需要从单个或多个源迁移许多仓库，Gogs 提供了可脚本化的迁移 API 来帮助您自定义迁移过程。

- **请求地址**: `/api/v1/repos/migrate`
- **请求方法**: `POST`
- **请求参数**:

|参数名称|是否必须|备注|
|---------|--------|----|
|`username`|**是**|操作者用户名|
|`password`|**是**|操作者密码|
|`clone_addr`|**是**|克隆地址（HTTP/HTTPS URL 或本地路径）|
|`auth_username`|否|授权认证用户名|
|`auth_password`|否|授权认证密码|
|`uid`|**是**|仓库拥有者 ID|
|`repo_name`|**是**|仓库名称|
|`mirror`|否|值为 `on` 时表示该仓库为镜像|
|`private`|否|值为 `on` 时表示该仓库为私有|
|`description`|否|仓库描述|

- **响应结果**:
	- 迁移成功（200）:
	- 迁移失败:

	```json
	{
		"message": <错误信息>
	}
	```

目前已经有一些第三方的迁移脚本：

- [gogs-migrate](https://github.com/valeriangalliat/gogs-migrate)
- [BitBucket to Gogs Migration Script](https://github.com/girvo/bitbucket-to-gogs-migrator)