# MongoDB-Kubernetes

This repository contains a Helm chart for deploying MongoDB and Mongo Express. The chart simplifies the process of setting up and managing MongoDB and its administrative interface, Mongo Express, within a Kubernetes cluster. It's for development purposes only since there is no persistance configured for the database.

## Chart Details

- **Chart Name:** mongodb-chart
- **Description:** Helm chart for deploying MongoDB and Mongo Express
- **Version:** 0.1.0

## Installation

You can install Helm chart directly from published version on GitHub Packages:
```
$ helm upgrade --install mongodb-chart oci://ghcr.io/cvitaa11/mongodb-chart --version 0.1.0
```

or package it locally on your machine by following the instructions below 👇🏻

1. Make sure you have Helm installed on your machine and configured to work with your Kubernetes cluster.

2. Clone this repository:
```
git clone [repository_url]
cd [repository_directory]
```

3. Customize the deployment by editing the `values.yaml` file. You can modify settings such as memory and CPU limits for MongoDB and Mongo Express, as well as the service type and node port.

4. Package the Helm chart using the following command: `helm package ./mongodb-chart`

5. Deploy the Helm chart using the packaged chart and the following command: `helm install [release_name] mongodb-chart-0.1.0.tgz`

Replace `[release_name]` with a name for your release.

6. Monitor the deployment using Kubernetes tools like `kubectl` and check the status of your pods, services, and any associated resources.

## Configuration

The main configuration for the MongoDB and Mongo Express deployment can be found in the `values.yaml` file. You can adjust the following parameters:

- `mongodb.image`: The Docker image for MongoDB.
- `mongodb.resources.limits.memory` and `mongodb.resources.limits.cpu`: Memory and CPU limits for the MongoDB container.
- `mongoExpress.image`: The Docker image for Mongo Express.
- `mongoExpress.resources.limits.memory` and `mongoExpress.resources.limits.cpu`: Memory and CPU limits for the Mongo Express container.
- `service.type`: The type of Kubernetes service (e.g., LoadBalancer, NodePort).
- `service.nodePort`: The node port used for accessing the services.

## Clean Up

To uninstall the Helm release and remove all associated resources, use the following command:
```
helm uninstall [release_name]
```

Replace `[release_name]` with the name of your release.

If you don't want to use Helm chart you can also deploy separate manifests one by one.

NOTE: Order of creation matters!

#### Create secret
```
kubectl apply -f mongo-secret.yaml
```

#### Create MongoDB deployment
```
kubectl apply -f mongo-deployment.yaml
```

#### Create MongoDB service
```
kubectl apply -f mongo-service.yaml
```

#### Create ConfigMap
```
kubectl apply -f mongo-configmap.yaml
```

#### Create Mongo Express deployment
```
kubectl apply -f mongo-express-deployment.yaml
```

#### Create external service for Mongo Express
```
kubectl apply -f mongo-express-service.yaml
```