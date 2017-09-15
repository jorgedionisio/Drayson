# Drayson

Install gcloud and kubectl:
https://cloud.google.com/sdk/docs/quickstarts

sudo yum update kubectl

Set the project id and compute zone:

gcloud config set project PROJECT_ID
gcloud config set compute/zone us-central1-b

Clone the necessary files from Google Cloud git repo:

git clone https://github.com/GoogleCloudPlatform/container-engine-samples
cd container-engine-samples/wordpress-persistent-disks
