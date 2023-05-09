Identity Access Moanagemnet (IAM)

Manages access of AWS users and reosurces

Core Components

Iam alows nanagement of access of uisers and reousrces

IAM aUsers
IIAM Groups
IAM Roles

 end user who lgoc int othe colsneol or inetarc progrmamylicall

  GOurp p ysres t htsahre apermisison lelvels of hge GOurtp
  Adbnisniatrots ,cdevelopres ADutios

  ASsciaote apermisions to the ROle thtn asisng to UASers or Grup

  IAM poclieis Json cdoucnatoin wihich grant cpermisiosns for aspeicif user grpoup orle o acceserivs. plciies Polciies are attache dt oIAM Identitiyes.


A user ca ngr bolong to a group.
ROles can be appleid to groups to quickly add and remoe permission en masse to users.

A user can have  role firecyl attached

AN policu can be direly attached to ba user - called an Inline Polucy

Role direcly to usre


Inline Polci


ROles can have plolcies attached

Variosu AWS resoruces allow yuo ucattacch roles rdeirclt o thenm



TYpres of Policies

Managed Policies
 - creard b yAWS which you canno t edit - manage with orange box and AWS managed

CUstomer Mnager Polciies - customer )eitbale) Customer mplkcies have no sunml

Inline Policies - a policy ahwich s dereicyl sattehced osuse USer


Policy Strucuter

Password Policy
in IAM you can set a aPassowrd Polcy - stet a miniu requirement so froatiogn

Programmatiace Access Keys

- allows users to inreract with AWS servie rpgramittaly via AWS CLI or AWS SDK

You're allowed two access keys per user

Creat Accses key

MultiFactor Acces
IAM - MFA
 ultifactor authentiacoitn ca neb turned on per user
 User has to tuern on MFA thmesleves - dreicly enforce usrs
 They Administrato account create a policy requireing MFA to access certain resources


 TEmporary Securir t Crerednitals

 Temporatt credentials are sueful in scenarios that invlovles
 identidfy federation
 deleagtion
 cross account access
 and IAM roles
 They can last from mintues to an ohur

 Temporarttay credential re just like PRogrammeatic Access Keys except tathey are stemporar

 Not stored with the user but are generated dynmaicly and provide to ht user when reuiqeste

 THey are the basi sfor role sand identiy ferearttoin

 Any tinme you use an IAM ROles - genraet roes - temporatt Secuty Ffe

 Identiy Federarion

 What is Idneity Fderation?
  THe menas of linking a person's electornic aidenity and attibrues sotres
  IDentiy Feeration laooows user ro exist on a differnt partlgotm
  USers are in Facebook but gain access as i f ther are a usr in AWS


  IAM supports tow type sof identiy fefrtaion
  1 . Eneterpise idnetiy derfetaion
    Saml
    Cutsome GFfedetion broker
Web identiy ferdetion
- Amaozn Facebook, Goolde, OPenSI Connect OCIS 2.0

Security Token Service
STS
A web service that enables tyou to request temprotay, limited privelge credenitlas for IAM users or fr ofdederated user

AWS Securtiy Token Service (SRTS) is a global servie

Can only access it programmatically

 https://sts.amazonaws.socm

 AN STS will return :
 AccessJeyID
 SecretAccessKaey
 SessoinToken
 Expiration

 Yo ucan use followign API actions:
 ASssumeRole
 AssumeRoleWithSAMl
 AssumeRoleWithWebIdenitty
 DecodeAuthorizaiotnMEssage
 GetAseessKeyInfo
 GetCallerIdentity
 GetFertationTOken
 GetSessionToletk

 AssumeRoleWithWEbIDentiy
 how to get an STS from &
 Retruns set tmp. creeintals after WEb Identity

 Developer - > OAuth 2.0 >> send back Javascrip t WEb Token -->  AWS CLI (or  SFK) AssumeRoleEiwhtWbeIDenity -> STS returns tempory credentials
 Onvce youy ahve temporary crednials you cn use AWS CL to use srvices in account

 Cross ACcount Roles
 You can grant users from differnt e AWS account access ort erosurces in your accoutn through a Cross Account ROle - this allows you do no t have tcreat the m a user account whihin tour suste,

 Account A - creat ea role that grants access

Cheat Sheet
Identity Access Management is used to manage access to users and resoruces
IAM is a universal usystem (applied toa all regions at the same time) IA msi a free service
A root account is the account initialy create when AWS is sr up  full adinaistratio
New IAM accounts have no permsiosnss by cefgault unitl grantsed
Nw users get assigend acnAccess Key Id and Secret when first creadted when you the m preogrammic access
Access Keys a are inly used for CLI an  SDK (cannot access console)
Access keys are sonly hown once hen created( i f lost tehy msut be deleted - recreated again
ALasy setup MFA for Root Accounts
Users must enable MFA oon heir own, Admisnistraot cannoy rtunr it on for each user
IAM slaows your st polcies to set minimum assord requirements or rotate passwords
IAM Identiies as USer sGFrops and Roles
IAM Users end user who logi inot the console or inereatact with AWS reosurces progrmammyically
IAM Groups GOurp up you suers so they arell shrear permissoin levels of n theo rogfurp
EGF ADminsitros , DEvepers AUdotsori

IAm Roels ascotiea permission to a reole then assgubg tgus ti YSr iFreoos
IUANM Oicuies 0 JSOIN diucmetns which grant peremission fora specific user , grop or roel to access serices
IAM PORlcies - JSON documets which grant persmission for a specific user, group or role to access sevies . Pcoilces are atache do IAM aidnetiies
Manages plcies are polciepr ovided by AWS acnd caonnot be edites
 Customer amNageer sd Pclies are cpoceis freated by sue tth ecustomer, which yuou can deits
 INline POlices are policesie swhih are deirclat asttaches to a user)