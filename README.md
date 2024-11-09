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
Default region name [None]: us-east-1
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

y verificamos el archivo config deberia quedar asi

```
[default]
region = us-east-1
output = json
```

podriamos correr el siguiente comando, para ver las instancias de ec2

```bash
aws ec2 describe-instances
```

y deberiamos ver algo asi 

```json
{
    "Reservations": [
        {
            "Groups": [],
            "Instances": [
                {
                    "AmiLaunchIndex": 0,
                    "ImageId": "ami-06b21ccaeff8cd686",
                    "InstanceId": "i-0889cdf516330be26",
                    "InstanceType": "t2.micro",
                    "KeyName": "vockey",
                    "LaunchTime": "2024-11-09T12:48:54+00:00",
                    "Monitoring": {
                        "State": "disabled"
                    },
                    "Placement": {
                        "AvailabilityZone": "us-east-1b",
                        "GroupName": "",
                        "Tenancy": "default"
                    },
                    "PrivateDnsName": "ip-172-31-90-245.ec2.internal",
                    "PrivateIpAddress": "172.31.90.245",
                    "ProductCodes": [],
                    "PublicDnsName": "ec2-3-83-25-106.compute-1.amazonaws.com",
                    "PublicIpAddress": "3.83.25.106",
                    "State": {
                        "Code": 16,
                        "Name": "running"
                    },
                    "StateTransitionReason": "",
                    "SubnetId": "subnet-05b45d879859dcab9",
                    "VpcId": "vpc-00f7f6906b7fc65e0",
                    "Architecture": "x86_64",
                    "BlockDeviceMappings": [
                        {
                            "DeviceName": "/dev/xvda",
                            "Ebs": {
                                "AttachTime": "2024-10-26T03:03:24+00:00",
                                "DeleteOnTermination": true,
                                "Status": "attached",
                                "VolumeId": "vol-0def00f10d0739d62"
                            }
                        }
                    ],
                    "ClientToken": "2ce656ed-bfa4-4c31-a3b1-53f3837074b6",
                    "EbsOptimized": false,
                    "EnaSupport": true,
                    "Hypervisor": "xen",
                    "NetworkInterfaces": [
                        {
                            "Association": {
                                "IpOwnerId": "amazon",
                                "PublicDnsName": "ec2-3-83-25-106.compute-1.amazonaws.com",
                                "PublicIp": "3.83.25.106"
                            },
                            "Attachment": {
                                "AttachTime": "2024-10-26T03:03:23+00:00",
                                "AttachmentId": "eni-attach-049e6e9c1c5f722ae",
                                "DeleteOnTermination": true,
                                "DeviceIndex": 0,
                                "Status": "attached",
                                "NetworkCardIndex": 0
                            },
                            "Description": "",
                            "Groups": [
                                {
                                    "GroupName": "launch-wizard-2",
                                    "GroupId": "sg-013c104ab2008aa01"
                                }
                            ],
                            "Ipv6Addresses": [],
                            "MacAddress": "12:36:67:a9:4c:77",
                            "NetworkInterfaceId": "eni-07610435b0f7201c1",
                            "OwnerId": "134744162619",
                            "PrivateDnsName": "ip-172-31-90-245.ec2.internal",
                            "PrivateIpAddress": "172.31.90.245",
                            "PrivateIpAddresses": [
                                {
                                    "Association": {
                                        "IpOwnerId": "amazon",
                                        "PublicDnsName": "ec2-3-83-25-106.compute-1.amazonaws.com",
                                        "PublicIp": "3.83.25.106"
                                    },
                                    "Primary": true,
                                    "PrivateDnsName": "ip-172-31-90-245.ec2.internal",
                                    "PrivateIpAddress": "172.31.90.245"
                                }
                            ],
                            "SourceDestCheck": true,
                            "Status": "in-use",
                            "SubnetId": "subnet-05b45d879859dcab9",
                            "VpcId": "vpc-00f7f6906b7fc65e0",
                            "InterfaceType": "interface"
                        }
                    ],
                    "RootDeviceName": "/dev/xvda",
                    "RootDeviceType": "ebs",
                    "SecurityGroups": [
                        {
                            "GroupName": "launch-wizard-2",
                            "GroupId": "sg-013c104ab2008aa01"
                        }
                    ],
                    "SourceDestCheck": true,
                    "Tags": [
                        {
                            "Key": "Name",
                            "Value": "back"
                        }
                    ],
                    "VirtualizationType": "hvm",
                    "CpuOptions": {
                        "CoreCount": 1,
                        "ThreadsPerCore": 1
                    },
                    "CapacityReservationSpecification": {
                        "CapacityReservationPreference": "open"
                    },
                    "HibernationOptions": {
                        "Configured": false
                    },
                    "MetadataOptions": {
                        "State": "applied",
                        "HttpTokens": "required",
                        "HttpPutResponseHopLimit": 2,
                        "HttpEndpoint": "enabled",
                        "HttpProtocolIpv6": "disabled",
                        "InstanceMetadataTags": "disabled"
                    },
                    "EnclaveOptions": {
                        "Enabled": false
                    },
                    "BootMode": "uefi-preferred",
                    "PlatformDetails": "Linux/UNIX",
                    "UsageOperation": "RunInstances",
                    "UsageOperationUpdateTime": "2024-10-26T03:03:23+00:00",
                    "PrivateDnsNameOptions": {
                        "HostnameType": "ip-name",
                        "EnableResourceNameDnsARecord": true,
                        "EnableResourceNameDnsAAAARecord": false
                    },
                    "MaintenanceOptions": {
                        "AutoRecovery": "default"
                    }
                }
            ],
            "OwnerId": "134744162619",
            "ReservationId": "r-0ed516336c5d0f4b6"
        },
        {
            "Groups": [],
            "Instances": [
                {
                    "AmiLaunchIndex": 0,
                    "ImageId": "ami-06b21ccaeff8cd686",
                    "InstanceId": "i-09770df9761550ba5",
                    "InstanceType": "t2.micro",
                    "KeyName": "vockey",
                    "LaunchTime": "2024-11-09T12:48:54+00:00",
                    "Monitoring": {
                        "State": "disabled"
                    },
                    "Placement": {
                        "AvailabilityZone": "us-east-1c",
                        "GroupName": "",
                        "Tenancy": "default"
                    },
                    "PrivateDnsName": "ip-172-31-18-225.ec2.internal",
                    "PrivateIpAddress": "172.31.18.225",
                    "ProductCodes": [],
                    "PublicDnsName": "ec2-3-92-32-196.compute-1.amazonaws.com",
                    "PublicIpAddress": "3.92.32.196",
                    "State": {
                        "Code": 16,
                        "Name": "running"
                    },
                    "StateTransitionReason": "",
                    "SubnetId": "subnet-0166043168b82a710",
                    "VpcId": "vpc-00f7f6906b7fc65e0",
                    "Architecture": "x86_64",
                    "BlockDeviceMappings": [
                        {
                            "DeviceName": "/dev/xvda",
                            "Ebs": {
                                "AttachTime": "2024-10-24T03:42:31+00:00",
                                "DeleteOnTermination": true,
                                "Status": "attached",
                                "VolumeId": "vol-0437ae44a71267f85"
                            }
                        }
                    ],
                    "ClientToken": "59b4d08b-7d99-4cb9-af41-933fbbcfdd05",
                    "EbsOptimized": false,
                    "EnaSupport": true,
                    "Hypervisor": "xen",
                    "NetworkInterfaces": [
                        {
                            "Association": {
                                "IpOwnerId": "amazon",
                                "PublicDnsName": "ec2-3-92-32-196.compute-1.amazonaws.com",
                                "PublicIp": "3.92.32.196"
                            },
                            "Attachment": {
                                "AttachTime": "2024-10-24T03:42:31+00:00",
                                "AttachmentId": "eni-attach-025f149eb6043e012",
                                "DeleteOnTermination": true,
                                "DeviceIndex": 0,
                                "Status": "attached",
                                "NetworkCardIndex": 0
                            },
                            "Description": "",
                            "Groups": [
                                {
                                    "GroupName": "launch-wizard-1",
                                    "GroupId": "sg-0157b02a2ba85e73a"
                                }
                            ],
                            "Ipv6Addresses": [],
                            "MacAddress": "0a:ff:f9:35:81:19",
                            "NetworkInterfaceId": "eni-06dc0e5919fd4a8c8",
                            "OwnerId": "134744162619",
                            "PrivateDnsName": "ip-172-31-18-225.ec2.internal",
                            "PrivateIpAddress": "172.31.18.225",
                            "PrivateIpAddresses": [
                                {
                                    "Association": {
                                        "IpOwnerId": "amazon",
                                        "PublicDnsName": "ec2-3-92-32-196.compute-1.amazonaws.com",
                                        "PublicIp": "3.92.32.196"
                                    },
                                    "Primary": true,
                                    "PrivateDnsName": "ip-172-31-18-225.ec2.internal",
                                    "PrivateIpAddress": "172.31.18.225"
                                }
                            ],
                            "SourceDestCheck": true,
                            "Status": "in-use",
                            "SubnetId": "subnet-0166043168b82a710",
                            "VpcId": "vpc-00f7f6906b7fc65e0",
                            "InterfaceType": "interface"
                        }
                    ],
                    "RootDeviceName": "/dev/xvda",
                    "RootDeviceType": "ebs",
                    "SecurityGroups": [
                        {
                            "GroupName": "launch-wizard-1",
                            "GroupId": "sg-0157b02a2ba85e73a"
                        }
                    ],
                    "SourceDestCheck": true,
                    "Tags": [
                        {
                            "Key": "Name",
                            "Value": "api-gateway"
                        }
                    ],
                    "VirtualizationType": "hvm",
                    "CpuOptions": {
                        "CoreCount": 1,
                        "ThreadsPerCore": 1
                    },
                    "CapacityReservationSpecification": {
                        "CapacityReservationPreference": "open"
                    },
                    "HibernationOptions": {
                        "Configured": false
                    },
                    "MetadataOptions": {
                        "State": "applied",
                        "HttpTokens": "required",
                        "HttpPutResponseHopLimit": 2,
                        "HttpEndpoint": "enabled",
                        "HttpProtocolIpv6": "disabled",
                        "InstanceMetadataTags": "disabled"
                    },
                    "EnclaveOptions": {
                        "Enabled": false
                    },
                    "BootMode": "uefi-preferred",
                    "PlatformDetails": "Linux/UNIX",
                    "UsageOperation": "RunInstances",
                    "UsageOperationUpdateTime": "2024-10-24T03:42:31+00:00",
                    "PrivateDnsNameOptions": {
                        "HostnameType": "ip-name",
                        "EnableResourceNameDnsARecord": true,
                        "EnableResourceNameDnsAAAARecord": false
                    },
                    "MaintenanceOptions": {
                        "AutoRecovery": "default"
                    }
                }
            ],
            "OwnerId": "134744162619",
            "ReservationId": "r-0e70c2fa029b9ca8d"
        }
    ]
}

```

