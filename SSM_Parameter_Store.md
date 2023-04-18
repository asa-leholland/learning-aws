# SSM Parameter Store
Secure hieracrchical storage for configuration data management and secrets management

Can store sadata lsuch as passwors d, data base stirings, and license codes as apaartametes values
Strore confuigraiton data nas secure strings in hieracrthices and trac versions
You can encrypt parametrs usng KMS

Parametrrs
create hierarcriehies uing /prod/application.CLOUDFORNT_KEY_PAIR
ca n select a tier:
- Standard Tier - cup to 10,000 parameters, parameter value size p t o4 Kb, parameter pokicies are not availebl  - no additonal charg
- - Advance d tier - can creat emore than 10,000 aramters, parameters cvlue size up 8kb
- Paramter polcieis are available
- Cahrges apply
-

- String - just a string

- StringList comma seaapretd string
- Secure String - ecnrypres tring using KMS


## PRicign and Parameter Tiers
                                Standard        Advances
Number of params / region           10,000      100,000
Max size of param value             4KB`        8KB
Paramter Policies                   No             Yes
Cost                                Free        $0.05 per parametert . month

You cna conver ta stranadrd parameter to an advanced parameter to any time, bu tyou cannot rever a n advanced parameter to an standard parameter


## Paramter Policies
Force you to update or delete passwords
eonly availble to advanced tier of Parameter Store

Using Asycnthonoeus periodc dacans - after you create a policy tyou don't need to performa dddiotnla actions to enforce the policy
 Can assign multiple policies to a paramter

 Policy Types
  - Expiratrion - this polci cdeletes ahe parameter afgter a speicifed adata n dtime

ExpirationNortticioant - this plocy treggirs an event in AmazonCloud QWathc evnets that notifies you about eupcoing expirtion
NoChangeNotificaiton
- this policy treiigers a enve in Cloud Wathc if a paramter hjas not been modifed for a spricie period of time
- This poluc tpe is uysed when a developer apsserpn eeds t obe change with in a paeiodo ftime


### CLI Example

`aws ssm put-parameter --name "/plantes/vulcan/population"      --value 4.9B --type String
aws ssm put-parameter --name "/.planter/vucan/grabity"      -value 1.4G --type String
`aws ssm put-parameter --name "/plantes/vulcan/classifaication"     --value M       --type Strign

this sets Version: 1 before any edits


`aws ssm get-paramaeters-by-path --path /planets/vulcan` tou output all parameters for a CLI hierarycghy