# Cognito

Amazon Cognito is a Decentralized Managed Authentication service
Think Sign-up, sign-in integration for apps using Facebook, Google IE Social Identity Provider


```mermaid
graph TD

Client
Client-->|Authenticate and get tokens|User[User Pool]-->IpDs[Identity Providers <br/> IpD <br/> Social Sign-In or OIDC or SAML]
Client-->|Exchange tokens for AWS credentials|IDer[Identity Pool]-->Syncs[SYncs other PCs or mobiles]
Client-->|Access AWS services with credentials|Other[Other AWS Services like DynamoDB or S3]
```

## Cognito User Pools
Cognito user pools are a user directory with authentication to Identity Providers (IpD) that grant access to your app

## Cognito Igentity Pools
Cognito Identity Pools provide temporary credentials for users to access AWS services

## Cognito Sync
Cognitory Sync alllows users to sync data nas preferncec across all devices


Web IDneiity Fedferation - eo exchange identity and security info between an IdP (idetity provider) and application

Identity Provider - trusted provider of your user iedneity lets you acuthitetcate to access other servicces- Identitry Providers are Googlie, GitHub, Linkedin GFacebook, Amazon, Twitter
Identity Providers are powered by either OAUTH (using the OpenID Connect OIDC protocol)
OAUTH is commonlt used for Web Identity FDederation

Alternatively can use Single Sign On (SSO) which is commonly implemented uisng SAML (Security Assertion Markup Language)


## Cognito User Pools
User Directory with authentication to IpD (Identity Providers) that grant access to app
Basccially a standard aadtabase of directories for Sign Up, Sign In, Account recorvery, and Account Confirmation
- Allows users to sign in deircely to the user pool, or using Web Identiy DFefderation
- Uses AWS Cognitor as the idetity borker bwtween AWS and IpD
- Successfuly user authetncatioa generates a JWT (json web otken)
User pools can be thought of the as the account used to access the system IE email address and password
- Persisted using JWT (json web token)

Cognito User Pools allow you to set choos ewhich attbiutes and set password requirements, apply MFA, restrict user access via adminverification, and set up analytics using PinPoint (think Mail chinp) for user campaigns

Key: This is a way to decentralize your user authenticatoi


## Cognito Identity Pools
Provides AWS credentials to access services
Identity can be though of as the acutal mechanism authorizing access to AWS reousrces

IE, ig you want an application to access S3 or Dynamo DB you need a Cognito Identiyy Pool not a User Pool becasue this is TEMPORARY access

Select a Provider (Cognirot or any), or allow unauthenticated identityies

Download the SDK

## COfnitot Sync
Lets you sycn user data and preferneces across devices across code

Uses push synchtonaztion to push updates and synchronzie data
Uses SNS under the hood


### Settign up Cognito User Pools: Set App Integration - provicde a callbakc URL

Can provide a callback URL, and Oauth scopes (phone, email, openid, aws.cognito.signin.user.admin, profile)

Allowed Oauth flows: authorization code frant, impicait grant and cleiant credentials



Can create a 10minutemail email account for testing
https://10minutemail.com/



### Cheat Sheet
Cognito is a decensralized managed authentication suystem
When you need to easily add authentication to mobile and desktop apps, think Cognito
User PPools user adirectroy: allows user to authenticate using OAuth to Identiy Povider such as Facebook, Goolge aor Amazon to connect to web-appl;ications. Cognito User Pool is in itself an IpD
User Pools use JWTs for perstisitng authenticaiotn

Identity Pools proviee temporary AWS credentials to services lik S3, SynamoDB
Cognito Sync can sync user data and preferences across devices with one line of code (powered by SNS)
Web Identity Federation exhange idenity and securit informatrion between an Identif[yt Porivide] (IdxcP0 nad an applicatoin)

Identity Provider (IdP) - a trsuted provider of your user identiy that lests you use auntihecation to access other servers, eg DFFfacebook, Twitter Google amaaonz

OIDC is a type of idetntiy provider which uses OAuth
SAML is a type of Identity Provider which is use d for signle sign on