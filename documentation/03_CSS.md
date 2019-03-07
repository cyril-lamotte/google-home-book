
# Workflow

- Les CSS sont compilées avec le préprocesseur `SASS`.
- Aucun framework n'est utilisé.
- Un controle de code automatique est appliqué (via stylelint). Les règles
  utilisées sont définie dans `.stylelintrc`.


# Conventions de codage

Tableau récaptitulatif :
https://docs.google.com/spreadsheets/d/1T-_NBi1UsvojCWUjcETeurcPOKk6698IEXIdj7zgCeo/edit#gid=1204112438


# SASS

## Architecture

Les mixins/functions/variables sont déclarées dans des fichiers distincts du
code du projet (dans le dossier `abstract`), afin de pouvoir générer, si
nécessaire, plusieurs feuilles de style utilisant les mêmes mixins sans inclures
du code inutilisé.


### Mixins / function / variables

- abstract/                             # Mixins / fonctions / variables.
   |- base/                               # Mixins génériques.
   |
   |- project/                            # Mixins du projet.
   |   |- forms/                            # Champs de formulaires.
   |   |- _mix-blocks.scss                  # Blocs.
   |   |- _mix-contrib.scss                 # Contenu contribué (WYSIWYG).
   |   |- _mix-headings.scss                # Titres
   |   |- _mix-buttons.scss                 # Boutons.
   |   |- _mix-lists.scss                   # Listes.
   |   |- _mix-tables.scss                  # Tableaux.
   |
   |- variables/                          # Variables du projet.
       |- _breakpoints.scss                 # Variables de mise en page.
       |- _colors                           # Définitions des couleurs.
       |- _fonts                            # Définitions des polices.
       |- _sprites                          # Images sprites (généré automatiquement)


### Code CSS

- common/                                 # Styles transverses.
   |- base/                                 # Formulaires, boutons, liens...
   |- components/                           # Composants réutilisables (modales / pager...)
   |- nav/                                  # Header, footer, menu, breadcrumbs...

- critical/                               # Mise en page critique
   |- helpers/                              # Classes générique pour l'alignement, l'affichage...
   |- layout/                               # Architecture des pages
   |- reset/                                # Box sizing, images.

- features/                               # Fonctionnalités spécifiques

- home/                                   # Page spécifique (ex: page d'accueil)


- common.scss              # Styles communs à toutes les pages.
- critical.scss            # Mise en page critique.
- editor.scss              # Style des éditeurs WYSIWYG.
- features.scss            # Styles des autres pages ou blocs.
- home.scss                # Styles spécifiques à la page d'accueil.
- print.scss               # Impression.
__


> critical.css devrait être injectée en style "in-page", afin d'accélérer le
  rendu des pages et les performances.



***


## Méthodologie

`BEM` (http://getbem.com/naming/) est utilisé pour une maintenabilité facilitée.


***


## Outils

### `Normalize.css`

`Normalize.css` est intégré via un plugin postCSS (qui réduit la taille du
code en fonction des navigateurs cibles)


### Grilles

Aucune grille par défaut n'est définie. Les `flexbox`, `grid` ou `float` sont
utilisés.


## Exemples

### A. Je veux habiller une page spécifique non réutilisée (ex: page d'accueil).

- Ajouter le code dans le dossier correspondant `home/` ou autre.
- Créer des fichiers séparés pour chaque zone identifiable de la page.
- Créer des mixins pour les éléments de base réutilisés (voir point B).

> Cloisonner le code d'une page particulière permet de charger la CSS
correspondante uniquement à l'affichage de cette page, ainsi, on gagne en
performance.


### B. Je veux créer un style utilisé plusieurs fois (titre, bouton, liste,
champ de formulaire ou tout élément de base).

- Créer une mixin dans le dossier `abstract/projet` dans le fichier
  correspondant à l'élément à habiller.
- Créer une classe dans `common` qui utilise cette mixin.
- Cette mixin et la classe corresponsante sont utilisables ensuite partout
  (common, features, pages spécifiques).


### C. Je veux habiller une zone apparaissant sur toutes les pages (ex: navigation, footer).

- Ajouter le code dans le dossier `common`.
- Créer des mixins pour les éléments de base réutilisés (voir point B).


### D. Je veux habiller une zone apparaissant sur plusieurs pages

- Ajouter le code dans le dossier `features`.
- Créer des mixins pour les éléments de base réutilisés (voir point B).
