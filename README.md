****Create EKS Cluster From UI**
**Create Role for EKS Cluster:**
Go to AWS Management Console.
Navigate to IAM (Identity and Access Management).
Click on "Roles" and then click on "Create role".
Choose "AWS Service" as the trusted entity.
Choose "EKS-cluster" as the use case.
Click "Next" and provide a name for the role.


**Create Role for EC2 Instances:**
Go to AWS Management Console.
Navigate to IAM (Identity and Access Management).
Click on "Roles" and then click on "Create role".
Choose "AWS Service" as the trusted entity.
Choose "EC2" as the use case.
Click "Next".
Add policies: [AmazonEC2ContainerRegistryReadOnly, AmazonEKS_CNI_Policy, AmazonEBSCSIDriverPolicy, AmazonEKSWorkerNodePolicy].
Provide a name for the role, e.g., "myNodeGroupPolicy".



**Create Compute Resources:**

Go to AWS Management Console.
Navigate to Amazon EKS service.
Click on "Compute" or "Node groups".
Provide a name for the compute resource.
Select the role created in step 2.
Select Node Type & Size.
Click "Next" and proceed to create the compute resource.

****Create EKS Cluster:**

Go to AWS Management Console.
Navigate to Amazon EKS service.
Click on "Create cluster".
Enter the desired name, select version, and specify the role created in step 1.
Configure Security Group, Cluster Endpoint, etc.
Click "Next" and proceed to create the cluster.

**Create Compute Resources:**
Go to AWS Management Console.
Navigate to Amazon EKS service.
Click on "Compute" or "Node groups".
Provide a name for the compute resource.
Select the role created in step 2.
Select Node Type & Size.
Click "Next" and proceed to create the compute resource.

**Configure Cloud Shell:**

1.Open AWS Cloud Shell or AWS CLI.

Execute the command:

aws eks update-kubeconfig --name shack-eks --region ap-south-1

2.Replace "shack-eks" with the name of your EKS cluster and "ap-south-1" with the appropriate region if different.

3.These steps should help you in setting up your EKS cluster along with necessary roles and compute resources.

**Install ArgoCD:**
Here are the steps to install ArgoCD and retrieve the admin password:

#Create Namespace for ArgoCD:

kubectl create namespace argocd

#Apply ArgoCD Manifests:

kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/v2.4.7/manifests/install.yaml

#Patch Service Type to LoadBalancer:

kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'

#Retrieve Admin Password:

kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d

These commands will install ArgoCD into the specified namespace, set up the service as a LoadBalancer, and retrieve the admin password for you to access the ArgoCD UI.

**# install argoCD**
![Screenshot 2024-03-04 113202](https://github.com/vijayalakshmi1205/repo-2/assets/144942239/7709f737-4bd1-49ff-b690-d86cd1cdc547)

**# repo**
![Screenshot 2024-03-04 120935](https://github.com/vijayalakshmi1205/repo-2/assets/144942239/b17ae296-cd2c-4a90-8174-8843af87252b)

**# deployed**
![Screenshot 2024-03-04 121510](https://github.com/vijayalakshmi1205/repo-2/assets/144942239/0ee11fb4-88ac-46d7-9e81-469747728239)

**# output ping**
![Screenshot 2024-03-04 121046](https://github.com/vijayalakshmi1205/repo-2/assets/144942239/5c18fbeb-637a-408b-ba33-d4895731f719)

