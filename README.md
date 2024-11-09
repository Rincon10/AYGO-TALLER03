# AYGO-TALLER03

## AWS-CLI Workshop: Creating an EC2 Instance

In this workshop, you will learn to use **AWS-CLI** to create an **EC2 Instance**.

## Prerequisites

1. Install the `aws-cli` application.
2. Configure the `aws-cli` application:


~/.aws/credentials, segun las credenciales que le de AWS, estas se crean con el aws configure
```bash
$ aws configure
```

```bash
AWS Access Key ID [None]: AKIAIOSFODNN7EXAMPLE
AWS Secret Access Key [None]: wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
Default region name [None]: us-west-1
Default output format [None]: json
```

y despues nos vamos a modificar el archivo creado y le agregamos la configuracion que nos de aws

el crea el archivo en la ruta del usuario que ejecuto la configuracion, en mi caso fue

```bash
C:\Users\camil
```

modificamos el archivo
```bash
vi .aws/credentials
```
y le agregamos las crendiciales que nos de aws

```
[default]
aws_access_key_id=TEST6X3AYTEST
aws_secret_access_key=TEST/04KE+qRQHkD/TEST
aws_session_token=TEST//////////TESTxHJA5WWTuzuF+4kgAHweuaqoZMPzMGYte5AxQDsdEI2pS8NjlvLIZ9GZWL0TRnimA1jC5tL25BjqeAerUu1nMcMn2LKCROuQYu6z9vMkjRjTekiVEXA13gYbmvzEOvhvm9N4+oRYWLbKqch+kbuBoK7Ckg/KJB9KskJZ0tebvqTEST/pU
```





## Step 1: Create a Key Pair for EC2

```bash
% aws ec2 create-key-pair --key-name MyKeyPair --query 'KeyMaterial' --output text > MyKeyPair.pem
```