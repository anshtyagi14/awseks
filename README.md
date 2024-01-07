# awseks

### Step 1: Create IAM User for AWS CLI

1. Navigate to and select `IAM` from the main dashboard.

<img src="src/01.png"/>

2. Within `IAM`, locate and click on `Users` in the left navigation pane, then proceed by clicking on "Create User'.

<img src="src/02.png"/>

3. Enter the desired username in the provided field, then click "Next" to continue.

<img src="src/03.png"/>

4. In the permissions section, choose `Attach policies directly`. Search for `AdministratorAccess`, select it, and then click "Next."

<img src="src/04.png"/>

5. Review all the details for accuracy and click on "Create user" to finalize the process.

<img src="src/05.png"/>

6. Once the user is created, click on the newly created user's name to view their profile.

<img src="src/06.png"/>

7. In the user's profile, navigate to the `Security Credentials` tab, under `Access Keys` section click on "Create Access Key".
 
<img src="src/07.png"/>

8. For the use case, select `Command Line Interface (CLI)`, check the confirmation box, and then click "Next."
 
<img src="src/08.png"/>

9. Skip the option to add a description tag by clicking on "Create Access Key."
 
<img src="src/09.png"/>

10. Carefully copy the displayed `Access key` and `Secret access key`, and securely store them for future use.
 
<img src="src/10.png"/>


-----


### Step 2: Create IAM Roles for Cluster and Worker Node

1. Access `IAM`, locate and click on `Roles` in the left navigation pane followed by "Create role".

<img src="src/11.png"/>

2. For the Trusted entity type, select `AWS service`. Under the use case, choose `EKS` and then `EKS - Cluster`. Click "Next" to proceed.

<img src="src/12.png"/>

3. `AmazonEKSClusterPolicy` will be pre-selected by default. Click "Next" to move forward.

<img src="src/13.png"/>

4. Enter `EKS-Cluster-Role` as the role name and finalize the process by clicking "Create role."

<img src="src/14.png"/>

5. Return to the main dashboard and click on the "Create role" button once more.

<img src="src/15.png"/>

6. Again, select `AWS service` as the Trusted entity type. Under the use case, choose `EC2` and then `EC2` again. Click "Next" to continue. For permissions policies, select `AmazonEC2ContainerReadOnly`, `AmazonEKS_CNI_Policy`, and `AmazonEKSWorkerNodePolicy`.

<img src="src/16.png"/>

7. Name this role `EKS-Worker-Node-Role` and complete the creation by clicking on "Create role."

<img src="src/17.png"/>

8. The roles are now successfully established.

<img src="src/18.png"/>


-----


### Step 3: Create EKS Cluster

1. Navigate to and select `Elastic Kubernetes Service` from the AWS Management Console.

<img src="src/19.png"/>

2. Within Elastic Kubernetes Service, click on `Clusters` in the left sidebar, then select "Add cluster" followed by the "Create" button.

<img src="src/20.png"/>

3. Enter a name for your cluster, choose the desired Kubernetes version, and select the previously created `EKS-Cluster-Role`. Click "Next" to proceed.

<img src="src/21.png"/>

4. Select the appropriate VPC, subnets, and security groups for your cluster configuration, then click "Next".

<img src="src/22.png"/>

5. Skip the observability options by clicking "Next", moving to the next configuration step.

<img src="src/23.png"/>

6. Notice that "Kube-proxy", "Amazon VPC CNI", and "CoreDNS" add-ons are pre-selected by default. Click "Next" to continue.

<img src="src/24.png"/>

7. Choose the specific versions for each of the add-ons: "Kube-proxy", "Amazon VPC CNI", and "CoreDNS".

<img src="src/25.png"/>

8. Review all configurations to ensure they are correct and click "Create." Wait for the cluster's status to transition from "Creating" to "Active," indicating your cluster is now successfully created.

<img src="src/26.png"/>


-----


### Step 4: Create Worker Node

1. Click on the name of the cluster you have previously created.

<img src="src/27.png"/>

2. Go to the `Compute` tab and, in the `Node groups` section, click on "Add node group."

<img src="src/28.png"/>

3. Enter a name for the node group, select the previously established `EKS-Worker-Node-Role` for the IAM role, and then click "Next."

<img src="src/29.png"/>

4. Choose the appropriate AMI type, Instance type, and Disk size. In the "Node group scaling configuration", set the desired, minimum, and maximum sizes of the node group, then click "Next."

<img src="src/30.png"/>

5. Select the subnets for the node group. The subnets chosen during the cluster creation will be automatically selected by default. Click "Next" to proceed.

<img src="src/31.png"/>

6. Review all your configurations for accuracy and then click "Create" to initiate the creation of the worker node.

<img src="src/32.png"/>

7. Wait for the node group's status to change to "Active" and for the nodes status to "Ready" indicating that they are ready for use.

<img src="src/33.png"/>


-----


### Step 5: Cluster access to IAM User

1. Revisit the previously created cluster by clicking on its name. In the `Access` tab, look for the `IAM access entries` section and select "Create access entry."

<img src="src/34.png"/>

2. From the "IAM principal" options, choose the IAM User you created earlier, then click "Next."

<img src="src/35.png"/>

3. In the access policies section, select `AmazonEKSClusterAdminPolicy`. Click "Add policy." Once the policy is listed under added policies, proceed by clicking "Next."

<img src="src/36.png"/>

4. Carefully review all the changes to ensure they are correct and then click "Create."

<img src="src/37.png"/>

5. After this process, you can confirm in the `IAM access entries` section that the `AmazonEKSClusterAdminPolicy` is now successfully attached to your IAM User.

<img src="src/38.png"/>


-----


### Step 6: Access cluster using AWS CLI and kubectl

1. Verify that both `awscli` and `kubectl` are installed on your system.
2. Execute the command `aws configure`. When prompted, enter the access key and secret access key you saved earlier during IAM user creation. Also, specify your cluster's region and set the output format to `json`.
3. To confirm the identity of your IAM User, run `aws sts get-caller-identity`.
4. Update your Kubernetes configuration by running `aws eks --region <cluster region> update-kubeconfig --name <cluster name>`, replacing `<cluster region>` and `<cluster name>` with your specific details.
5. Check if the correct cluster context is active by running `kubectl config get-contexts`.
6. To verify access to your cluster, execute `kubectl get svc` and review the displayed services.

<img src="src/39.png"/>
