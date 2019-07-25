# GCLOUD CHEATSHEET

## Contents

* [IAM](#iam)

## IAM

```bash
# Create service account in project
gcloud iam service-accounts create [SERVICE_ACCOUNT_NAME] --project [PROJECT_ID]

# Create and download JSON key for service account
gcloud iam service-accounts keys create ./credentials.json --iam-account [SA_NAME]@[PROJECT_ID].iam.gserviceaccount.com

# List active keys for service account
gcloud iam service-accounts keys list --iam-account [SA_NAME]@[PROJECT_ID].iam.gserviceaccount.com

# Delete JSON key from service account
gcloud iam service-accounts keys delete [KEY_ID] --iam-account [SA_NAME]@[PROJECT_ID].iam.gserviceaccount.com
```
