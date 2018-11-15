---
name: Modèle personnalisé
---

# Modèle personnalisé

Il est possible d'inclure votre propre contenu header ou footer dans Gogs sans toucher au code source original. Ceci est utile pour ajouter du code "analytics" ou pour inclure du contenu statique personnalisé.

Pour en savoir plus consultez : [inject custom head and footer](https://discuss.gogs.io/t/how-to-inject-custom-head-and-footer/943).

## Inclure un fichier CSS personnalisé

Voici un exemple pour inclure un fichier CSS personnalisé dans votre instance Gogs. Les noms et répertoires sont arbitraires, ils peuvent être modifiés à votre guise, l'unique restriction étant qu'ils soient accesibles par une requête.

1. Créez un fichier nommé `custom.css` dans le répertoire `public/css`.
2. Placez des règles CSS dans ce fichier.
3. Editez le fichier `custom/templates/inject/head.tmpl` et ajoutez une ligne `<link rel="stylesheet" href="/css/custom.css">`
4. Redémarrer Gogs
5. Ajoutez plus de contenu CSS dans le fichier ne nécessite pas de redémarrer Gogs
