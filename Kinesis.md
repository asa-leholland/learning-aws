# Kinesis

Scalable and durable real time data srteaerming serviece
To ingrest and analyze data in real time from multiole sources

When you need real time, think Kineseis
Collecting ,p rocessing kaand anlzying streaming datain the lcoud

Steraming Data example - stock rpices,d game adata, socail network data, geospatila data, cick stram data

Thare are 4 different ypes of Kinese Streams
 - Kinese Data Streams
 - Kineses Frehourse Delivery Stremas
 - Kinsese Data Analytics
 - Kinsees Video Analytics


## Kinesis Data aSteremas
- A bunch of produtes send data through Kinesis Data Strems (which are buiuld of shards) into consumers, wich are configured to be EC2 sinstnaces with unique code that gets sent o  Redshift, DynamoDB, S3 or EMR

You bpay per running shard
You cnn have multiple consumers, you misut manually configure your cnuosumers
Data can be perstingi nfrom 24 hours to 168 hours ebfoer it diasppears from stream

## Kinesis Firehous e Delivery system
Profucers send to Kinesis Firehouse , which has a Transform Compress Secure process and is hen immediately consumed on the sother side (for exmample, into an S# bucket, or REedshifr or Elasticserach or splunk
You hc=hoose one conumeser from pa refdined list
Data immesdaitely idsappears once it is conusmed
You can convert incoming data to other file formats, compress and secure data
You conl pay for data that is ingested
No flexibilty on data types
Very inexepensive - simpelr to sur

## Kinses Video Streams
Securely reitain and vaideo and audio encodde data
Ingest mvieo and aduio encoded ata from variosu sevices and or sercie
Output video atat to ML or video process
Consumers can be Sagemaker , Rekogntion, Tensorflow, Custom Video Processing, or HLS base vide oplayback\Typcially used for Security Cameras, Web Camera, Mobile camers

## Kinesis Data Anlaytics

Lets you pass some inpuit strema (can be Data Strem, Firehouse or Vidoe Stream) and pass to Data Analytics which runs throug custom SQL you provide and res treuslt are then output
This allows for real time analytics of tyour data


## Amazon Kinses i the AWS olutio nfor collectin processing an anlyzign streamign data in the cloud
When you need real time, think Kinesios
Kinesis Data astreams - price per runnign sahrd, data can persist withi nth estrea, data is oreders and every consumer keepp its oen poisition. Conusmers must be manually added (coded) and ata persists for 24 horus (efual) o 168 hours
Kinesis Firehouse - pay for only h the data ingested , adata immediately disapepars once oprocessed
Conumser of chosice is from a prdedeifned set of srvices, S3, Redshift, Elasticsearhc ros pinl
Kinesis Data Anlytics - allows you to perfrom quereis in real tiem - need sa Kinses Data Streams or Firehouse as the input and poutpouis
Kines Video anlaytics - securely ingersts andtores video and uadoi encoded data to cnoousmers susge a s SagemKer, Rekognition or other sertvies to applic Machien Learning and Vidoe Procesiing
KPL (Kinesis Proucer Libarary_ is a Java library to write data to a stream
You ca n wrt edat to strem ausng QAWS SDK but KPL is more eficincet
)