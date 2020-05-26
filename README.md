# gcloud cheatsheet

## Contents

* [IAM](#iam)
* [Storage](#storage)
* [Services](#services)

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

## Storage

```bash
# Create a new bucket in a project
gsutil mb -p [PROJECT_NAME] -c [STORAGE_CLASS] -l [BUCKET_LOCATION] -b on gs://[BUCKET_NAME]/

# Delete a bucket
gsutil rm -r gs://[BUCKET_NAME]

# Delete bucket only if it is empty
gsutil rb gs://[BUCKET_NAME]

# Enable versioning in bucket
gsutil versioning set on gs://[BUCKET_NAME]
```

## Services

```bash
# Enable service API
gcloud services enable [API_NAME] --project [YOUR_PROJECT_ID]
```
