---
title: "Front End"
date: 2020-04-06T23:55:45+02:00
---

## Introduction

La partie cliente de l'application sera fournie via **AWS CloudFront** qui prendra source dans un **AWS S3 Bucket**.

**AWS S3 Bucket** est un service de stockage. Celui est facturé à la quantité de données stockée ainsi qu'au nombre de transactions effectuées (lectures, écritures). Pour plus d'informations, consultez [la page du produit](https://aws.amazon.com/fr/s3/).

**AWS CloudFront** est un service de distribution de contenu. Celui-ci est facturé à la quantité de données (au Go) transféré. Pour plus d'informations, consultez [la page du produit](https://aws.amazon.com/fr/cloudfront/).

Pour mettre en place cette architecture nous utiliserons **AWS CloudFormation** qui permet de définir une architecture et de la déployer depuis un simple fichier de configuration. Pour plus d'informations, consultez [la page du produit](https://aws.amazon.com/fr/cloudformation/).