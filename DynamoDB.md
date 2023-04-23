# Dynamo DB
A key-value and document NoSQL database which can guarantee consistent reads and writes at any scale

Key Value has a key which references a Value

Document Store = Nested Data strcuture for KV

DynamoDB = features fully managed, mult-region, multi-master, durable, build in securirt,y backeup and restore, in-memory caching

Provides eventual consistent REadfs (default) and Strongl Coonsisten Reads

Specify your reads and writes capacity per seconds

Data stores across 3 ifferent AZs and alll o SSD


- Table: contains rows and columns
- Items: row of data
- Atributes: columns of data
- Key: header of column
- Value: acuual data

Read Consistency
- eventual consistend reads - default
- when copies are being updated across regions it is possibel for you oto read and be returnged an inconssisten copy
- reads are fast but there is no cguartnee dof bconsitent
- all copeis o d darta eventually necome generally consistent within a second

Strognly Consistent Reafds
whene copeies are bieng updated and yo uattempt t oread, it will not retu na resul ubtil all coipies are consistent
You have a gauarntee of consistenc bu t tetade off ishigherlec (slowly reads)


Dyannamo DB automaticlalycreates partitiaons for you as data grows
localted in tsame are a oo access quicker

Primayr Key
Simple Primary Key


 How a Primary Key ith aonly a Partition Key chooses which particion

 Partision A    Partitiona B        Particiain C


DynamoDB Internal Hash Function
- decides which partiion o  rite aat
- Takes your new data and a Primary Key


A Composite Primary Key = Primary Key made up a partition and a Sort Key

Paritiona A
Adds new daata = into same artiion that stores imilar data



# Query
Allows you to find items in a tabe based on priamry key alues
WUeyr an y table or seconday index that has a copmosite cpimrayr key (partiioan an sort key)
By defualts, reads as aeventually consistent
By dfualt reatun all attirbutees for itmes
You cna return speicifec iarritbutes by usui g ProjectExpression
By default is sorting ascenting

Scans return evertyhing -

Avoid scans when possible


#p P rovisionseCapacity
- confiured RCUS (Read Cpaciaty Units) and WCUs (write capacity Units
- can set Dynamoc BD for proevisiosn to scale vapacity up and down based on utilization
- If you cao beyond coapacity yo will ger PRovisionsThourghuputExceeded Exception
- )
- THrottleding - requata that are throreled will be froppd d- dat alosss


    Read Capacity Units
    A rea capaciy unit represnts one strongly consistent read per second
    or two evetally consistne reads per seocnds f
    or an itme up to 4 KB in size

How to calcualte Reads Capacity Units

50 redas at 40 KB per itme
(size in KB) rounded to 4, divide by 4 .... x (number of reads) = RVUs


33 reads at 17 KB per item (strongly conssistent Reads)
17KB --> 20 KB
(20/4) x 33 = 132 RCUs

Eventualy Cocnsitentc,t, just calcualte strong RCU, divide by 2 ad d round up


## Write cCapacty

1. ROund up to nearest 1, times bnumber of writes



Global Tables
- Amazon Dynamo DB global tables provide a fully managesd olution for depoloying a multi-region multi-maseter databae, whithaving to buld and miantain your own replication solutoin
- To create a floba ltables:
- Use KMS SMKENable Streams
- Stream typ of New and Old Image
- THen you cna add a region

Used for muliti-regio, multo-master without haveing to deploy your own replciaticoin solution


ACID Transactions -
Atomicity
 COnsiistency
 Isolation
 Durability

A transaction represnta  change that will occur ot hthe tadatabase - if any fependent donsiotns aila htan a transcation roll robakc


DynamoDB affers the ability to perfom transsaction at no addiotnal coss
using Transact Write ITems anfd Tranasct Get Items opeartions
DynamoDB transaction allow for all or nothing changes to multiple itmes buto witin adn acrsso tobales

DFYnaoiDB performs two underfliyn reads or write of every tiem in teh  teansaciotn
one tio oprepae rthe rtasactiono
ne to  commite the reanasatoin

THese two unedrlying read rrite opeartions are visible in your AMazon Cooudathc metrics

