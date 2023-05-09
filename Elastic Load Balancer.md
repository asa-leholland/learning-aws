# ELB
Distrbutes inco,ming application traffic across multiple targets, such as EMaaon EC2 isntances, container, IP adreeses and lmLambda functions

Load Balancaers can be phyusical hardware or veirtal software that accepts incoing traffic and then ditibutes the traffic to multiple atragets. Thjey can balance the load via ifferent rules. THes reuls vary basedo n ttpes of load balancers.

Elastic Loadb Blancer (ELB) is the AWS oslutoin for laod balancing rraggic and there are three types availblae

1. Application Load Balancer (ALB) Http/https
2. Network Load Balancer (NLC (TCUP./UDP)
3. Classic Load Valabcver (CLB (GLEagyc))
   )

ELB Flow of Traffic

Listenrs: Incoming rtfffic isavaluatioed against listeners. Listenrers evaliuarte any tarifci hat matcehs the lisners; port. FGOr classic load balancer, EC2 instances are firetelsy regiesrterd toh teh Load Blancer

Rules: Not aavialebl tofr clasisc lOad balacner
Listenre witll the n invotke rules to fevciwhat to do twith the taggiv. Generalyl next tsp is tforawrd traggfic to a Target Grouop
Traget Gotups (not availabel  for aCLassic load aacalncer_
EC @ inane are regersteted as tagets to a a Targert Grou]



## Examples
For APlication Load Blanacer (ALB) or Netwrok Load Balancer (NLB) traffic is sent to the Lisnterrs
When a port patcehs it when tchecks the turles for what to do
Rules will fowrare rtafiic to a Ragert Torup
Target Group will evnely fistrinute traffic to isntances regiesreted o the at Target Group


Rules are only availbel on ALB

Classic Load Balncers - CLB traffic is sent to the lInsterns. WHen the port matches it hten it forwardf othe traffic to any EC2 insanvce hat are resgitered t ohte Classci Load Balnace.r CLB does not allw you to apply tules o lineserte.


app.examplro.co -> Route53 -> CLN -> set up Lisnteres - no Target Groups

Application Load Balancer
desigend ato balance HTTP and HTTPS traffic
Opeartes in Applcaiton layer (Layer 7) of OSI Model

ALB has a feature called Request Routing which allwos you to add routing rules to your liseners based on HTTP protocl

Web Application Firewall (WAF) can be attached to ALB

Great for WEb Applications

OSI Layers
Layer 7 Applcaiton
Layer 6 Presentation
Layer 5 Session
Layer 4 transport
Layer 3 Netork
Layer 2 Data LInk
Layer 1 Pbysical

Network Load Balancer

Designed to balance TCP/UDP
THey operate at Layer 4 of the OSI Model

Can handle millions of requests per second hile still mainaitaine extermely olow latency
Can perform Vrozz Zone load balcning
Grear t for Multilae yt Video Games or whe nnetwork performace nsi critical


(Layer 4 Transport)


Classci Load Balncer

It was WAWS first Laod balncer (legacy()

Can balnce HTTP, HTTPS or TCP tragffic not at the tsame time

Ut can use layer 7 features (OSI model) such as sticky suessions
It can also use strict layer 4 (OSI ) balnceing for purely TC aplcations

Can perform Vross Zone Load Balncaing

It will repsonf with a 504 erro r(timeout) id the underlyung applciatoin is mot repsonfing (at the web servefr or databale eel)

Not recomended for use, use NLB or ALB instead



Stick ySessions
Advanced LodbALncing Method
Binds a user session to a specific ec2 instance

Ensure s that all requests from tnat session are sent to the same isntance
Typically utrilzied with a Calssicc Load balancer

Can be enabeld for AL:B thoug hcan only be se ton a Target Gorup not individal EC2 instances

Cookeis are used to remember which EC2 instnace

USeful sheen speicif information is only stroed lcoally on a single instanecv

User requesting a IPV4 address, check the X-Forwwarfef -For Heaeder

The XX_FOrwarde -For XFF header is a commnd method for identifying the origination IP affrress of a client connection o a web server though an HTTP proox y or a load balncer

ELB Helath CHecks

Instance sathat are monitored by the ELB report back Health CHecks as InService or OutOfServies

Helaht Checks communciate directly with the instace to deteminr its state

ELB does not terminate (kill) unhealth instance, it will jsut refiret traffic to healthy intstnaces


FOR ALB an NLB the ehalth checks are found on the Ratareg Toup


ELB does not Terminate unhealht instances, it jus reitreects

Cross Zone Load Balancing
Only for Clasic and Network Load Blancer


Crozz Zone Load Balncing Enabled
requests are distribued evenly across the instance in all aenabled Abailableilt Zones



Cross Zone Load Blancing Disabled
requests are dsibitrubed evenly across the insatnce in only its Availablileit Zone

Request Routing

Allows you to apply ruels to incoming reques and the nforward or redirect tarfic

Host Header
Source IP
Path
Htp Headter
Hettp Header MEhtod
QUeyr String



ELB Cheet Sheet
There are three Elastic Laod Balncers: Network, Applcaiton and Classic Load Balancer
A elasti c load balcner must have eat least two Availabeility Zones
ELastic Load lbalcners cannot go cross -regions, you misut create one per region
ALB has Listeners Rulees and tRaget Gorups to trorue traffic
BLC uses Listeners anTarget Gorusps to route traffic
CLB uses Listeneres and EC@ isntance sare firectly registerd as targes to CLB
APplcaiton Load BLancer is for HTTP(S) trafgfic and the name impelis it si foog for Wb APplciaitons
Network Laoba aVClansre is ofr TCP .UP wjhcis is gfoos fort high netwrok thoruhput ec cideo games
Classci lOaf balncer is legacuy and it no recommended
Use XForwaded For CFF to get original IP of cinomicnig raggic passing thorug EB
Yopu can attach Web Applciation Girwaall (WATF) ot ALB but not to NL Bor CLB
You can attache Amazon CVerrtiticaiton Mansager SSL to any of hte ELast ic Laod Blancers for SSL
ALB has davneae Request Reouting Rules whre yio uca nroute basedo nsubfomain header, path and potter JTTPS oiformation
Sticke t sessions cam ne esnaned for CLNB or ALB adn sessions are re,em,nereed vaia coker