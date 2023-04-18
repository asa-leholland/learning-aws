# SQS (Simple Queue Service)

Fully managed queuing service that anebales you to decouple and scale microservcies, distibuted sytemsa nd serverles applicaitons

## What is Queueing Service
Used to provide asynchronous commonicoaiton and decoupe processes via messages /e vent
From a sender and receiver (producer and consumer)

QUeueing - generally will delete messages once they are consumered, simple communication, Not Real Time, have to pull, not reactive
Example: SQS, Sidekiq, RabbitMQ

VS

Streaming: multiple consumers can react to events (messages) event lives in the stream fro long periods of trime, so complex operations can be applied - real time
Exaples: Kinese, Apache kafka, NATS
SQS is for Application Integration
AWS SQS is a solution for the distributed queiing of messages generating by your application
It consolidates isolated application together by linking messageds between
A queue is a temporary repositiory tfor messages that are awaiting processing
Using the AWS SDK write code which publishes messages on to hte queue or you pull the queue for messages

SQS is PULL BASED while SNS is PUSH BASED


## Example Use Case
1. App Publishes messages to the queue
2. Other app pullls the queu and finds the message and does something
3. Other app reporst that they competled their task and marks the message for completion
4. Otiignla app pulls the queu and sees the message is no longer in he queu

Both appsa re using the AWS SDK t opush messagesd and pull from the queu


## Message Size
can be between 1 byte and 256 KB

Amazon SQS Extended Client Library for Java
lets you send essages 256KB to 2GB in size
The message will be stored in S# and library will reference the S3 object

## MEssage Retrension

How long SQS qill hold on to a message in the queu before dropping it
Default = 4 days
minimun 60 seconsd to max of 14 days before deletion

## Standard Queues
AWS SQS Standard Queues alw you to have nearly unlimited number of transsaction per second
Guaranteed that message will be delivered at least once
more hat one copy of amessage could be potneitlaly elievered out of oder
Provides best-oeffort ordering - message is generally delivered i he same order it was sent

## FEFO First in First Out
support multiple orderd message gorups withi na single queue
Limited to 300 transaction epr second
SWS FIFO queus have all he same capabillieis of Standard WQueue


## Visibliy Timeout
period of time that messages are invisible in the SQS squeue, after reader picks up that message
will be deleted from the queu after a job ahas been proessed
if Job is not process befored visibilty timeout prriod message will become visible again for anohtber reade
This can result inthesame result being delivered twice

30 second defdfualt
0 secodn minitue
12 hours max


## Polling

Polling is the method in which we retrieve messsages from q ueue
- Short polling (default) returns messages immediately, eveif the messgae queu being polled ied empty
- When you need am essage right away, shorting pilling is what you nwant

Long polling waits until message arrives in teh queue, or until the long polling timeout expires
Long polling makes int inecpensive to retrieve messaged from your queue as soon as the nesages re availbel
Using long polling will reuce th e cose because yo u cna redice the number of empt y retrieves
Most use cases you want to use Long Poilling

You ca nenavbel lOng polling when receiving a message by setting he qiat time in ReceiveMESssageRequest

### SQS Cheat Sheet

SQS is a queing servie using messages with a queue - think Sidekiq or RabbitMQ
SQS is used for application integration - allows decouples apps to t alk to one anouter
To read SQS use need to pull the queue using AWS SDK
SQS is not pushed based
SQS supports both Standarda nand FIFO queus
Stnadatas aallowsu nlimited messages per seconsd ,does not guarantee oreder ofleivery, alawyas deleivers at eleast once you ust protect again duplicate mesages being processedded
FIFO aimiantes th eore ro messages wtihin a 300 limit
Two lkidns of polling (Short and Logng)
Short pollin returnem smessages immediaetly (ca nresult in eptr result, Default)
Long polling waits auntil message arrives in queue, or if the logn poll timeout expires
In majortyi fo cases, long polling is more desirable
Visibility Time out is the period if tuiim thatmessage are invisiabe in te he SQS queue
MEssages wil b e deleted after a job has process ed (before visibility riomiut expires)
If viaibiltiy imtouet expires, then a job ill be viibile t o thqueue
The devfualt visibilit y timout is 30 secobd
Tioeut avan be 0 secons to 12 horas
SQS can retain messages from 60 seconds to 14 days and by efaulti s 4 ayas
Message size 1 byte oto 200 KB unless Java ca nuncrease to 2GB
