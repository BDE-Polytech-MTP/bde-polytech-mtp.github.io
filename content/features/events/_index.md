+++
title = "Événements"
date = 2020-04-30T21:05:31+02:00
weight = 2
+++

### Création d'un événement

Un utilisateur aillant la permission `WRITE_EVENTS` peut créer un événement pour son BDE. Pour cela il renseigne les informations suivantes (qui peuvent se distinguer en 3 catégories) :

##### Les propriétés intrinsèques de l'événement

* Le nom de l'événement
* La description de l'événement : un texte en markdown
* La date d'ouverture des réservations : peut ne pas être spécifiée, auquel cas l'événement sera directement ouvert aux réservations
* La date de fermeture des réservations : peut ne pas être spécifiée, auquel cas l'événement sera ouvert aux réservations indéfiniment
* Si l'événement est ouvert aux adhérents

##### Le nombre de places qui peuvent être réservées

* Le nombre de places par école :
    * L'école concernée : (la liste des école peut être récupérée via l'API GraphQL)
    * Le nombre de places pour les adhérents/non-adhérents de cette école (une seule et même valeur)
    * Le nombre de places pour les externes de cette école

##### Les sondages

* Les différents sondages proposé :
    * Le nom du sondage
    * La description du sondage : un texte en markdown
    * Si le sondage est destiné seulement aux adhérents ou pas
    * Si une réponse au sondage est obligatoire
    * Si le sondage est modifiable seulement par un admin ou pas
    * Les différents choix possibles pour ce sondage :
        * Le dénomination du choix
        * Le nombre maximum de personnes qui peuvent sélectionner cette options (optionnel)


#### Exemple de la structure d'un événement

{{% notice note %}}
Les noms d'attributs ci-dessous ne sont que des exemples, il ne représentent pas exactement le choix définitif des noms qui seront utilisés pour l'API GraphQL.
{{% /notice %}}

```yaml
title: Campo
description: "# Teaser

              Passez un **incroyable** week-end dans un lieu de *rêve*.

              # Déroulement

              On se retrouve place de l'Europe à 8h pour le départ en bus et c'est parti !"
bookingStart: 10-09-2021
bookingend: 17-09-2021
limitedToMembers: false
places:
    # Montpellier
  - bde: dfsd65f-zaza32-54dfd65-sdfs45f
    schoolPlaces: 300
    externPlaces: 0
surveys:
  - title: Payé
    description: Est-ce que la place a été payée ?
    limitedToMembers: false
    required: true
    adminRestricted: true
    choices:
      - name: Oui
        max: -1
  - title: Régime alimentaire
    description: Veuillez renseigner si vous avez un régime alimentaire nécessitant une attention particulière
    limitedToMembers: false
    required: false
    adminRestricted: false
    choices:
      - name: Végétarien
        max: -1
      - name: Végan
        max: -1
      - name: Sans gluten
        max: -1
      - name: Autre
        max: -1
  - title: Caution
    description: Est-ce que la caution pour les bus a été donnée ?
    limitedToMembers: false
    required: true
    adminRestricted: true
    choices:
      - name: Oui
        max: -1
  - title: Bus
    description: Dans quel bus voulez-vous être ?
    limitedToMembers: false
    required: true
    adminRestricted: false
    choices:
      - name: Bus 1
        max: 60
      - name: Bus 2
        max: 60
      - name: Bus 3
        max: 60
      - name: Bus 4
        max: 60
      - name: Bus 5
        max: 60
```

### Modification d'un événement

Tous les paramètres d'un événements doivent pouvoir être changés.