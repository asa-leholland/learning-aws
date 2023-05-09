AWS Cloud Trial

Is a servie that enabled government, co plicance operation al aduting, and risk auditing of your WS accout
AWS CLoudTrail is uesed t oiomiontr API calls and ACtions made of n the AWS Account
Easily identiy which susers and accounts made the call th o AWS eg.

Where SOurce IP aDdress
When Evetnt TIme


CLoud Trail Event History
Cloud is alread loggin f by deafult and will colllecltogs
Igf  you nede more than t90 days yoiy need to craet a Trail
Trails are output to S3 and do not have DUI like Event Hisotyr
To Analzye a Trail oud have to USer AMazon Athena

ClousdTrail Loggins
 Atrail can be set to log to all reiogions

 A Trail can be set to across all accounts in a na ROganiztion

 You can Encryp t youyr Logs using Servier sisde encription via Ket Managemesn Sevices (SSE-KMS)

 We can snsure Integr iog lofs to see if hey have tameperew ewe need to log File Validation

 CLoudTrail to Cloud Watch
 CloudTRrail can be set to deliver event ot a ClopudWAthc Logs

 CloudWatch eanLogs enabled you to receive SNS snotiicatoin from CoudWAtch when API activie

 Managemnt vs CData Evnts

 Managemnet Evnta

Tracsk manageme operaiotn - turne do ndef dedault , can't be druntedd. Vonfiguring secuurkt ,AIM AAtachRolePOluc API operaiotns
REgiosteitn devices
COnfigtiog rules for roting data
Setting up logging


 Data taEvents
Taaskcs sepcific operatrions for sepcigf iAWS servcies
DFata events are high olumn logging and will result in additoinal charges
Stack GetObjectDelte OBject Pu tOBjetx
When you need o know who to blame, think CloudTrial
Govnermneac omplaincoprations al autiditn aand risk auditing are keywoads

CLou dTrial by Default logs event data for the past 90 days via Event Hisotyr
To trakc beyondf 90 days you need to create Trail
To ensure logs have no tbeen tampered with you neeed to tuern on Log il Validation options
CLoud Trail Ogos ca neb encriupy ed using KMS (Keyu Managemen Tseve)
CLouss Dtrail acn eb set ot log across all AWS sccounts in an ORganiztoin ad alll reiogns oin as Coun
CloudTrail logs can bestremesd to CLoudWAtch lgos
Trails are outputttes to an S2 bucket that yo usepciy
Cloud Trail logs two lkign sof events: Maagment eEvnts anDAtat Events
Mangeent Evbents log mangemetn operaitons eg Atach Role Poluc
Data eVents log data operations rfor srouces S3 Lamda eg Get ONject Flete ONject and PutOBjest
Fata Eventa are deibale by degfual whne craring a Trail
Trail logs in LS2 can be aa alyze sing ZAHten