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
