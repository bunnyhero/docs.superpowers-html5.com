# Utiliser la gestion de versions

La [gestion des versions](https://fr.wikipedia.org/wiki/Gestion_de_versions) permet de créer des points de contrôle dans votre projet, de comparer d'anciennes révisions avec de nouvelles ainsi que de sauvegarder votre travail sur un service tel que [GitHub](https://github.com/) ou [Bitbucket](https://bitbucket.org/).

Les projets Superpowers sont bien adaptés pour être utilisés avec un outil de gestion de versions. Bien qu'il n'y ait pas de support intégré pour le moment, des outils existants comme Git ou Mercurial fonctionnent parfaitement.

<div class="note">
  <b>Consultez "Fins de ligne et Git"</b> plus bas si vous rencontrez des problèmes d'édition des scripts avec Git sur Windows.
</div>

## Délai lors des modifications

De façon à minimiser son impact sur les performances, le serveur Superpowers n'écrit pas immédiatement sur le disque tous les changements que vous faites à un projet. L'écriture sur le disque peut avoir un délai allant jusqu'à 60 secondes.

Lorsque vous créez une nouvelle révision pour votre projet, vous pouvez soit attendre 60 secondes, soit arrêter votre serveur afin de vous assurer que tout a été correctement écrit sur le disque (nous ajouterons probablement à terme un bouton pour forcer la sauvegarde sur le disque).

## Fichiers à ne pas versionner

Il y a certains fichiers que vous ne voudrez sans doute pas sauvegarder dans votre dépôt :

  * `internals.json` change tout le temps et peut être reconstruit automatiquement
  * Le répertoire `rooms/` contient votre historique de chat récent
  * `members.json` contient les informations des membres du projet que vous ne voulez pas forcément sauvegarder

Vous pouvez utiliser un fichier `.gitignore` ou `.hgignore` pour les ignorer.

## Fins de ligne et Git

Si vous utilisez Git sur Windows avec l'option `core.autocrlf` configurée à `true`, vous devrez ajouter un fichier `.gitattributes` à la racine de votre dépôt avec le contenu suivant :

```
*.txt text eol=lf
```

Ca empêchera Git de modifier les caractères de fins de ligne automatiquement, ce qui pourrait causer des soucis lors de l'édition de vos scripts.