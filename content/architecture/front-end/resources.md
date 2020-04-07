---
title: "Les ressources"
date: 2020-04-07T00:32:01+02:00
weight: 1
---

## Les ressources

Nous aurons besoin de déployer 4 ressources AWS pour délivrer la partie cliente :

* S3 Bucket : stock les fichiers
* S3 Bucket Policy : définit les droits d'accès au contenu du S3 bucket
* CloudFront Distribution : sert du contenu à travers le monde
* CloudFront Origin Access Identity : permet d'identifier la resource CloudFront Distribution lors de l'accès au S3 Bucket

![](/images/front-end-architecture.png)