+++
title = "Réservations"
date = 2020-04-30T21:05:31+02:00
weight = 3
+++

### Réservations

#### Étudiant

Un étudiant peut voir la liste des événements auxquels il peut participer, participe, ou a participé. Pour chaque événement l'étudiant peut voir le nom ainsi que la description de celui-ci. On peut classer un événement dans 5 catégories :

1. Un événement que l'on ne peut pas encore réserver (`now() < bookingStart`)
2. Un événement que l'on peut réserver (`(!bookingStart || now() >= bookingStart) && (!bookingEnd || now() <= bookingEnd)`)
3. Un événement qui n'a plus de place de disponibles
4. Un événement que l'on a déjà réservé
5. Un événement que l'on ne peut plus réserver (`now() > bookingEnd`)

Pour réserver un événement, il clique sur le bouton de réservation de l'événement ; si à ce moment là l'événement n'est pas plein, une réservation est créée pour l'étudiant qui est renvoyé vers page détaillant celle-ci. Il peut alors répondre aux sondages proposés et voir qui a aussi réservé l'événement.

{{% notice note %}}
Un peu imaginer un indicateur pour signaler si des sondages obligatoires n'ont pas encore été remplis.
{{% /notice %}}

#### Utilisateur avec la permission `WRITE_BOOKINKS`

Un utilisateur avec la permission `WRITE_BOOKINGS` peut changer les choix des utilisateurs concernant les sondages. Il peut aussi supprimer des réservations et en ajouter.

##### Modifier une réservation

L'utilisateur peut lister les réservations d'un événement ou d'un étudiant, il sélectionne ensuite la réservation et se retrouve sur la page lui permettant de modifier celle-ci.

##### Supprimer une réservation

Lorsque l'utilisateur est sur la page d'une réservation, il peut supprimer une réservation en cliquant sur un bouton de suppression, une boite de confirmation apparait alors et dans si l'utilisateur valide sa demande de supression, la réservation est supprimée.

##### Ajouter une réservation

L'utilisateur se rend sur la page de l'événement et peut ajouter une réservation pour un étudiant. L'ajout de cette réservation peut mener le nombre de réservations à dépasser le nombre de places disponibles.