## Step 1: Create a Key Pair for EC2

```bash
aws ec2 create-key-pair --key-name MyKeyPair --query 'KeyMaterial' --output text > MyKeyPair.pem
```
o el siguiente

```bash
aws ec2 create-key-pair --key-name MyKeyPair --query 'KeyMaterial' --output text | Out-File -Encoding ascii MyKeyPair.pem
```

Verify the key pair file:

```bash
ls
```

```bash
% ls
MyKeyPair.pem
```


Make the private key readable only by you

```bash
chmod 400 MyKeyPair.pem 
```

Check the fingerprint

```
aws ec2 describe-key-pairs --key-name MyKeyPair
```

y veriamos algo de la siguiente forma 

```json
{
    "KeyPairs": [
        {
            "KeyPairId": "KeyPairId",
            "KeyFingerprint": "KeyFingerprint",
            "KeyName": "MyKeyPair",
            "KeyType": "rsa",
            "Tags": []
        }
    ]
}

```

incluso podemos verificar, que en nuestra cuenta de aws

![alt text](docs/img/01.png)

![alt text](docs/img/02.png)

## Second Step: Create a Security group

Before proceeding check for VPCs configured in your account

buscamos en aws el servicios de VPC


VPC es el servicio de seguridad que necesitaremos para configurar, el security group y ademas de una subred (cualquiera)


