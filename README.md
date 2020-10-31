# MongoDB-Kubernetes

Note: Order of creation matters!

## Create secret
kubectl apply -f mongo-secret.yaml

## Create MongoDB deployment
kubectl apply -f mongo-deployment.yaml

## Create MongoDB service
kubectl apply -f mongo-service.yaml

## Create ConfigMap
kubectl apply -f mongo-configmap.yaml

## Create Mongo Express deployment
kubectl apply -f mongo-express-deployment.yaml

## Create external service for Mongo Express
kubectl apply -f mongo-express-service.yaml
