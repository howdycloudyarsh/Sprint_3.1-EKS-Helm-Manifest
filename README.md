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

```
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```

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


==================================================================================================================================================================

==================================================================================================================================================================

### 2. Through "HELM" 

```
terraform init
terraform validate
terraform fmt
terraform plan
terraform apply --auto-approve
```

#### Once EKS and nodes get craeted then got to the "kubectl server" , execute these below commands.

#### Step #1:Install Helm on Ubuntu

#### Download the gpg key

```
curl https://baltocdn.com/helm/signing.asc | gpg --dearmor | sudo tee /usr/share/keyrings/helm.gpg > /dev/null
```

#### Install the apt-transport-https 

```
sudo apt-get install apt-transport-https --yes
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/helm.gpg] https://baltocdn.com/helm/stable/debian/ all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list
```

#### We need to update your system packages:

```
sudo apt-get update
```

#### Now lets Install helm:

```
sudo apt-get install helm
```

#### Step #2:Install AWS CLI on Ubuntu

#### Download the aws cli bundle using below command

```
sudo curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
```

#### Extract the aws cli bundle setup

```
sudo unzip awscliv2.zip
```

#### Configure the AWS CLI on Ubuntu


```
sudo ./aws/install
```

#### Verify the AWS CLI version

```
aws --version
```

#### Step #3:Install kubectl binary with curl

#### Download the latest release with the command:

```
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
```

#### Install kubectl

```
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
```

#### Test to ensure the version you installed is up-to-date:

```
kubectl version --client
```

#### Step #4:Configure AWS CLI

#### To connect AWS using CLI we have configure AWS user using below command

```
aws configure
```

#### It will ask AWS Access Key ID, AWS Secret Access Key, Default region name, Default output format.


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

#### Now install Helm chart

```
helm install <deployment-name> helm-chart/
```

![image](https://github.com/howdycloudyarsh/Sprint_3.1-EKS-Helm-Manifest/assets/133496386/2c2bfe08-433f-4f2d-af3d-9be13b1e729c)


#### It may take a few minutes for the LoadBalancer IP to be available.

![image](https://github.com/howdycloudyarsh/Sprint_3.1-EKS-Helm-Manifest/assets/133496386/539c168b-f8d9-49e6-80f6-263dc8c7ae3a)


#### Now copy and paste your load balancer url to the browser and check


![image](https://github.com/howdycloudyarsh/Sprint_3.1-EKS-Helm-Manifest/assets/133496386/ad135790-7896-4e40-b04a-ac9fdf9679e3)







