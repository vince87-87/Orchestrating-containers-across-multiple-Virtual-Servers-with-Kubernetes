# STEP 0-INSTALL CLIENT TOOLS BEFORE BOOTSTRAPPING THE CLUSTER.

**awscli** – is a unified tool to manage your AWS services

**kubectl** – this command line utility will be your main control tool to manage your K8s cluster. 

**cfssl** – an open source toolkit for everything TLS/SSL from Cloudflare

**cfssljson** – a program, which takes the JSON output from the cfssl and writes certificates, keys, CSRs, and bundles to disk.

Install AWS CLI & Configure AWS Profile

aws configure sso

<img width="859" alt="image" src="https://user-images.githubusercontent.com/49937302/186780768-352e698f-c71c-4ed9-bcb5-82e613da4679.png">

aws ec2 describe-vpcs --profile AWSAdministratorAccess-877249880464

<img width="791" alt="image" src="https://user-images.githubusercontent.com/49937302/186781709-2cfc4ae3-cdb9-4fce-8023-ac0c07f45e96.png">

****Install kubectl** (linux)**

wget https://storage.googleapis.com/kubernetes-release/release/v1.21.0/bin/linux/amd64/kubectl

chmod +x kubectl

sudo mv kubectl /usr/local/bin/

kubectl version --client

****Install kubectl** (mac)**

brew install kubectl

**Install CFSSL and CFSSLJSON**

cfssl is an open source tool by Cloudflare used to setup a Public Key Infrastructure (PKI Infrastructure) for generating, signing and bundling TLS certificates. In previous projects you have experienced the use of Letsencrypt for the similar use case. Here, cfssl will be configured as a Certificate Authority which will issue the certificates required to spin up a Kubernetes cluster.

**LINUX**

wget -q --show-progress --https-only --timestamping \
  https://storage.googleapis.com/kubernetes-the-hard-way/cfssl/1.4.1/linux/cfssl \
  https://storage.googleapis.com/kubernetes-the-hard-way/cfssl/1.4.1/linux/cfssljson

chmod +x cfssl cfssljson

sudo mv cfssl cfssljson /usr/local/bin/

**MAC**

brew install cfssl

cfssl version

cfssljson --version

<img width="458" alt="image" src="https://user-images.githubusercontent.com/49937302/186782948-66185897-b676-4301-a593-4b85ba71da68.png">

brew install cfssl

# Step 1 – Configure Network Infrastructure (manually)

Create VPC

<img width="1415" alt="image" src="https://user-images.githubusercontent.com/49937302/186784239-e66df605-63a1-4dad-aa52-85374e06962d.png">

Configure DHCP Options

<img width="1429" alt="image" src="https://user-images.githubusercontent.com/49937302/186784851-48e91bcc-e0c4-4763-a82d-6de731404d16.png">

<img width="1440" alt="image" src="https://user-images.githubusercontent.com/49937302/186785064-84a0e71d-2cfa-403d-8bf1-cfdc56fa78c8.png">

Create IGW/Route table/Subnets

Create Security Group

Master & Worker node port requirement

https://kubernetes.io/docs/reference/ports-and-protocols/

<img width="738" alt="image" src="https://user-images.githubusercontent.com/49937302/186788036-79826a85-c18e-4eb0-8d48-b442789c8fac.png">

Allow inbound Traffic based on k8 port requirement

<img width="1430" alt="image" src="https://user-images.githubusercontent.com/49937302/186787651-53242898-73da-43aa-8e55-e620d695ca4b.png">

Create Load Balancer & target group

<img width="1421" alt="image" src="https://user-images.githubusercontent.com/49937302/186789431-5fa2eed3-7e55-415f-aeb7-5b2334a354f4.png">

<img width="1415" alt="image" src="https://user-images.githubusercontent.com/49937302/186789972-b2839ba0-906b-4e1c-ace8-5c99102bedad.png">

<img width="1438" alt="image" src="https://user-images.githubusercontent.com/49937302/186789560-605b76bc-5bf1-4c7c-b264-e46777e6067f.png">



