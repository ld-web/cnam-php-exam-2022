# CNAM - PHP - Examen

> Vous devrez envoyer votre rendu, c'est-à-dire une archive ZIP contenant l'ensemble des sources, images et CSS, par email

## Sujet

Vous allez réaliser une application présentant des albums de musique. Les utilisateurs anonymes, donc non authentifiés, de votre application, pourront ajouter un ou plusieurs albums à un panier, pour les commander.

> Votre application s'appuiera sur une base de données MySQL pour la gestion des albums

## Pages attendues

Partie "publique" du site, accessible à tous les utilisateurs :

- Page d'accueil (liste des albums)
- Fiche album (sur cette page, possibilité d'ajouter l'album au panier)
- Voir le panier
- Login

Partie "privée", administration, accessible seulement aux utilisateurs authentifiés :

- Liste des albums enregistrés (possibilité de supprimer un album depuis cette liste)
- Nouvel album
- Déconnexion

## Base de données

Votre base de données contiendra 2 tables : `users` et `albums`.

> Vous trouverez un fichier `bdd.sql` contenant le script de création des 2 tables. Vous devez simplement créer votre base de données au préalable, puis exécuter ce script SQL pour créer les tables

### Structure des tables

#### **users**

| Nom de la colonne | Type    | Commentaire                           |
| ----------------- | ------- | ------------------------------------- |
| id                | INT     | NOT NULL, AUTO_INCREMENT, PRIMARY KEY |
| login             | VARCHAR | Taille 255                            |
| pass              | VARCHAR | Taille 255                            |

> Vous réaliserez un script de création d'utilisateurs de tests (**fixtures**)

#### **albums**

| Nom de la colonne | Type    | Commentaire                           |
| ----------------- | ------- | ------------------------------------- |
| id                | INT     | NOT NULL, AUTO_INCREMENT, PRIMARY KEY |
| artist            | VARCHAR | Taille 255                            |
| title             | VARCHAR | Taille 255                            |
| cover             | VARCHAR | Taille 255                            |

> Le champ `cover` de la table `albums` contiendra un lien vers une image, sur internet ([Unsplash](https://source.unsplash.com) par exemple), **pas besoin de faire d'upload**

## Apparence

Votre application présentera un menu, une zone de contenu et un footer.

Dans le menu, on fera apparaître de manière conditionnelle les liens d'administration (Nouvel Album, Liste des albums, déconnexion), selon que l'on est connecté ou non.

Vous êtes complètement libre sur l'apparence de l'application. Si vous le souhaitez, vous pouvez utiliser une librairie externe comme Bootstrap.

## Gestion du panier

Quand un utilisateur voudra ajouter un album à son panier, vous utiliserez les **sessions** PHP pour stocker **l'ID** de l'album ajouté.

Ainsi, sur la page "Voir le panier", l'idée sera de faire une requête récupérant tous les albums avec leurs ID.
