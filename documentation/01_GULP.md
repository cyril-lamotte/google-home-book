
# Workflow

`gulp` permet d'automatiser et de lancer des tâches :

- Compilation du CSS
- Compression d'images
- Inclusion de fichier HTML
- Déploiement sur FTP
- Génération d'archive


# Installation de NodeJS & gulp

1. Nécessite `nodejs` installé (https://nodejs.org/en/)
2. Nécessite `gulp` installé globalement avec `npm install --global gulp`
3. Lancer la commande `npm install` à partir de la racine du thème pour
   installer les dépendances


## Versions

NodeJS       : x.x.x
Gulp         : 3.9.1
node-modules : Voir package.json


# Lancement du task runner.

1. Lancer la commande `gulp` à partir de la racine du thème/maquette
(voir gulpfile.js)


## Commandes

`gulp`         : Lancer l'écoute des répertoires et les compilations.
`gulp clean`   : Supprimer les fichiers générés automatiquement.
`gulp archive` : Générer une archive zip du répertoire.

> `project.namespace` doit être modifié pour générer une archive avec le nom du projet.


`gulp deploy`  : Déployer les sources par FTP (configuration dans le gulpfile).

- `project.ftpPath` indique le chemin sur le serveur pour le déploiement par FTP.
- Il faut également indiquer les informations de connexion au serveur dans la
  tâche `deploy` (host, user, password).


## Tests de régressions visuelles

La configuration de l'outil est dans `backstop.json`.

`gulp bs_ref`     : Créer un jeu de référence.
`gulp bs_test`    : Comparer avec la référence.
`gulp bs_approve` : Le dernier test devient la référence.


## Génération des images sprites

Afin de réduire les échanges avec le serveur et d'optimiser les performances,
les images sont combinées dans un "sprite".

Toutes les images insérées dans `sources/img-sprites` sont compilées et
compressées en une seul image `sprites.png`.


> Le fichier abstract/variables/sprites.scss est généré automatiquement par le
  module `spritesmith` (ne pas l'éditer).


