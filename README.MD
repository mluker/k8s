# Simple application set up using MongoDB and Mongo Express.

Prereq:
* Install [Kind](https://kind.sigs.k8s.io/)
* Install Docker

Steps:
1. kind create cluster ([create a cluster with one control-plane](https://kind.sigs.k8s.io/docs/user/quick-start/))
2. kubectl cluster-info --context kind-kind (set context)
3. kubectl apply -f mongo-secret.yaml
4. kubectl apply -f mongo-configmap.yaml
5. kubectl apply -f mongo.yaml
6. kubectl apply -f mongo-express.yaml
7. kubectl port-forward svc/mongo-express-service 30000:8081

## mongo.yaml
Deployment file a MongoDb database and service leveraging secrets

> | Command | Description |
> |---|---|
> | kubectl apply -f mongo.yaml | create |

## mongo-express.yaml
Deployment file a MongoDb database and service leveraging secrets and values from configMap.

> | Command | Description |
> |---|---|
> | kubectl apply -f mongo-express.yaml | create |
> | kubectl port-forward svc/mongo-express-service 30000:8081 | forward traffic to internal port |

## mongo-secret.yaml
Secrets have to be create before they can be referenced

> | Command | Description |
> |---|---|
> | echo -n 'my-password' \| base64 | create base64 string |
> | kubectl apply -f mongo-secret.yaml | create |

## mongo-configmap.yaml
Configs have to be create before they can be referenced

> | Command | Description |
> |---|---|
> | kubectl apply -f mongo-configmap.yaml | create |

## Useful commands
> | Command | Description |
> |---|---|
> | kublectl get service | list all of the services |
> | kublectl get pod | list all pods |
> | kublectl get service | list all services |
> | kubectl get secret | gets secret info |
> | kubectl apply -f <filename> | creates and updates resources in a cluster |
> | kubectl get all | list all info about the cluster |
> | kubectl cluster-info | get cluster info |
> | kind create cluster | create a new cluser, default name will be 'kind' |
> | kind delete cluster | delete a cluser, default name will be 'kind' |
> | echo -n 'my-password' \| base64 | create a base64 string |