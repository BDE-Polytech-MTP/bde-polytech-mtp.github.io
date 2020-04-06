---
title: "Le déploiement"
date: 2020-04-07T00:32:01+02:00
weight: 2
---

## Déploiement de l'architecture

Pour déployer l'architecture il suffit de passer par CloudFormation qui va nous permettre de déployer notre stack directement depuis un fichier de configuration.
Pour cela il suffit de se connecter sur la console AWS, d'aller sur CloudFormation et de créer une pile depuis le modèle ci-dessous. Il n'y a rien d'autre à configurer.

{{% notice note %}}
Pensez à bien sélectionner la région *Paris (eu-west-3)* avant de créer la pile
{{% /notice %}}

```yaml
AWSTemplateFormatVersion: '2010-09-09'
Description: 'S3 content distribution through CloudFront'

Resources:
  S3Bucket:
    Type: 'AWS::S3::Bucket'
    DeletionPolicy: 'Delete'
    Metadata:
      Comment: 'Bucket used to store frontend files'
    Properties:
      AccessControl: 'Private'
      BucketName: !Sub 'bde-mtp-frontend'

  S3BucketPolicy:
    Type: 'AWS::S3::BucketPolicy'
    Metadata:
      Comment: 'Bucket policy to allow cloudfront to access the data'
    Properties:
      Bucket: !Ref S3Bucket
      PolicyDocument:
        Statement:
          - Action:
              - 's3:GetObject'
            Effect: 'Allow'
            Principal:
              CanonicalUser: !GetAtt CfOriginAccessIdentity.S3CanonicalUserId
            Resource:
              - !Sub 'arn:aws:s3:::${S3Bucket}/*'

  CfDistribution:
    Type: 'AWS::CloudFront::Distribution'
    Metadata:
      Comment: 'A CloudFront distribution with an S3 origin'
    Properties:
      DistributionConfig:
        Comment: 'A distribution with an S3 origin'
        DefaultCacheBehavior:
          AllowedMethods:
            - 'HEAD'
            - 'GET'
          CachedMethods:
            - 'HEAD'
            - 'GET'
          Compress: true
          DefaultTTL: 86400
          ForwardedValues:
            Cookies:
              Forward: 'none'
            Headers:
              - 'Origin'
            QueryString: false
          MaxTTL: 31536000
          MinTTL: 86400
          TargetOriginId: !Sub 's3-origin-${S3Bucket}'
          ViewerProtocolPolicy: 'redirect-to-https'
        DefaultRootObject: 'index.html'
        Enabled: true
        HttpVersion: 'http2'
        IPV6Enabled: true
        Origins:
          - DomainName: !GetAtt S3Bucket.RegionalDomainName
            Id: !Sub 's3-origin-${S3Bucket}'
            OriginPath: ''
            S3OriginConfig:
              OriginAccessIdentity: !Sub 'origin-access-identity/cloudfront/${CfOriginAccessIdentity}'
        PriceClass: 'PriceClass_100'
        CustomErrorResponses: 
          ErrorCachingMinTTL: 300
          ErrorCode: 404
          ResponsePagePath: '/index.html'


  CfOriginAccessIdentity:
    Type: 'AWS::CloudFront::CloudFrontOriginAccessIdentity'
    Metadata:
      Comment: 'Access S3 bucket content only through CloudFront'
    Properties:
      CloudFrontOriginAccessIdentityConfig:
        Comment: 'Access S3 bucket content only through CloudFront'

Outputs:
  Region:
    Description: 'Stack deployement region'
    Value: !Ref 'AWS::Region'
  S3BucketName:
    Description: 'Bucket name'
    Value: !Ref S3Bucket
  CfDistributionId:
    Description: 'CloudFront Distribution ID'
    Value: !Ref CfDistribution
  CfDistributionDomainName:
    Description: 'CloudFront Distribution Domain Name'
    Value: !GetAtt CfDistribution.DomainName
```
