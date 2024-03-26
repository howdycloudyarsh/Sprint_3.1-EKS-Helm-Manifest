## Sprint_3.1-EKS-Helm-Manifest

### Deploy Google Micro-Services Application EKS Manually using Manifest and Helm Concept.

### 1. Through "Manifest" 

```
git clone https://github.com/howdycloudyarsh/Sprint_3.1-EKS-Helm-Manifest.git
cd Sprint_3.1-EKS-Helm-Manifest
terraform init
terraform validate
terraform fmt
terraform plan
terraform apply --auto-approve
```

#### Once EKS and nodes get craeted then got to the "kubectl server" , execute these below commands

'''
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
'''

#### Configure AWS credentials

```
aws configure
```

#### Install kubectl binary with curl on Linux

```
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
```

#### Install kubectl

```
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
```

#### Then Run these below commands on "kubectl-server"

```
aws eks --region <region-name> describe-cluster --name <cluster-name> --query cluster.status
aws eks --region <region-name> update-kubeconfig --name <cluster-name>
```

#### Then to check we will clone google online boutique repository as example.

```
git clone https://github.com/GoogleCloudPlatform/microservices-demo
cd microservices-demo/
```

#### Deploy Online Boutique to the cluster.

```
kubectl apply -f ./release/kubernetes-manifests.yaml
```

#### Wait for the pods to be ready.

```
kubectl get pods  "or"
kubectl get pods -o wide
```


#### After a few minutes, you should see the Pods in a Running state.


![image](https://github.com/howdycloudyarsh/Sprint_3.1-EKS-Helm-Manifest/assets/133496386/51781079-0e76-4cb6-9026-605e0d7f42e3)


![image](https://github.com/howdycloudyarsh/Sprint_3.1-EKS-Helm-Manifest/assets/133496386/9bee68ba-e224-4be5-b493-3c50ce237edd)










