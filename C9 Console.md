# C9 Console

## Opening Ports

To open ports for an Elastic Beanstalk application, you will need to use the following base:

1. Open C9
2. Know `curl -s http://169.254.169.254/latest/meta-data`

### Getting Mac Address

1. run `curl -s http://169.254.169.254/latest/meta-data/mac`

### Use Mac Address to get Security Group IDs

1. Run `curl -s http://169.254.169.254/latest/meta-data/network/interfaces/macs/<Your MAC address>/security-group-ids` to get Security IDs

### Get your IP address
In a new tab, open
<http://checkip.amazonaws.com/>

### Open Ports

Finally Run the following command for each security group (I think):

` aws ec2 authorize security-group-ingress --group-id <SECURITY GROUP ID> --port 8080 --protocol tcp --cidr <IP ADDRESS>/32 `

Example:
 `aws ec2 authorize security-group-ingress --group-id sg-00b2b2897fb3f318 --port 8080 --protocol tcp --cidr 169.234.230.142/32`

`/32` means only one IP address in the CIDR block


### Check that Ports are Open

Run `aws ec2 describe-security-groups --group-ids <SECURITY GROUP IDS> --output text --filters Name=ip-permissions.to-port,Values=8080`

Example:
`aws ec2 describe-security-groups --group-ids sg-00b2b2897fb3f318 --output text --filters Name=ip-permission.to-port,Values=8080`
This defaults to JSON which is hard to read, so its text
Describe all the SEC GROUPS, and only filter this IP, only inbound rules that have port 8080

# This might not be working