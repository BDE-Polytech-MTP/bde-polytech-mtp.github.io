---
title: "Introduction"
date: 2020-04-09T19:07:54+02:00
weight: 1
---

## [RDBMS](https://fr.wikipedia.org/wiki/Base_de_donn%C3%A9es_relationnelle) VS. [NoSQL](https://fr.wikipedia.org/wiki/NoSQL)

Comme pour beaucoup de systèmes d'information, nous avons besoin de stocker des données. Pour stocker ces données nous allons bien sûr utiliser une base de données et le choix d'une base de données relationnelle ou NoSQL s'offre donc à nous.

Comparons alors rapidement les deux solutions :

|                   | RDBMS                               | NoSQL                        |
|-------------------|:-----------------------------------:|:----------------------------:|
| Tables avec schéma| <i class="fas fa-check"></i>        | <i class="fas fa-times"></i> |
| Respect du principe [ACID](https://fr.wikipedia.org/wiki/Propri%C3%A9t%C3%A9s_ACID) | <i class="fas fa-check"></i> | <i class="fas fa-times"></i> |
| Coûteux en CPU    | <i class="fas fa-check"></i>        | <i class="fas fa-times"></i> |
| Coûteux en espace disque | <i class="fas fa-times"></i> | <i class="fas fa-check"></i> |
| Scale bien        | <i class="fas fa-times"></i>        | <i class="fas fa-check"></i> |
| Est peu onéreux   | <i class="fas fa-times"></i>        | <i class="fas fa-check"></i> |
| Est simple à concevoir | <i class="fas fa-check"></i>   | <i class="fas fa-times"></i> |

Après avoir vu le tableau ci-dessus on voudrait certainement se diriger vers une RDBMS plutôt que sur une BDD NoSQL. Cependant deux choses nous importent actuellement : le prix et les performances. En nous pouvons voir que dans ces deux cas précis, une BDD NoSQL est à préférer (cela dépend aussi de la facilité à représenter nos données dans une BDD NoSQL bien sûr).

## DynamoDB

**DynamoDB** est une base de données NoSQL développée par Amazon qui permet une très faible latence à haut scaling. La tarification se calcul à partir du nombre de demandes de lectures et d'écritures et suivant la quantité de données stockées. Pour ce dernier point, on peut facilement prévoir un coût nul pour le stockage (25 Go gratuits). Pour plus d'informations, [consultez la page du produit](https://aws.amazon.com/fr/dynamodb/).

Pour concevoir une BDD DynamoDB qui corresponde à nos besoins nous devons d'abord définir les patterns d'accès à nos données pour ensuite être capable d'insérer nos données dans une table d'une manière qui nous permette de répondre à nos besoins.