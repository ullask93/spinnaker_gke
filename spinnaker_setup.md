# Spinnaker Setup on GCP

Refer link: https://github.com/GoogleCloudPlatform/spinnaker-for-gcp.git

Clone this repo on Google Console in the Directory ```cloudshell_open```

Spinnaker is deployed as a Stateful set in Kubernetes Cluster and makes use of Cloud Storage to store its Persistant Data. <br>
Before the setup make sure that the necessary roles are assigned to the user.

## Spinnaker on GKE Cluster

```
mkdir $HOME/spinnaker
cd $HOME/spinnaker
WORKDIR=$(pwd)
```
Install kubectx (this tool will help to easily swith between different contexts)
```
git clone https://github.com/ahmetb/kubectx $WORKDIR/kubectx
export PATH=$PATH:$WORKDIR/kubectx
```

Configure Project, Zone for the setup
```
gcloud config set project PROJECT_ID
export ZONE=<region>
gcloud config set compute/zone ${ZONE}
```
Run the setup script.
```
PROJECT_ID=${DEVSHELL_PROJECT_ID}
~/cloudshell_open/spinnaker-for-gcp/scripts/install/setup_properties.sh
~/cloudshell_open/spinnaker-for-gcp/scripts/install/setup.sh
```
Connect to Spinnaker
```
~/cloudshell_open/spinnaker-for-gcp/scripts/manage/connect_unsecured.sh
```


