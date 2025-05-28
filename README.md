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

Now, we need to connect to our Kubernetes cluster. This can be done by running the following command:

                 aws eks --region us-east-1 update-kubeconfig --name <cluster-name>

Step 3: Install ArgoCD via Helm

helm repo add argo https://argoproj.github.io/argo-helm
helm install argocd argo/argo-cd \
  --namespace argocd --create-namespace \
  --set server.service.type=LoadBalancer


To log in to Argo

              argocd_initial_admin_secret = "kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath={.data.password} | base64 -d"
              argocd_server_load_balancer = "a53a6bf4abebe46f79da6179425ca5f4-7d359c1121a50305.elb.eu-west-1.amazonaws.com"


We need to get the initial ArgoCD admin secret, so we can run the first command for that:

                kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath=\"{.data.password}\" | base64 -d"

I have used domain that is not valid just i adde3d we can configure this way (optional)


