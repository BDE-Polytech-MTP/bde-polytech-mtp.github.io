+++
title = "Authentification"
date = 2020-04-30T21:05:31+02:00
weight = 1
+++

### Connexion

L'utilisateur rentre :

* Son email
* Son mot de passe

Il appuie ensuite sur le bouton de connexion ce qui déclenche un appel à l'API OAuth.

* Si les identifiants sont bon, l'API renvoie le token d'accès ainsi que le token de rafraichissement et l'utilisateur se retrouve la page d'accueil du site
* Si les identifiants sont incorrects, l'API retourne un code 400 et un message d'erreur s'affiche pour l'utilisateur

### Mot de passe oublié

L'utilisateur appuie sur un bouton "Mot de passe oublié" puis renseigne son email avant de valider. Ceci envoie une requête de reset de mot de passe sur l'API GraphQL qui renvoie une des trois réponses suivantes :

* L'email indiqué n'existe pas : on affiche une erreur à l'utilisateur
* L'email a bien été envoyé : on affiche une page indiquant d'aller consulter les mails

Quand l'utilisateur clique sur le mail de reset de mot de passe dans le mail, cela le renvoie vers une page pour reset sont mot de passe. L'utilisateur doit
rentrer son nouveau mot de passe ainsi que confirmer son nouveau mot de passe avant de pouvoir valider. Une fois le formulaire validé, un appel à l'API est effectué pour mettre à jour le mot de passe.

{{% notice warning %}}
Le lien de reset de mot de passe n'est valide qu'un certain temps, ce qui peut mener à un lien invalide. Dans ce cas, la page de reset de mot de passe indique juste que le lien n'est plus valide. (la validité d'un lien se vérifie via un appel à l'API GraphQL)
{{% /notice %}}