# Secrets Manager

Automatic Rotation = main benefitt for databse
rotate interaval
Creteaate Lambda fuction perfotm rotation
aws secretsmanager describe-0-secret --secret-id

get-secret-value

Stores password in RDS

```mermaid
graph LR
SM[Secrets Manager]-->Lambda-->RDS

WA[Web App in EC2]-->|Web Server uses password<br/>to form connection URL|RDS
WA-->|Web Server uses AWS SDK to get database credentials|SM

Developer-->|Uses a database manager to connect to a Database|RDS
Developer-->|Uses AWS CLI to obtain database credentials|SM
```