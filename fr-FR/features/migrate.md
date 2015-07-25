---
name: Migrez des dépôts
sort: 3
---

# Migrez des dépôts

Pour vous rendre la vie plus facile, Gogs supporte la migration de dépôts provenant d'autres sources d'hébergement Git via HTTP / HTTPS. Pour ce faire, vous avez deux options, soit utiliser l'interface web ou l'API de migration scriptable.

## Migrez en utilisant l'interface web

Dans l'URL `/repo/migrate`, vous pouvez entrer HTTP / HTTPS URL d'un dépôt distant Git, avec l'autorisation en cas de besoin. Dessous de la partie de l'information de la source, vous pouvez entrer les informations du dépôt, comme d'habitude.

Par exemple:

![](/docs/images/migrate_repo.png)

## Migrez en utilisant l'API

Dans le cas où vous avez beaucoup de dépôts qui doivent migrer de même de mettre différentes sources, Gogs a une API de migration scriptable pour vous permettre de personnalisé votre processus de migration.

- **URL**: `/api/v1/repos/migrate`
- **Method**: `POST`
- **Parameters**:

|Paramètre|Requis|Note|
|---------|--------|----|
|`username`|**True**|Nom de l'utilisateur|
|`password`|**True**|Mot de passe de l'utilisateur|
|`clone_addr`|**True**|Addresse du clone (URL HTTP/HTTPS ou chemin locale)|
|`auth_username`|False|Autorisation utilisateur|
|`auth_password`|False|Autorisation mot de passe|
|`uid`|**True**|Identifiant du propriétaire du dépôt|
|`repo_name`|**True**|Nom du dépôt|
|`mirror`|False|Mettre `on` si il est un miroir|
|`private`|False|Mettre `on` si il est priver|
|`description`|False|Description du dépôt|

- **Response**:
	- Success(200):
	- Failure:

	```json
	{
		"message": <error message>
	}
	```

Il y a aussi quelques scripts déjà disponibles :

- [gogs-migrate](https://github.com/valeriangalliat/gogs-migrate)
- [BitBucket to Gogs Migration Script](https://github.com/girvo/bitbucket-to-gogs-migrator)
