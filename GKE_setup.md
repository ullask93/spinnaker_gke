# Create GKE clusters

Create the Cluster
```
gcloud container clusters create dev --zone <region> --num-nodes 1 --machine-type n1-standard-2
gcloud container clusters create prod --zone <region> --num-nodes 1 --machine-type n1-standard-2
```

Connect to the clusters (to make an entry to **kubeconfig** file)
```
export PROJECT_ID=$(gcloud info --format='value(config.project)')
gcloud container clusters get-credentials dev --zone <region> --project ${PROJECT_ID}
gcloud container clusters get-credentials prod --zone <region> --project ${PROJECT_ID}
```
Configure Spinnaker cluster and GKE clusters by adding kubernetes account to Spinnaker Configuration
```
~/cloudshell_open/spinnaker-for-gcp/scripts/manage/add_gke_account.sh
```
Change the context to Spinnaker cluster
```
kubectx gke_${DEVSHELL_PROJECT_ID}_${ZONE}_spinnaker-1
~/cloudshell_open/spinnaker-for-gcp/scripts/manage/push_and_apply.sh
```
Whenever there are changes made into hal configuration file locally, it has to be pushed and applied into the application in the cluster.