You can use consition Check with SYnaicBD transaciotn to do a precontaoio check\
Yo can check that an exim exist to check that item speicif catrtribtuesi thg time

## Support for TTL -
Allows you ato add a column for expiry_at which stoores a datetime as an EPOCH which is numerical stringigeid number of itme
then if the TTL is exceeded then it is autodelete


- THrotlling Exception - rate of rquests excees the allow dthropugu = -t his aexceptio nmight be return if you perform aony of the ollowing upaortions too rapidly (update Table, CreateTable or Deleee Table)

Provision TroughoutExceedeExeption - you exceed your maiximun allows provisoine thourput for a tbale or soro one more more glaboal seocnay indexe

The WAS SKD will autoamtically reur using Expoentinal Backeodd when an error occurs
attempt th request again 50 100 300 m up to a minute

# #Indexcses
a database index is a vcopy of esected column of data in a ratabase which is used to quickly sort

DynamDB as to o types of indexesLS
I - local seconadyar index - can only be crearted with initla table
GSI = global seoncay index
You should generally usse global over local
Strong consistency is a decideing facot

A locval senoadt index can bprobvied strong xonistnecy
a flobal secondar y canoy provife esting consistnecy

## WHat is a Local sceoncaua index (LSI)?
It;s iloc eveyt apartion of an LSI is scope d to a base tbale partioin
that has the same partion key balue
THte total size of inidexed itmes hor ow any one parition key van't exceed 10 GB
Shoreas provision sthougpur settings gor rea dnarit activiet ith hte table it is indexing


LSIs are acreartd with the initial tableLSI
 cannot be added modified or xelted after crearion
 aN LSI needs oot ha partition oand sort ke
 The aprition key mus t hbe the same as the base table
 thte sort key shoul be fifferet rom te aase tbale



 LSI vs GSI

 Characteristics        Lcoal Seconart Inex     Flobael Seconday iNex
 Key schema     Composite       Soimple or Composite
 Key Attibtues      Partition Key meust he bsame ae base table      Parition and Sirt key can be any attibute
 Size restrionc per partion key value       all oindexed aitems must be 10 GB or laess      unlimies
 Oline index operation      creat inedex on table creation      add, mopify or celete incex antany time
QUeries an praittions       query over asingel partiion as specified by t heapratioin key bslue in he query     query of the eteir table across all paritions
Read Cosnistency        Local Seconay index acmuscam ne Stromgly r Evenyal onsisteny        FLSI ca nonly be aeventual consistenct
Proviso THOUgput conusmpureoin      LSI cna hare capacity wunits with teh base table        GSI has its own capacity
PRojected attibrues     LSI ca nrequest attintuiestes are not projected in to the index     GSIS cvan only request he attribures that re projected inod the index

## DAX - DynaoDB Acelerator
DAX is a fully managed in-memory cahce for Dynamo DB that runs isn a clusetr

DAX is ideal for:
- apps that require the fastes possible resoponse tiem for reads - eg, real time bigging, social gamin, and rading applications
- Apps that read a small numer of items more reqionely than others
- APps that are read-intensive but are alos cost sensitve
- Apps that require reperetated read s agains a loarge set of ata

Dax is not aideal for
- apps that require strongly consistent readsapps that doe not require microsecond reposne times for  reads or that oe not eed  t ogf oogllanod repeated read actiiet for m unerlying
- appes ahta re write intensive or that do not perfrom muc h read activier
- apps thar are already sigi na  iffern cahing solution wtih Dymao DB adn are arusing htie o nw client sie lofic fow witikg thin wthat cahcing soluton

ElasticAchcace - useufl for Redis and high -hintesity write applciations

