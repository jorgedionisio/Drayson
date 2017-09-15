# Drayson

Install gcloud and kubectl:
'''https://cloud.google.com/sdk/docs/quickstarts'''

sudo yum update kubectl

Set the project id and compute zone:

gcloud config set project PROJECT_ID
gcloud config set compute/zone us-central1-b

Clone the necessary files from Google Cloud git repo:
git clone https://github.com/GoogleCloudPlatform/container-engine-samples
cd container-engine-samples/wordpress-persistent-disks

Create the Kubernetes cluster:
gcloud container clusters create persistent-disk-tutorial --num-nodes=3

Create the persistent disks:
gcloud compute disks create --size 200GB mysql-disk
gcloud compute disks create --size 200GB wordpress-disk

Setup MySQL

Change the password to one of your choice:
kubectl create secret generic mysql --from-literal=password=YOUR_PASSWORD

kubectl create -f mysql.yaml

Check if the container is running:
kubectl get pod -l app=mysql

Create MySQL Service

kubectl create -f mysql-service.yaml

Check if the MySQL service is created:
kubectl get service mysql

Setup WordPress

kubectl create -f wordpress.yaml

Check if the container is running:
kubectl get pod -l app=wordpress

Expose the wordpress App:

kubectl create -f wordpress-service.yaml

Check the external IP address of the cluster:

kubectl get svc -l app=wordpress
