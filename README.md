# Terraform AWS EKS Infrastructure

This project provisions an **Amazon EKS cluster and its supporting AWS infrastructure using Terraform**.

The infrastructure is fully defined as Code, allowing the complete environment to be created with `terraform apply` and removed with `terraform destroy`.

## Architecture

* **VPC:** `10.0.0.0/16`
* **Subnets:** 2 public subnets across 2 Availability Zones
* **EKS Cluster:** Kubernetes 1.31
* **Node Group:** 2 × `t3.medium` EC2 instances
* **IAM Roles:** Separate IAM roles for the EKS cluster and worker nodes
* **Internet Gateway:** Provides internet access for public subnets
* **Infrastructure as Code:** Terraform

## Project Structure

```text
terraform-aws-eks/
├── provider.tf         # AWS provider configuration
├── variables.tf        # Input variables
├── vpc.tf             # VPC, subnets, route tables, and Internet Gateway
├── iam.tf             # IAM roles and policies
├── eks.tf             # EKS cluster configuration
├── node-groups.tf     # EKS worker node group
├── outputs.tf         # Terraform output values
└── terraform.tfvars   # Variable values
```

## Key Features

* Infrastructure as Code using **Terraform**
* Multi-AZ architecture for improved availability
* Reusable configuration using **Terraform variables**
* Terraform outputs for important infrastructure values
* Dedicated IAM roles for EKS cluster and worker nodes
* Proper AWS resource tagging for EKS integration
* Complete infrastructure deployment using `terraform apply`
* Complete infrastructure cleanup using `terraform destroy`

## Deployment

### 1. Initialize Terraform

```bash
terraform init
```

### 2. Preview Infrastructure Changes

```bash
terraform plan
```

### 3. Deploy the Infrastructure

```bash
terraform apply
```

After deployment, Terraform provisions the VPC, networking components, IAM roles, EKS cluster, and worker nodes.

### 4. Configure kubectl

Connect your local `kubectl` to the newly created EKS cluster:

```bash
aws eks update-kubeconfig --region us-east-1 --name three-tier-eks
```

Verify the worker nodes:

```bash
kubectl get nodes
```

## Infrastructure Validation

The screenshots below demonstrate the successful creation of the:

* AWS VPC and networking infrastructure
* EKS cluster
* Worker nodes and Kubernetes connectivity
* Terraform-managed AWS resources

### Successful Deployment

![EKS Cluster](https://github.com/user-attachments/assets/cad5fcfa-591a-4c89-b0cb-b077bec94a0a)

![AWS Infrastructure](https://github.com/user-attachments/assets/85ea0ec6-ffc5-4522-86f2-97e81ee296f8)

![Terraform Deployment](https://github.com/user-attachments/assets/609d7004-063f-453a-b39f-e9271949a014)

## Cleanup

To avoid unnecessary AWS charges, the infrastructure can be completely removed with:

```bash
terraform destroy
```

Terraform will remove the resources created by this project.

## What I Learned

Through this project, I practiced provisioning AWS infrastructure from scratch using Terraform and deploying an EKS Kubernetes environment with networking, IAM, and worker nodes.

This project demonstrates practical experience with:

**Terraform → AWS VPC → IAM → EKS → EC2 Worker Nodes → Kubernetes**

---

**Built by Hashir**