## Cheat sheet
Dynamo DB i a fully managed NOSQL keky/value and document sdatabas
Dynoam DB is suited for workloads with any amount of ata tha trequire preidible read and awrite preformance and automatinc scaling from large ro small and everythwre in between
DynamoDB scales aup and down fo support whatever read nad write capacity you sepcigf per secon in preovisioned capacity mode OR you can set it to On-Demand mode and there is lottlte to no capcait planning
DynamoDB can be set to support evenually consistent reas by default and Strongly Consistent Reas on a per-call basis
Eventll yconsisten reads data s returned immegdiatel by t dat can be inconssitne. Copies of fata will be generally consistent in 1 seocnd
Strongly consistent reads will aalwys read from a leader paritio nsince it always has sn up to dat copy. Data will enever be inconsistent but laatency may be heigher. Copies of fata willb e consistent wiht a guaranee of 1 second
DynamoDB stroes 3 copies of dfata on SSD cdrives acorss 3 AZs oin a region
DynamoDB Most common catatupes are B (Binary), N (Number) and S (String)
Tables consist of ITems (rows) and tiems consist of Atrtirbutes (columsn)
A aprtition is when DynamodB slices your able up into smaller chunks offata, this speepds up reads for larver large tables
FYnamocDB autoamtically creattes partitions
- every 10 GB of adata
- when you exceed RCUSs (3000) or WCUS( 1000) limit s for a singel partition
- When DYnao DB seeds a patter nof a ohht partioin  it will split that partition in an attmpet ot fix the iseue

DynamoDB will ety to evenly split the RCUs and WCUs across partioins
PRiamru eysy define where and how your data will be stored in partiios
Primary key comies in two types:
    - Simple Priamry KEy (using only a parition Key)
    - Composit PRimart Jet (using both a parition and Sor  key
Partitoin Key is also known as a HASH
SOrt Key is also known as Range
WHen creating a simplet Primary KEy the Parition Key value must be unique
WHen creating a composite Primary Key the comiend parition and SOrt Key must be uniqie
WHen USeinf Sort key recors on the pairtion, are lgoically group togeher in Ascenin order
DYnomDB GFoobbal tables provide a fully manages oliution for depoyigmin maulti-region, multi-maseter databases
Dynamo DB supports transatciont via the TranscatWTiteITems andTransactGetITems API Cals
Trnasaction le you qayuer multipe tabes at ince and its a nall or ntohing approach - all API calls must succeed
SUna,ocDNB DTreams allows you to set up a Lambda fucntion triggered every time data is modified in a table to react to changes
Streams d onot consum e RCUs

DynmoBD has two types of index
LSI - Local Seconday index
    - supports stringly or evenutaly consistency reds
    - can obly be created wit hthe initial table (cannot be modigfied or cannaot be deleted unless altso deleting the table)
    - only composite
    - 10GB or less of data per partition
    - Share cpacity units with base table
    - Must share Paritiotn Key with base tbale
GSI - Globa l secondayr index - cannot provide strong consistency
    - onyle eventual consistency reads
    - can creat modif y or delet at any time
    - allows both Simple and Composited
    - Can hae hahteer attrirbuets as Partion Key or Sort Key
    - No size resticiton per partiion
    - Jas its own cpaacit settings

Scans
Your tables should be sdiesgned in such a way that your orklaod priamry access paterrns do no tu se scans
Ovearll scans should be needed parinly - eg an infrequen tperot
Scans thorugh all items in a table and the nreturns one or more items thourhg gfilters
By defaul, t this return s all attibutes for  every itme - use ProjectExpression to Limit
Scans are equential, you can speed up a scan thourgh parallel scans using Segmnets and Total Segments
Scan scan be slow, especially with bvery large tables and acan easily cnsume your provisioned thourghpti
Scana are one of the most expensive ways to acacess data in DynamoDB

Quyery
- Find items based on primary key values
- Table mus have a composite ey in order to be abel t o query
- By defaul,t queireis are eventualy consistent - use ConsistendRead = True to change to Strongly Consistetn
- By defualt, returns all artribute for each item found by a query - use ProjectExpressio nto lomit
- By default, is sorted asceding , useScanINdexFOrmatwtf to False to reverse order to descecing

DynamoDB has two capacity modes: Provisioned and On-Demand
You can switch between these moeds once eveyrr 24 hors
Provisioned THroughput Capacity is the maximum amount of cacpaity your application is allwoed to read or write per second from a table or index
- pRovisioned is suited for predictbale or staead sstate workloads
- RCUs is Read Capacity Unit
- WCUs is Write Capacity Unit
- You should eneable auto sacling with Provisioned capacity mode
- In this mode you set a floor and celig for hte capcait you wis h the table to support
- DYnamod DB will automatcially add and remove acapciaty t o betwen these values aon your behald and throlle calsl that go aboue ce the ceiling for too long
- If you go beond your proeviiosla capacity, you'lld fet an exception - ProvisionedTHorugputExceededException (throttleing_
- THrottleing is when reuqests are blocked due to read of rwirte freeuce higher than set threshols
- EG, exceeding set sprovision capaicty, patiroints plitting ,table and index capacity mismatch
- )

