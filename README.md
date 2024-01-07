# awseks

### Step 1: Create IAM User for AWS CLI

1. Navigate to and select "IAM" from the main dashboard.

<img src="src/01.png"/>

2. Within IAM, locate and click on "Users" in the left navigation pane, then proceed by clicking on "Create User."

<img src="src/02.png"/>

3. Enter the desired username in the provided field, then click "Next" to continue.

<img src="src/03.png"/>

4. In the permissions section, choose "Attach policies directly." Search for "AdministratorAccess," select it, and then click "Next."

<img src="src/04.png"/>

5. Review all the details for accuracy and click on "Create user" to finalize the process.

<img src="src/05.png"/>

6. Once the user is created, click on the newly created user's name to view their profile.

<img src="src/06.png"/>

7. In the user's profile, navigate to the "Security Credentials" tab, under "Access Keys" section click on "Create Access Key."
 
<img src="src/07.png"/>

8. For the use case, select "Command Line Interface (CLI)," check the confirmation box, and then click "Next."
 
<img src="src/08.png"/>

9. Skip the option to add a description tag by clicking on "Create Access Key."
 
<img src="src/09.png"/>

10. Carefully copy the displayed "Access Key" and "Secret Access Key," and securely store them for future use.
 
<img src="src/10.png"/>

-

### Step 2: Create IAM Roles for Cluster and Worker Node

1. Access IAM and from the left sidebar, choose "Roles" followed by "Create role."

<img src="src/11.png"/>

2. For the Trusted entity type, select "AWS service." Under the use case, choose "EKS" and then "EKS - Cluster." Click "Next" to proceed.

<img src="src/12.png"/>

3. "AmazonEKSClusterPolicy" will be pre-selected by default. Click "Next" to move forward.

<img src="src/13.png"/>

4. Enter "EKS-Cluster-Role" as the role name and finalize the process by clicking "Create role."

<img src="src/14.png"/>

5. Return to the main dashboard and click on the "Create role" button once more.

<img src="src/15.png"/>

6. Again, select "AWS service" as the Trusted entity type. Under the use case, choose "EC2" and then "EC2" again. Click "Next" to continue.
- For permissions policies, select "AmazonEc2ContainerReadOnly," "AmazonEKS_CNI_Policy," and "AmazonEKSWorkerNodePolicy."

<img src="src/16.png"/>

7. Name this role "EKS-Worker-Node-Role" and complete the creation by clicking on "Create role."

<img src="src/17.png"/>

8. The roles are now successfully established.

<img src="src/18.png"/>


-

<img src="src/19.png"/>



<img src="src/20.png"/>

-

<img src="src/21.png"/>

<img src="src/22.png"/>

<img src="src/23.png"/>

<img src="src/24.png"/>

<img src="src/25.png"/>

-

<img src="src/26.png"/>

<img src="src/27.png"/>

<img src="src/28.png"/>

<img src="src/29.png"/>

<img src="src/30.png"/>

-

<img src="src/31.png"/>

<img src="src/32.png"/>

<img src="src/33.png"/>

<img src="src/34.png"/>

<img src="src/35.png"/>

-

<img src="src/36.png"/>

<img src="src/37.png"/>

<img src="src/38.png"/>

<img src="src/39.png"/>