los grupos de seguridad son como los firewalls.


importante ir guardando el id del vpc, subred y del security group

```bash
aws ec2 create-security-group --group-name <my-sg-cli> --description <"My security group"> --vpc-id <vpc-xxxxxxxx>
```

para mi caso voy a usar los mismos nombres

sacando el id del vpc aqui

![alt text](docs/img/03.png)

```bash
aws ec2 create-security-group --group-name my-sg-cli --description "My security group from cli" --vpc-id vpc-00f7f6906b7fc65e0
```

si todo salio bien veremos nuestro security group en aws

![alt text](docs/img/04.png)

o por consola List security groups


```bash
aws ec2 describe-security-groups --group-ids <idSecurityGroup>
```

en mi caso seria 

```bash
aws ec2 describe-security-groups --group-ids sg-06345f49b2c8310af
```

Now we are going to assign access permissions to the security group. We are not going to restrict access by IP address. However, you could use the following command to check your public IP address and use it to make a more restricted version of the example.

este comando solo nos dice la direccion ip de la cual estamos accediento a amazon
```bash
curl https://checkip.amazonaws.com
```

respuesta
```
186.96.109.58
```

NOTA: para el ejemplo colocaremos 0.0.0.0 para dar permisos de acceso a todo el mundo, pero si  quisieramos limitarlo a solo nosotros colocaremos la ip otorgada por el anterior comando

Add a permission to the security group:

```bash
aws ec2 authorize-security-group-ingress --group-id <group-id> --protocol tcp --port <port> --cidr <direccion-ip>
```

en mi caso seria 

```bash
aws ec2 authorize-security-group-ingress --group-id sg-06345f49b2c8310af --protocol tcp --port 3389 --cidr 0.0.0.0/0
```

response 

```json
{
    "Return": true,
    "SecurityGroupRules": [
        {
            "SecurityGroupRuleId": "sgr-009ec73c3cd86aea8",
            "GroupId": "sg-06345f49b2c8310af",
            "GroupOwnerId": "134744162619",
            "IsEgress": false,
            "IpProtocol": "tcp",
            "FromPort": 3389,
            "ToPort": 3389,
            "CidrIpv4": "0.0.0.0/0"
        }
    ]
}
```

Now you can check the security group

```bash
aws ec2 describe-security-groups --group-ids <security-id>
```

en mi caso es 

```bash
aws ec2 describe-security-groups --group-ids sg-06345f49b2c8310af
```


Add a permission for ssh connections, the port must be 22 to ssh cone:

```bash
aws ec2 authorize-security-group-ingress --group-id sg-06345f49b2c8310af --protocol tcp --port 22 --cidr 0.0.0.0/0
```

## Third Step: Create the instance

Before creating the instance check for a subnet configured in your account. 

Create a t2.micro instance using the ami-032930428bf1abbff ami:

para sacar el ami nos dirigiremos a aws y simplemente copiaremos el id de la ami asi:

![alt text](docs/img/05.png)

la subnet sale del vpc

```bash
aws ec2 run-instances --image-id <ami-032930428bf1abbff> --count 1 --instance-type t2.micro --key-name MyKeyPair --security-group-ids <sg-01f4c77b81e9dc434> --subnet-id <subnet-1175cf1d>
```
en mi caso es

```bash
aws ec2 run-instances --image-id ami-063d43db0594b521b --count 1 --instance-type t2.micro --key-name MyKeyPair --security-group-ids sg-06345f49b2c8310af --subnet-id subnet-026505a0219cd4314
```

Check that you can connect to the server

