# DevOps Training - Team Deployment

## Requirements:
1. Install Terraform: https://www.terraform.io/downloads
2. Install AWS CLI: https://aws.amazon.com/cli/
3. Configure AWS CLI with an AWS account

## Steps to Deploy:

### Step 1: Configure AWS CLI
```bash
aws configure sso
```
- Below are the example values you can use.
```bash
sso_start_url = # Provided by your instructor
sso_region = ap-south-1
sso_account_id = # Provided by your instructor
sso_role_name = AmazonS3Access
region = ap-south-1
output = json
```
-------------------

```bash
notepad $env:USERPROFILE\.aws\config
```
- Config should look something similar like below configuration, if not please replace it with below values. And update the sso_start_url and sso_account_id with correct values.
```bash
[profile AmazonS3Access]
sso_start_url = # Provided by your instructor
sso_region = ap-south-1
sso_account_id = # Provided by your instructor
sso_role_name = AmazonS3Access
region = ap-south-1
output = json
```
-------------------

```bash
aws configure list-profiles
```

 - You should see "AmazonS3Access"

-------------------

```bash
aws sso login --profile AmazonS3Access
```
 - Now a aws webpage will open and perform the authentication and allow it to access your AWS account.

-------------------
### Step 2: Terraform command to deploy

```bash
terraform init
```
- This will take some tiem to install the modules. So be patient and wait for a while.

-------------------

```bash
terraform validate
```
- This will validate your terraform code and provides a Success message.

-------------------

```bash
terraform plan -var="student_id=Yourname"
```
- This will perform a plan and will showcase what are the aws resources will be created or destroyed or updated, so please make sure your are creating right things.

-------------------

```bash
terraform apply -var="student_id=Yourname"
```
- This will deploy your solution to your aws account and once its successful you will get website_url and bucket_name. And also you can verify it in you AWS S3.

-------------------

```bash
terraform destroy -var="student_id=Yourname"
```
- Once everything is done, please clean your stash.