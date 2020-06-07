---
title: "Création d'un événement"
date: 2020-06-07T12:05:40+02:00
weight: 1
---

## Aspect fonctionnel

{{% notice note %}}
Ici, un `groupe` désigne un ensemble d'utilisateur aillant des attributs communs (même section, même BDE, adhérent ou non, etc ...).
Cette notion sera développée ailleur plus tard.
{{% /notice %}}

Un événement est décrit par les choses suivantes :

* Son nom
* Une miniature (à terme, peut-être, n'est pas une feature prioritaire)
* Un état d'ouverture (réservations à venir, réservations ouvertes, réservations terminées)
* Sa date d'ouverture des réservations (optionnelle)
* Sa date de fermeture des réservations (optionnelle)
* Sa date d'organisation (optionnelle)
* Le BDE qui l'organise
* Le nombre de places par *groupe* (peut être illimité)
* Un prix par *groupe* (peut être nul)
* Un moyen de paiement (optionnel)
* Un état indiquant si c'est un brouillon ou non

Un événement définit comme étant un brouillon ne sera visible que par les organisateurs ce celui-ci. Dès lors qu'un événement n'étant plus un brouillon, celui-ci est visible par TOUS les étudiants.

L'état d'ouverture d'un événement permet d'indiquer si des réservations sont actuellement possibles. Cet état est modifiable manuellement par les organisateurs ou automatique si des dates d'ouverture/de fermeture des réservations sont indiquées.