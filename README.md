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

# Get IAM policies of a project
gcloud projects get-iam-policy [PROJECT_ID]

# Grant user or service account a role on a project 
gcloud projects add-iam-policy-binding [PROJECT_ID] --member serviceAccount:[SA_NAME]@[PROJECT_ID].iam.gserviceaccount.com --role roles/[ROLE]

# Login as a service account with a credentials.json file
gcloud auth activate-service-account [ACCOUNT] --key-file=KEY_FILE

# Grant permission to a user account until a specific time
gcloud projects add-iam-policy-binding example-project-id-1 \
    --member='user:myuser@mydomain.com' \
    --role='roles/compute.instanceAdmin.v1' \
    --condition=”expression=request.time < \
                 timestamp("2020-12-31T00:00:00Z"),\
                 title=expires_end_of_2020,\
                 description=Expires at midnight on 2020-12-31”
```

## Storage

```bash
# Create a new bucket in a project
gsutil mb -p [PROJECT_NAME] -c [STORAGE_CLASS] -l [BUCKET_LOCATION] -b on gs://[BUCKET_NAME]/

# Delete a bucket and all of its objects
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

## Container / GKE

```bash
# Create a basic and cost effective GKE cluster for testing and dev 
gcloud container clusters create [CLUSTER_NAME] --project [YOUR_PROJECT_ID] --zone europe-west4-a --preemptible --num-nodes 1 --machine-type g1-small
```

```bash
# Enable autoscaling for GKE cluster and specify maximum number od nodes for the cluster 
gcloud container clusters update demo --enable-autoscaling --max-nodes 2
```
