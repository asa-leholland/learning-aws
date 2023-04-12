# Key Management Service
KMS

KMS makes it easy for you to create, control and rotate encryption keys used to encrypt youre data on AWS
Multi_Tenatnt - Hardware Security Module (MSM)

Most AWS servieces can just check a checkbox that says "Encryption" and choose a KMS key to encrypt the volume

KMS can be used to with CloudTrail to audit access histroyt

- this can be used to determine who did what with waht key


Key services that KMS integrates with: RDS, CodeCommit, S3, CodeDeploy, Galcier, SNS, SQS, DynamoDB, EC2, X-Ray, ElastiCache, and CodeBuild
Hardware Security Module
- designed to be stored in memory
- designed to be tamper proof
- hardware that is specialized to store encryption keys

Multi_Tenant - allows multiple customers to use the same piece of hardware
Customers are isoalted from each other virtually
If one customer used all the pieces of hardware (aka a dedicated usage) thius would also be called single-tenant
- KMS is only FIPS 140-2 Level 2


# CloudHSM
This is AWS' single tenant HSM which gives you full control
Dedicated HSM (single tenant) means you can meet stricter compliance
FIPS 140-2 Level 3


## CloudHSM is more for enterprises that need to meet regulations


## Customer Master Keys (CMKs)

Encryption - process of encoding a message or information in such a way that only authorized parties can access it

Cryptographic key (aka data key) - string of data used to lock or unlock crypopgraphic functions (authentication, authiraztion and encryption)

Master Key - stored in secure hardware to encrypt all other keys in system

Envelope Encryption - the act of using a Master Key to encrypt Data KEys that are used ton encrupt data

KMS primarily manages logical represeantion of the master keys

CMK includes metadata such as key ID, creation date, descripotion and key state

CMK contains the jey material sued to encfrript ./ descrypt data

### AWS KMS supports symmetric and asymmetric CMKs

Symmetric Key
A 256-bit key that is used for encryption and decryption - uses one single key

Example would be encrypting an S3 bucke tusing AES 256

Asymmetric Key
is a pair of RSA keys that is used for encryption and decryption OR signing and verifcation (but not both)
One Key pair, IE, public and private
EC2 key paris used to SSH into a server

## Generally - Symmetric key (1 key) is less secure than Asymmertric (2 key pair)

## Core CLI Commands

`aws kms create-key`:   create unique CMK in your AWS account and region
`aws kms encrypt`:      encrypt plaintext into ciphertext by using a customer amster key
`aws kms decrypt`:      decrypt ciphertextthat was encryptied by an AWS KMS customer master key (CMK)
`aws kms re-encrypt`    decrypt ciphertex and re-encryt wutgub AWS KMS (manually rotate a CMK, change CMK that protects a ciphertext, change encryption content of cycphertext)
`aws kms enable-key-rotation`   enables automatic toration of the key material for the specified symmetric customer master key (CMK). You canno t perform this operation on a CMK in a differenet AWS account


Key management service (KMS) creates and manages encryption keys for AWS Services
Key Management serveice (KMS) can be used with ClouddTrail - to trqck who made changes with what key (key access history)
KMS has the ability to automatically rotate out keys every year with no need to re-encrypt
Customer Master Keys - CMKs are primarty resources on KMS
KMS is multi-tenant HSM
multi-tenant means you are sharing hardware with multiple custoemr
Hardware Security Module (HSM) is a specialized hardware for storing keys and is tamper proof
CloudHSM is FIPS Level 3 (more secure)
KMS stores Master Keys (not data keys)
Envelope Encryption - master keys used to encrypt data keys using Master Keys
KMS supports two types of keys symmetric and asymmetric
    - symmetric = isngle key using 256 bit encryption
    - S3 buckey
  - Asymmetric uses two keys (pblucli and private)
  - aws kms create-key - creates a key
  - aws kms encrypt- encrpy a key
  - aws kms decrypt
  - aws kms re-encrypt - for manuafllay rotating CMK (customer master key, change CMK that protects ciphertext or change encryption content of cycepher text)
  - aws kms enable-key-rotation -  turn on automatic key rotationg for symmetric keys and same user
  -