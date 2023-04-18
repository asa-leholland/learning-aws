# Simple Notifcicaiont Service (SNS)

Sub scribe and send notifiction via text message, email, webhooks, lamdas, SQS and mobile notifications

## What is PubSub
Publish-subscibt epatterns commonly implemetned in messageing systems
Sencer of message (publisher) does not send mesaages directly to receivers
Instead send messages to an event bus which categoriezes messages into grop.
Receives of messages (subscibers) subscribe to thise groups. New messages htat appear within the subscription are imeediaetely develivere d ot them

Publisher have no knowlsge of who their subscpers are
subscribers do not pull for messages
messages are instead autoamtiveally and imemegsiately pusheed to ubscribers
messages an events are interchangelable terms in pub sb

## What is SNS

SNS is highel abailbael ,udrable ,secure, ffully managed pub/sub messageing service that ienables you to devouple microservices, distributed systems and serverlss applicaitons
Application Integration
publishers push events to an SNS topic
subscribers subscribe to SNS topic to have events pushed to them


## Topics
Topics allow you to group multiple subscriptions together
A top ic is able to delivver to multiple procols at once eg emial, text http/s
Wjen to[pics delvever messages t susbcribers ith woll wautmatcally format your message accorind to the subscribers chosen protocol
You can ecnytptopcis vis KMS

- Publishers don't care about the scubscribers protocol
- Subscribers listen for incoming messages

## SNS Subscriptiosn

A subscription can only subscribe to one protocol and one topic

The following protocols

HTTPS and HTTPS create webookhs into your web application
EMail good for ineternal email notificaiotns (only supports plain text)
Email JSON sens you json via email
Amazon SQS place SNS message into SQS queue
AWS Lamda triggers a limbda function
SMS ened a text message
 Platform applicaiton endpoints - Mobile Push

 You create subscriptios on topics

Application as a Subscriber - Push notification messages directl to apps on mobile devices

Push notificaiton messages sent to a mboile endpoint can appear in the mobile app as message alerts  badeg updates or sound s

Amazon eDevice Messaging
Applie Push Notificaiont Serivce
Baidu CLous Push
Firbease Cllouodu Messaigfnaign
Microsoft Push Mntofication for WIndoew Phoine
WIndows Push Notificaiton Sercvies


## SNS CheatSHeet

Simple Noticatio nService (SNS) is a fully managed puib sub messaging service
- SNS is for Application INtegertion. It allows decouples services and apps to communication with each other
- Topic is a logical acces point and communication chanle
- A topi  is able to deliver to multiple protocls
- You can encrypt topics via KMS
Publishers use the AWS API via AWS CLI or SKA to push messages t o a topci
Many AWS Services integrate wit hSNS and act as pobliushers
SUbsctioptions subscrpte to tpoics
WHen a topic receives a message it automattclal and immedaiteiona lpushesm essages to subscribesrs
All messages published o SNS arres tored redeuindanyl across multiple availabilir tonzes

Following prootocols
- HTTPS and HTTPS create ebhooks into web applciation
- Email is good for internal email notificatoins (only supports plain text_
- Email Json sends you json via email
- Amazon SQS place SNS message into SQS queue
- AWS Lambda triggers a lambda function
- SMS send a text message
- Platform aplpclaition endpoints 0- enables you to have native notifiacoti