On_Demand Capacity is pay per requst - only pay for aht you sue
- ON-Deand is suioted for new or unpredictable qworklsoads
- the throughpuit is only imited by the deafult uppler limits for a table (40K RCUs and 40K WCUs)
- Throtltlign can acocur if you exceed fouble your previous peak capacity (high water mark ) within 30 minutes, EG, if you prevousl peaked to a capacity of a maximum of 30,000 ops/sec, you coul d not peak immesitalye to 90,000 ipos/sec, but you could up to 60,000 opsx/sec
- Since there isno hard limit On-Demand coul bdecme veruy expensive based on emerging escanearios

Calculating Reads
- A read capacity unirt represnts: one strongly consisten read per second, or two evenulay consistent reads per second, for a n items up to 4KB in size
- How to calcualte RCUS for strong
- - round data up to nearest 4
- Dviide data by 4
- Times by numner of rearsd
- How to calcualte RCUs for eventual
- - round data up to neares t 4
- dvicie dby four
- multiple by numner of reads
- divide final number by 2
-  roun up the neatest integer

  Calcaulkting Writes (Writes)

  A write caaapcaity unit represents - one write per second for an itme up to 1 KB
  How to calulcaute Writes
    round data up to neares 1
    times by number ofwrites

DynamoDB Acceleraotr (DAX) is a filly managed in oemero write thourhg vahve fgor DynmaoDB that runs in a cluster
- reads are eventually consistent
- Icnoming requests are evently dsitrbued across al l the noeds in the clasuer
- DEX can reduce read respoinse times to microseconds
- DAX is ideal for
  - - dfastes repsonse times possible
  - apps that read a small numner of itmes more requentyl
  - apps that are read itneansvie
- DDAX is not aidela ofrcreatesd a new item or replaces an otld itme iwht the new itme - if the aitme has the same primary key as the inew aitem already iexists, the nrw is tem repalces the ei
  - aps that require strongly conisitn reasd
  - apps that do not rquire
  - Apps that are writ intensive or that do not performm uch read acitivet
  - Id you don;;t use DAX, use ElasticACehe

Dynamo DB notable commands (API) command using teh CLI eg. `aws dynamodb <command>`
- getitme returns a asetr of attirbutes for the item with the givien priamruy key - if notr matching itme, then it odeos not reutn any data and whether will be no ITem elemtni n hte reposnse
- put-item: repalces
- update-item - edits an exiitng items atributes oor adds a new irtem sot the table it if it does not already exist
- bartch-get-tiem reutnrs the atrirbutes of one or more items from one or m,ore tales. You identiyf request itms by preiamryu key. A single oparion can retice up to 116MB of adata which can tontain as many a 100 items
- Batch-write 0item puts orde letes multiple itesm in mone more tables. Can rrite up oti 16 MB of datra whch ahcan comprsie as many as 25 put or delet request.s Inivuals iutems to be weititen ca n be as large oas 400KB
- create-rable adds a new tbale to you accout, table names must be uniqeu wihit neach reion
- update-table mosdified the proviosnthou hhrpt settings, global secondary index, or Dynamo DB streams stetings for a given table
- delete-table opeariont deletes at able and all of its itmes
- transact-get-items is a synchtonmous operaton that automatclaly retiteves muliple items from one of more abtale (not nnot from index) in a single account and Region. Calll can contain up to 25 objec.s THe arggretate size of hei mes in the transaction cannotu exceed 4 MB
- RTanscane crite iitems - a synchitnouos rwoite operatio hat groups up to 25 action reques. These acitons can tagert items in deififenr tbales, bt not deifferetnAWS accounts or REgions and no rtao actions can tager the same item.
- Qeur finds items nased onpriamry ke vluaes. You can quyer table or secondart index taht has a coipomsitie primatr key.