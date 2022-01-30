# Simple Spinnaker Pipeline for Deployment into GKE Clusters

This is a simple pipeline setup using Spinnaker for the Continuous Delivery and GKE as Deployment Clusters.

## The Setup

- [Spinnaker Setup](https://github.com/ullask93/spinnaker_gke/blob/main/GKE_setup.md)
- [GKE Cluster Setup](https://github.com/ullask93/spinnaker_gke/blob/main/GKE_setup.md)
- [Code Build trigger for source code change in Github](https://cloud.google.com/build/docs/automating-builds/build-repos-from-github)

## Spinnaker Pipeline

- Developer pushes changes to the repository in github
- The Code Build trigger watches for the changes in Source code repository. It builds an image using DockerFile and pushes the image to Container registry.
- Spinnaker watches for this event using Pub/Sub service **(Configuration Stage)**
- Spinnaker will deploy the application into Dev Cluster. **(Deploy Manifest)** 
- Once the Deployment is Successful, one may need to manually approve for the Deployment into Prod Cluster **(Manual Approval)**
- Deployment into the Prod Cluster **(Deploy Manifest)**

