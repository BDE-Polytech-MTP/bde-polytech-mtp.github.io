+++
title = "Authentification"
date = 2020-04-30T21:05:31+02:00
weight = 1
+++

## Introduction

La fonctionnalité principale du site du BDE étant la réservation d'événements, nous avons besoin d'authentifier les utilisateurs du site. 

#### Aspect fonctionnel

Les utilisateur ne pourront pas créer de compte directement, le BDE devra inscrire les étudiants sur le site afin de leur permettre de se connecter, cela évite qu'un étudiant externe à l'école puisse se créer un compte et réserver un événement. Un système de parrainage permet aux externes d'obtenir un compte et ainsi de se connecter.

##### Étudiant de l'école

Pour un étudiant de l'école, les étapes de la création d'un compte sont les suivantes :
* Le BDE de son école lui crée un compte sur la plateforme en renseignant son adresse mail, sa section, son nom et son prénom.
* L'étudiant reçoit un mail à l'adresse indiquée lui permettant de valider son compte dans un temps imparti
* L'étudiant clique sur le lien qui l'amène sur une page lui demandant de choisir un mot de passe
* L'étudiant entre son mot de passe et valide

Le compte est créé.

##### Externe

Pour un étudiant externe à l'école la procédure est semblable :
* L'étudiant parrain entre le mail de l'étudiant externe
* L'étudiant reçoit un mail à l'adresse indiquée lui permettant de valider son compte dans un temps imparti
* L'étudiant clique sur le lien qui l'amène sur une page lui permettant d'entrer son nom, son prénom et son mot de passe
* L'étudiant rentre les informations et valide

Le compte est créé.

{{% notice note %}}
La fonctionnalité de parrainage doit pouvoir être désactivable par le BDE en question
{{% /notice %}}

#### Aspect technique

Différents systèmes existent pour gérer l'authentification des utilisateurs sur un site et dans notre cas nous allons utiliser les [JWT](https://jwt.io/) (JSON Web Tokens). Un JWT est une simple chaine de caractères composée de 3 partie :
* L'en-tête : contient des informations sur le token en lui-même comme par exemple l'algorithme utilisé pour signer le token
* Les données : contient toutes données que l'on veut stocker dans le token comme par exemple l'identifiant de l'utilisateur identifié par ce token
* La signature : contient une signature basée sur les deux première parties et une clé gardée secrète par le service d'authentification

L'en-tête et les données sont visibles en clair par le client (ce sont les juste des objets JSON encodés en base 64) ce qui veut dire qu'aucune information sensible ne doit être stockée dans le token. La troisième partie quant à elle sert seulement au service d'authentification à vérifier l'intégrité de l'en-tête ainsi que des données. La signature est le résultat des la concaténation des deux premières parties, le tout passé au travers de l'algorithme indiqué dans l'en-tête à l'aide d'une clé secrète connue seulement par le service d'authentification.