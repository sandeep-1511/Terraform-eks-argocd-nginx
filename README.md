Step 1: Create the architecture
This structure shows the key components and their roles in deploying the EKS cluster:

           terraform-eks-argocd-nginx/
           ├── terraform/ # Terraform code for EKS & VPC
           ├── manifests/ # Kubernetes manifests (Deployment & Service)
           ├── argocd/ # ArgoCD Application resource
           └── README.md

##   Prerequisites

- AWS CLI configured (`aws configure`)
- Terraform v1.5+
- kubectl
- Helm
- A GitHub repo


Step 2: Install AWS CLI

Step 3: Install Terraform

Step 4: Connect Terraform to AWS

Step 5: Create Terraform modules
These are the 6 files you will create to deploy your eks cluster:

         Create VPC module  
         Create EKS module
         Create Security Groupe module
         Create variables
         Create version
         Create output



Step 6: Run Terraform
Initialize Terraform
terraform init



Review Terraform Plan
terraform plan

Apply Terraform to Deploy EKS Cluster
terraform apply

Type yes to confirm and start deploying your infrastructure.



Step 3: Install ArgoCD via Helm

helm repo add argo https://argoproj.github.io/argo-helm
helm install argocd argo/argo-cd \
  --namespace argocd --create-namespace \
  --set server.service.type=LoadBalancer


