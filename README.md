# EKS [ Cluster Autoscaler ]

## Overview
EKS Cluster Autoscaler basically handles both master and worker nodes in Amazon's Elastic Kubernetes Service (EKS). It uses EKS for master node stuff and the Cluster Autoscaler to adjust worker nodes based on how busy things get. Easy peasy!

## Installation Steps

### 1. Set Up VPC: 
Use CloudFormation to create a secure VPC environment.

### 2.Create EKS Role
 Make an IAM role with the "AmazonEKSCluster" policy for EKS management.

### 3. Create EKS Cluster
- Execute the creation of an EKS cluster, specifying:
  - The previously created EKS role.
  - The VPC established through the CloudFormation.
  - Public and private cluster endpoint access settings.
  - Default selection of pods to be added to the cluster.

### 4. Add Node Group
Configure the node group with:
  - The VPC created earlier.
  - A role with policies (EC2ContainerRegistry, EKS_CNI, EKSWorkerNode, IAM-Policy_for_AutoScaler).

### 5. Configure kubectl
Use Cloud Shell to configure kubectl for EKS interaction.:
```bash
aws eks update-kubeconfig --name <cluster_name>
```

### 6. Deploy Cluster Autoscaler
Run the cluster-AutoScaler.yaml file to get your autoscaler going.

### 7. Customize Autoscaler
Use the command below to edit the Cluster Autoscaler deployment and customize parameters such as cluster name and Kubernetes version:
```bash
kubectl edit deployment -n kube-system cluster-autoscaler
```

### 8. Check Deployment
Make sure everything's running smoothly by checking pod status and logs:
```bash
kubectl get pod -n kube-system
kubectl logs -n kube-system POD_NAME
```

### 9. Deploy Nginx:
Deploy a sample Nginx app for testing by rununng the nginx.yaml 
#Then 
Access the application through the LoadBalancer DNS in web browser.

### 10. Test Autoscaling
Play around with Nginx replicas to see autoscaling behavior.
