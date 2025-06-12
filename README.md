## Deploy an EKS cluster using eksctl command
Create the necessary configuration in cluster.yaml

#### Create a Jenkinsfile for running eksctl command for deployment of EKS cluster:
1. Create a pipeline.
2. Set relevant environment variables.
3. Create various stages within the pipeline:
   - Checkout code from the repository.
   - Install kubectl.
   - Install eksectl.
   - Create the EKS cluster using eksctl command.
   - NOTE that the scripts cannot be executed using sudo or root access.
  
#### Setup Jenkins pipeline:
1. Login to the Jenkins server.
2. Install necessary plugins using Manage Jenkins -> Plugins option.
3. Add Github credentials in Jenkins -> Manage Jenkins -> Credentials -> Add Credentials -> Kind (Username and Password).
4. Add DockerHub credentials in Jenkins -> Manage Jenkins -> Credentials -> Add Credentials -> Kind (Username and Password).
5. Add AWS credentials in Jenkins -> Manage Jenkins -> Credentials -> Add Credentials -> Kind (AWS Credentials).
6. Create a Jenkins pipeline using **New Item** option.
7. Set this repository as the SCM source with necessary GIT settings.
8. Set the Script Path as Jenkinsfile using Pipeline -> Pipeline script from SCM section.
9. Save the changes and click **Build Now** to trigger the pipeline.
10. Check the Console Output associated with the lastest job for verification.
11. Also verify the CloudFormation stack progress and EKS cluster creation progress in the AWS management console in the selected region.
