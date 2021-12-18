Scenario 3
Let's get familiar with instance-profiles

Task goal: Terminate your personal instance
Resources:

EC2 - that you need to terminate
EC2 - instance that you create with the next parameters
AMI: ami-0718a1ae90971ce4d
Instance-type: t2.micro
Tag-specifications: 'ResourceType=instance,Tags=[{Key=Owner,Value=vasyl_ostapenko}]'
User: ubuntu
Note: use --subnet-id and --security-group-ids
Install AWS CLI but don't configure it
Be careful, if any of the parameters above are missing or incorrect, your instance will be automatically deleted
Filter example EC2: --filters "Name=tag-value,Values=scenario3*"
Credentials (used only for invoking validation Lambda):

Access key:
Sekret key:
Username:

************************

[2:45 PM] Anatolii Hromov
Final battle. You vs SSMTask goal: Find your personal key and validate it by invoking your personal Lambda function sc6_complete_Anatolii_Hromov with parameters (--payload '{"key": "Name_SurnameXXXXXXXXXXXX"}') Resources: EC2 RDS Lambda - sc6-lambdaLambda - sc6_complete_Anatolii_HromovFilter example EC2: --filters "Name=tag-value,Values=scenario6*"Credentials (start and finish with them): 

[2:45 PM] Anatolii Hromov
AKIA36D6ZZWUSGBYBM7Z

******************************

[2:45 PM] Anatolii Hromov
Final battle. You vs SSMTask goal: Find your personal key and validate it by invoking your personal Lambda function sc6_complete_Anatolii_Hromov with parameters (--payload '{"key": "Name_SurnameXXXXXXXXXXXX"}') Resources: EC2 RDS Lambda - sc6-lambdaLambda - sc6_complete_Anatolii_HromovFilter example EC2: --filters "Name=tag-value,Values=scenario6*"Credentials (start and finish with them): 

[2:45 PM] Anatolii Hromov
AKIA36D6ZZWUSGBYBM7Z

[2:45 PM] Anatolii Hromov
QhoP5K7y0qyIV5GeAE2FofR2x0bM/m2wOylGiibC

[2:45 PM] Anatolii Hromov
sc6_complete_vasyl_ostapenko



*******************

[2:34 PM] Anatolii Hromov
Configure your profileaws configure --profile scenario6_usernameDescribe the SSM parametersaws ssm describe-parameters --profile scenario6_usernameGet the keysaws ssm get-parameter --name <sc6-ec2-private-key> --profile scenario6_usernameecho -e "<private key>" > ec2_ssh_keyaws ssm get-parameter --name <sc6-ec2-public-key> --profile scenario6_usernameecho -e "<public key>" > ec2_ssh_key.pubGet the list of all EC2 virtual machineaws ec2 describe-instances --profile scenario6_usernameConect to EC2 virtual machinessh -i ec2_ssh_key ubuntu@<instance ip>Do from ec2 instance:aws lambda list-functions --region eu-central-1aws lambda get-function --function-name sc6-lambda --region eu-central-1do to your local machine: aws rds describe-db-instances

[2:34 PM] Anatolii Hromov
psql -h <rds db host/ip> -U sc6admin -d SecurityChalleng/dselect * from sensitive_information;

********************************
[2:34 PM] Anatolii Hromov
    Configure your profile
aws configure --profile scenario6_username
Describe the SSM parameters
aws ssm describe-parameters --profile scenario6_username
Get the keys
aws ssm get-parameter --name <sc6-ec2-private-key> --profile scenario6_username
echo -e "<private key>" > ec2_ssh_key
aws ssm get-parameter --name <sc6-ec2-public-key> --profile scenario6_username
echo -e "<public key>" > ec2_ssh_key.pub
Get the list of all EC2 virtual machine
aws ec2 describe-instances --profile scenario6_username
Conect to EC2 virtual machine
ssh -i ec2_ssh_key ubuntu@<instance ip>
Do from ec2 instance:

aws lambda list-functions --region eu-central-1
aws lambda get-function --function-name sc6-lambda --region eu-central-1
do to your local machine: aws rds describe-db-instances 
​[2:34 PM] Anatolii Hromov
    
psql -h <rds db host/ip> -U sc6admin -d SecurityChalleng

/d

select * from sensitive_information;
<https://teams.microsoft.com/l/message/19:aeb8bdabd8704a3d91d6e933f08ab487@thread.tacv2/1639830864447?tenantId=b41b72d0-4e9f-4c26-8a69-f949f367c91d&amp;groupId=c285dae1-9c1f-41fb-b2b5-98bd39ac9e5f&amp;parentMessageId=1639816798692&amp;teamName=EPAM AWS Security Challenge - Gameday for Students - Dec-2021&amp;channelName=Group-3&amp;createdTime=1639830864447>

**********************************

aws ssm describe-parameters --profile sc6

aws ssm get-parameter --name sc6-ec2-public-key --profile sc6

aws ssm get-parameter --name sc6-ec2-private-key --profile sc6



ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQDiPzQQpADHhh+TACGC/5IbZnALoovGuYY0RYkMe1DC53AkyT8MiZqDhtCl8a7+h+vonAYQ5c/FrKqp9o1IJ30YIch+IVoHXHMAttgb6Xeq4ME7KTXG3yukPG+xCNWGtRC6hlYrIKhgpEQwmGT1dDRT+LBaHmdHKGSwNBMjRgJEFNYHJL/JTqKtnILTZX4TAD+j4Net5w6l84zx1CMtIZ4HGNJqLpWtnAPlJpX0tJueicPomOP0MvBKVGFX+Nv5DneUN8XeF4/u75GVe5w9LtMLksFE4391qw9g25MBrR8tKQS9waGQH/JZTgTg4awJpAMuedxHMhlqZYY8MWazDbJCTgawFYV1Z2ZcNj6ilJNRmdMW4uEa3fqhQm42RDkkYDi0CU9zYWh/8kutbw3KBN3EZegKDZJi2M+fXWRMzMK33X3UcX1VzQKimZESov70VgnpKS4DJXg7UMrZOoKd0lHsqKns+fwx8DXilTbK3VMtycGVQv0XGjv/Y0x+VmofIgAeuIab8OHcX5BNCNG0h+YtCA9tg/ypCppeGqrAXwHw9Q2IakfaQiQe1kmwohunM2WqM3YsME8rRcHa/G763oJz2CzCd8HkSkKwUFEGr48zhSp1t9v8vMW1TV4aN5hAjKmk6x2fXSjq/UfslwMt5hM9t5pQ+SAqYi9fe06i6iQnbQ== vagrant@ubuntu-bionic

aws rds describe-db-instances --region eu-central-1

aws ec2 describe-instances --profile sc6
 
 
 3.70.156.126

ssh ubuntu@3.70.156.126 -i .\pr.ppk

aws lambda list-functions --region eu-central-1
aws lambda get-function --function-name sc6-lambda --region eu-central-1

DB_USER": sc6admin,
DB_NAME": "securedb,
DB_PASSWORD": "wagrrrrwwgahhhhwwwrrggawwwwwwrr"

psql -h sc6-rds-instance.chuhuhafdyes.eu-central-1.rds.amazonaws.com -U sc6admin -d securedb

Key_37 | vasyl_ostapenko831d2d985471c283


aws lambda invoke --function-name sc6_complete_vasyl_ostapenko --payload '{\"key\": \"vasyl_ostapenko831d2d985471c283\"}' --profile=sc6 output.json  
