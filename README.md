# Event-Driven Architecture for maintaing companies policy for only using EBS volume 'gp3' using for LambdaFunction and CloudWatch, IAM !

Video link for steps:- https://drive.google.com/file/d/1hst09gyirebfJuz5YAstXhXn37L4CJVs/view?usp=sharing

1. Create lambda_fun.py using python boto3 and create new role.

Inside lambda function create role as in image.

![Screenshot](https://github.com/ItsDev75/EBS_VOLUME_MAINTAINER/assets/80349641/b0909a5e-2a25-4e3c-bded-2447ac930f49)

Role created "ebs_vol_check-role-c8edb2k1"
 
2. Create Event rule in AWS CloudWatch.
# Event Pattern:-  
```
  {
    "source": ["aws.ec2"],
    "detail-type": ["EBS Volume Notification"],
    "detail": {
      "event": ["createVolume"]
    }
  }
```

3. Adding policies to role "ebs_vol_check-role-c8edb2k1" created by Lambda
# Permissions policies --> Ebs-volume-check:-
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "VisualEditor0",
            "Effect": "Allow",
            "Action": [
                "ec2:ModifyVolume",
                "ec2:ModifyVolumeAttribute",
                "ec2:CreateVolume"
            ],
            "Resource": "*"
        }
    ]
}
```
Congratulations!! Your job is safe now :wink:
