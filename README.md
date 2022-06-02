This site was built using [GitHub Pages](https://pages.github.com/).
# AWS Real Worlk Tasks
## AWS Lambda Tasks
<details><summary>Send alerts if AWS KMS is not rotated</summary>

  ```css
  Fetch all AWS KMS keys and if KMS is not rotated in 90 days and emails using SES, this should
  be impletented by scheduling lambda function
  ```
</details>
<details><summary>Automatically tag EC2,ALB,Autoscaling, RDS instances using Lambda</summary>

  ```css
  Keep common tags in s3 bucket, trigger lambda function when EC2,ALB,Auto Scaling,RDS 
  resources are created and tag them automatically
  ```
</details>
<details><summary>Automatically shutdown Dev EC2 and RDS instance on weekends</summary>

  ```css
  Group EC2 and RDS by taging appropriately and stop them weekends and start them on weekdays
  ```
</details>

## AWS Issues faced
<details><summary>CNAMEAlreadyExists Exception</summary>
  
  ```
     Read the following link about the issues
     https://aws.amazon.com/premiumsupport/knowledge-center/resolve-cnamealreadyexists-error/
  ```
  
</details>
