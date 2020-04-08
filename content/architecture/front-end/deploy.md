---
title: "Déploiement"
date: 2020-04-08T09:28:56+02:00
---

## Déploiement de l'application

Dans notre cas nous utiliserons le framework [Angular](https://angular.io/) pour construire notre application cliente. Pour déployer cette l'application sur notre architecture précédemment créée, il nous suffit de build notre application `ng build --prod` et nous devrions alors avoir notre application dans le dossier `dist/<app-name>`. Ensuite il faut copier l'application dans le S3 Bucket avec la commande `aws s3 cp ./dist/<app-name> s3://<s3-bucket-name> --recursive`.

{{% notice note %}}
`<app-name>` correspond au nom de votre application Angular et `<s3-bucket-name>` est le nom du S3 Bucket vers lequel vous voulez envoyer les fichiers. Donc notre cas c'est le nom que vous avez récupéré lors de la création de la stack avec CloudFormation
{{% /notice %}}

{{% notice note %}}
Il faut bien sûr avoir installé les CLI d'Angular et d'AWS ainsi qu'avoir configuré le CLI d'AWS avec `aws configure`. Il vous faut aussi avoir les droits d'accès au S3 Bucket (les permissions se gèrent avec AWS IAM)
{{% /notice %}}

Une fois cela fait, l'application devrait être disponible en vous rendant sur le domaine CloudFront que vous pouvez retrouvez dans les sorties de la pile précédemment créée via CloudFormation.