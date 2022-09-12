# CNAM - PHP - Examen

> Vous devrez envoyer votre rendu, c'est-à-dire une archive ZIP contenant l'ensemble des sources, images et CSS, par email

## Sujet

Vous allez réaliser une application présentant des albums de musique. Les utilisateurs de votre application pourront ajouter un ou plusieurs albums à un panier, pour les commander.

> Votre application s'appuiera sur une base de données MySQL pour la gestion des albums

## Pages attendues

Partie "publique" du site, accessible à tous les utilisateurs :

- Page d'accueil (liste des albums)
- Fiche album
- Voir le panier
- Login

Partie "privée", administration, accessible seulement aux utilisateurs authentifiés :

- Liste des albums enregistrés
- Nouvel album
- Editer un album
- Supprimer un album
- Déconnexion

## Base de données

Votre base de données contiendra 2 tables : `users` et `albums`.

> Vous trouverez un fichier `bdd.sql` contenant le script de création des 2 tables. Vous devez simplement créer votre base de données au préalable

### Structure des tables

#### **users**

| Nom de la colonne | Type    | Commentaire                           |
| ----------------- | ------- | ------------------------------------- |
| id                | INT     | NOT NULL, AUTO_INCREMENT, PRIMARY KEY |
| login             | VARCHAR | Taille 255                            |
| pass              | VARCHAR | Taille 255                            |

#### **albums**

| Nom de la colonne | Type    | Commentaire                           |
| ----------------- | ------- | ------------------------------------- |
| id                | INT     | NOT NULL, AUTO_INCREMENT, PRIMARY KEY |
| artist            | VARCHAR | Taille 255                            |
| title             | VARCHAR | Taille 255                            |
| cover             | VARCHAR | Taille 255                            |

> Le champ `cover` de la table `albums` contiendra un lien vers une image, sur internet ([Unsplash](https://source.unsplash.com) par exemple), **pas besoin de faire d'upload**

## Création d'un administrateur dans la table users

Afin de pouvoir se connecter à l'application, vous êtes chargé de créer un administrateur. En réalité, ici, vous n'aurez qu'à créer un utilisateur, unique, qui sera capable de se connecter pour administrer les albums présents en base de données.

Afin de pouvoir utiliser les méthodes `password_hash` pour enregistrer un utilisateur, et `password_verify` pour s'authentifier, vous créerez une page `create_admin.php` qui contiendra un script chargé d'insérer un utilisateur dans la base.

Pour résumer, ce script doit :

- Se connecter à la base de données
- Exécuter une requête `INSERT` dans la table `users` pour insérer un utilisateur unique, dont le mot de passe aura été chiffré avec `password_hash` au préalable

> Vous n'avez donc aucun mécanisme d'inscription à mettre en place. Juste un script statique nommé `create_admin.php`, qui créera, de manière statique, un utilisateur dans la base de données

## Apparence

Votre application présentera un menu, une zone de contenu et un footer.

Dans le menu, on fera apparaître de manière conditionnelle le(s) lien(s) d'administration, selon que l'on est connecté ou non.

Vous êtes complètement libre sur l'apparence de l'application. Si vous le souhaitez, vous pouvez utiliser une librairie externe comme Bootstrap.
