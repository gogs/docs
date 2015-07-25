---
name: Hacking sur Gogs
sort: 3
---

# Hacking sur Gogs/Contribuer à Gogs

Si vous voulez contribuer à Gogs vous devriez forker le projet et travailler sur la branche dev.
Il y a un hic cependant; certains paquets internes sont référencés par leur url Github. Alors
vous devez tromper l'outil afin de faire croire que vous travaillez sur un clone du dépôt officiel.

Commencez par télécharger le code source comme vous le feriez normalement :

    $ go get github.com/gogits/gogs

Désormais votre fork le projet sur Github et puis aller à la source du répertoire parent de Gogs :

    $ cd $GOPATH/src/github.com/gogits

Suprimmer le dépôt Gogs et cloner votre fork à sa place :

    $ rm -rf gogs
    $ git clone git@github.com:<USERNAME>/gogs.git gogs

Allez dans le répertoire de Gogs, checkout de la branche dev et utiliser `go get` à nouveau pour chercher de nouvelles dépendances:

    $ cd gogs
    $ git checkout develop
    $ go get

C'est tout! Vous êtes prêt à bidouiller sur Gogs. Testez vos modifications, envoyer-les à votre dépôt et ouvrez une demande.
