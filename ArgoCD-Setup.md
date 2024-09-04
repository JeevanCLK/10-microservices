# Create AWS EKS Cluster From AWS UI

1. **Create Role for EKS Cluster**:
   - Go to AWS Management Console.
   - Navigate to IAM (Identity and Access Management).
   - Click on "Roles" and then click on "Create role".
   - Choose "AWS Service" as the trusted entity.
   - Choose "EKS-cluster" as the use case.
   - Click "Next" and provide a name for the role.

2. **Create Role for EC2 Instances**:
   - Go to AWS Management Console.
   - Navigate to IAM (Identity and Access Management).
   - Click on "Roles" and then click on "Create role".
   - Choose "AWS Service" as the trusted entity.
   - Choose "EC2" as the use case.
   - Click "Next".
   - Add policies: [AmazonEC2ContainerRegistryReadOnly, AmazonEKS_CNI_Policy, AmazonEBSCSIDriverPolicy, AmazonEKSWorkerNodePolicy].
   - Provide a name for the role, e.g., "myNodeGroupPolicy".

3. **Create EKS Cluster**:
   - Go to AWS Management Console.
   - Navigate to Amazon EKS service.
   - Click on "Create cluster".
   - Enter the desired name, select version, and specify the role created in step 1.
   - Configure Security Group, Cluster Endpoint, etc.
   - Click "Next" and proceed to create the cluster.

4. **Create Compute Resources**:
   - Go to AWS Management Console.
   - Navigate to Amazon EKS service.
   - Click on "Compute" or "Node groups".
   - Provide a name for the compute resource.
   - Select the role created in step 2.
   - Select Node Type & Size.
   - Click "Next" and proceed to create the compute resource.

5. **Configure Cloud Shell**:
   - Open AWS Cloud Shell or AWS CLI.
   - Execute the command:
     ```
     aws eks update-kubeconfig --name jeevans-eks --region ap-south-1
     ```
   - Replace "jeevans-eks" with the name of your EKS cluster and "ap-south-1" with the appropriate region if different.

These steps should help you in setting up your EKS cluster along with necessary roles and compute resources.


# Install ArgoCD

Here are the steps to install ArgoCD and retrieve the admin password:

1. **Create Namespace for ArgoCD**:
   ```bash
   kubectl create namespace argocd
   ```

2. **Apply ArgoCD Manifests**:
   ```bash
   kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/v2.4.7/manifests/install.yaml
   ```

3. **Patch Service Type to LoadBalancer**:
   ```bash
   kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'
   ```

4. **Retrieve Admin Password**:
   ```bash
   kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
   ```
5. **Create a docker secrets in the same namespace where your aoplication has been deployed and include the dockehub username,password,email and namespace name in the below cmd(don't forgot to include your image pull secrets in deployment.yml files)**:

    imagePullSecrets:
    - - name: my-dockerhub-secret
     
   ```bash
   kubectl create secret docker-registry my-dockerhub-secret \--docker-server=https://index.docker.io/v1/ \--docker-username=XYZ \--docker-password=yourpasswdhere \-- 
   docker-email=xyz@gmail.com \--namespace=yourapplicationdeployednamespace name

These commands will install ArgoCD into the specified namespace, set up the service as a LoadBalancer, and retrieve the admin password for you to access the ArgoCD UI.