```json
{
    "Groups": [],
    "Instances": [
        {
            "AmiLaunchIndex": 0,
            "ImageId": "ami-063d43db0594b521b",
            "InstanceId": "i-0a07f73ff949f1831",
            "InstanceType": "t2.micro",
            "KeyName": "MyKeyPair",
            "LaunchTime": "2024-11-09T13:45:18+00:00",
            "Monitoring": {
                "State": "disabled"
            },
            "Placement": {
                "AvailabilityZone": "us-east-1e",
                "GroupName": "",
                "Tenancy": "default"
            },
            "PrivateDnsName": "ip-172-31-53-147.ec2.internal",
            "PrivateIpAddress": "172.31.53.147",
            "ProductCodes": [],
            "PublicDnsName": "",
            "State": {
                "Code": 0,
                "Name": "pending"
            },
            "StateTransitionReason": "",
            "SubnetId": "subnet-026505a0219cd4314",
            "VpcId": "vpc-00f7f6906b7fc65e0",
            "Architecture": "x86_64",
            "BlockDeviceMappings": [],
            "ClientToken": "f5eebe12-435c-446e-be76-6efd9cd300db",
            "EbsOptimized": false,
            "EnaSupport": true,
            "Hypervisor": "xen",
            "NetworkInterfaces": [
                {
                    "Attachment": {
                        "AttachTime": "2024-11-09T13:45:18+00:00",
                        "AttachmentId": "eni-attach-032d571769e66009c",
                        "DeleteOnTermination": true,
                        "DeviceIndex": 0,
                        "Status": "attaching",
                        "NetworkCardIndex": 0
                    },
                    "Description": "",
                    "Groups": [
                        {
                            "GroupName": "my-sg-cli",
                            "GroupId": "sg-06345f49b2c8310af"
                        }
                    ],
                    "Ipv6Addresses": [],
                    "MacAddress": "06:35:6a:0f:e2:33",
                    "NetworkInterfaceId": "eni-07f3f3285fc3e2b80",
                    "OwnerId": "134744162619",
                    "PrivateDnsName": "ip-172-31-53-147.ec2.internal",
                    "PrivateIpAddress": "172.31.53.147",
                    "PrivateIpAddresses": [
                        {
                            "Primary": true,
                            "PrivateDnsName": "ip-172-31-53-147.ec2.internal",
                            "PrivateIpAddress": "172.31.53.147"
                        }
                    ],
                    "SourceDestCheck": true,
                    "Status": "in-use",
                    "SubnetId": "subnet-026505a0219cd4314",
                    "VpcId": "vpc-00f7f6906b7fc65e0",
                    "InterfaceType": "interface"
                }
            ],
            "RootDeviceName": "/dev/xvda",
            "RootDeviceType": "ebs",
            "SecurityGroups": [
                {
                    "GroupName": "my-sg-cli",
                    "GroupId": "sg-06345f49b2c8310af"
                }
            ],
            "SourceDestCheck": true,
            "StateReason": {
                "Code": "pending",
                "Message": "pending"
            },
            "VirtualizationType": "hvm",
            "CpuOptions": {
                "CoreCount": 1,
                "ThreadsPerCore": 1
            },
            "CapacityReservationSpecification": {
                "CapacityReservationPreference": "open"
            },
            "MetadataOptions": {
                "State": "pending",
                "HttpTokens": "required",
                "HttpPutResponseHopLimit": 2,
                "HttpEndpoint": "enabled",
                "HttpProtocolIpv6": "disabled",
                "InstanceMetadataTags": "disabled"
            },
            "EnclaveOptions": {
                "Enabled": false
            },
            "BootMode": "uefi-preferred",
            "PrivateDnsNameOptions": {
                "HostnameType": "ip-name",
                "EnableResourceNameDnsARecord": false,
                "EnableResourceNameDnsAAAARecord": false
            },
            "MaintenanceOptions": {
                "AutoRecovery": "default"
            }
        }
    ],
    "OwnerId": "134744162619",
    "ReservationId": "r-03008aca0e6043784"
}

```

```bash
ssh -i "MyKeyPair.pem" ec2-user@<ec2-34-204-197-22.compute-1.amazonaws.com>
```

en mi caso seria

```bash
ssh -i "MyKeyPair.pem" ec2-user@ec2-54-160-98-105.compute-1.amazonaws.com
```