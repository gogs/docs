---
name: Webhook
sort: 0
---

# Webhook

Gogs supporte webhook pour les mouvements du dépôt, vous pouvez le trouver dans la page des paramètres(`/:username/:reponame/settings/hooks`). Tous les evenements 'pushes' par les requêtes POST, et nous soutenons actuellement deux versions de formats: Gogs et Slack.

### Paramètres

- `Payload URL` est l'adresse URL qui reçoit les informations cas de 'push'.
- `Secret` aide à identifier votre serveur.
- Only support `git push` event hook currently.
- `Active` indique si le hook est activé ou non.

### Information sur les événements

Ci-dessous montre un exemple d'informations sur l'événement qui sera envoyé par Gogs à Payload URL :

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
