---
title: "Patterns d'accès"
date: 2020-04-08T16:56:34+02:00
---

## Patterns d'accès au données

| | Description |
|-|-----------|
|1|[Récupérer un utilisateur par son email](#get-user-by-email)|
|2|[Récupérer un utilisateur par son ID](#get-user-by-id)|
|3|[Récupérer un événement par son ID](#get-event-by-id)|
|4|[Récupérer tous les événements auxquels participe un utilisateur](#get-events-for-user)|
|5|[Récupérer tous les événements pour un BDE donné](#get-events-for-bde)|
|6|[Récupérer tous les utilisateurs qui participent à un événement](#get-users-for-event)|
|7|[Récupérer tous les utilisateurs pour un BDE donné](#get-users-for-bde)|


## Contexte d'utilisation des patterns d'accès

##### Récupérer un utilisateur par son email 
<a id="get-user-by-email"></a>
Lors de la connexion, l'utilisateur s'indentifiera grâce à son adresse email et son mot de passe.
Lors d'un événement comme le Gala, afin de constituer les tables, les chefs de table entrent les emails des étudiants de la table (peut-être changer cela avec une simple recherche par nom/prénom).

##### Récupérer un utilisateur par son ID
<a id="get-user-by-id"></a>
Si un administrateur veut pouvoir consulter/modifier le profil d'un autre utilisateur, l'accès au profil de l'utilisateur se fera par son id.

##### Récupérer un événement par son ID
<a id="get-event-by-id"></a>
Pour l'édition d'événements et la réservation d'événements il faut être capable de récupérer les détails d'un événement à partir de son ID.

##### Récupérer tous les événements auxquels participe un utilisateur
<a id="get-events-for-user"></a>
Il faudra être capable de lister les événements auxquels participe un utilisateur.

##### Récupérer tous les événements pour un BDE donné
<a id="get-events-for-bde"></a>
Un BDE ne pourra éditer que les événements qu'il a créé. Pour cela il faudra être capable de récupérer les événements pour un BDE en particulier. 

**NOTE** : Si cet access pattern est difficile à mettre dans la table, on peut se contenter de récupérer tous les événements et filtrer dans la fonction Lambda (de préférence) ou sur le client sur événements qui correspondent au BDE voulu.

##### Récupérer tous les utilisateurs qui participent à un événement
<a id="get-users-for-event"></a>
Une fois sur la page de l'événement on peut voir les utilisateurs qui participent aussi à l'événement.

##### Récupérer tous les utilisateurs pour un BDE donné
<a id="get-users-for-bde"></a>
L'administrateur d'un BDE doit pouvoir récupérer tous les utilisateurs qui font parti de son BDE.