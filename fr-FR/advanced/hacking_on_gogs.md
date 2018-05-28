---
name: Hacker Gogs
sort: 3
---

# Hacker Gogs/Contribuer 

Si vous voulez contribuer à Gogs vous devriez forker le projet et travailler sur la branche `develop`.
Il y a un problème avec Go cependant, l'arborescence inclue l'URL Github officielle du projet. Vous devez alors faire passer votre fork pour le dépôt officiel.

Commencez par télécharger le code source comme vous le feriez normalement :

    $ go get github.com/gogs/gogs

Faites un fork du projet sur Github et puis aller à la source du répertoire de Gogs :

    $ cd $GOPATH/src/github.com/gogs

Suprimmer le dépôt Gogs et cloner votre fork à sa place :

    $ rm -rf gogs
    $ git clone git@github.com:<USERNAME>/gogs.git gogs

Allez dans le répertoire de Gogs, faites un checkout de la branche `develop` et utilisez `go get` à nouveau pour chercher de nouvelles dépendances:

    $ cd gogs
    $ git checkout develop
    $ go get

C'est tout! Vous êtes prêt à travailler sur Gogs. Testez vos modifications, envoyez-les sur votre dépôt et ouvrez un "pull-request" sur Github.
