# Bank Demo on Kubernetes

TLDR - Use the scripts in this directory to deploy the microservices to K8s used to demo the full Tanzu portfolio

## Install Data Services from TAC
 
```shell script
1_installl-data-services.sh
```
Right now it installs MySQL from TAC demo repo which installs a master/worker
To get the mysql password you can run `$(kubectl get secret --namespace default acme-mysql -o jsonpath="{.data.mysql-root-password}" | base64 --decode)`
## Build

```shell script
2_build-all.sh
```
This builds all the microservices and copies the manifest YAMLs to the `yamls/` directory

## Deploy to K8s

Verify your K8s context is set to the right cluster

```shell script
3_deploy-all.sh
```
Applies the yamls from `yaml` directory 


## TSM

### Enabling ISTIO

Command to run enabling Istioo on each Cluster after Cluster has been on-boarding to TSM

```shell script
kubectl label namespace default istio-injection=enabled
```

### Creating the Gateway on the 

```shell script
kubectl apply -f yamls/tsm/gateway-acme-bank.yaml
```

