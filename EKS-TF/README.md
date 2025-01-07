Create your 
code with Terraform and push into your github accounts.


<img width="960" alt="2025-01-07 (21)" src="https://github.com/user-attachments/assets/564be10a-2ec9-4849-825d-e55d52f91399" />


**Step1:** Sign into your AWS account if you dont have you can create a free account.

**STEP2:** Launch an Instance and follow the guidelines 

<img width="960" alt="2025-01-07 (22)" src="https://github.com/user-attachments/assets/7dabbebd-7206-484a-a60d-a3e8cbd10cbe" />


**STEP3:** connect to the server.
ssh -i "project3.pem" ubuntu@ec2-54-183-247-121.us-west-1.compute.amazonaws.com



<img width="960" alt="2025-01-07 (23)" src="https://github.com/user-attachments/assets/e620cc3e-dd03-415b-a3ba-09f96b1e0c3c" />

**STEP4**
****INSTALL DOCKER**
 Update Your System
Run the following commands to ensure your system is up-to-date:
sudo apt update
sudo apt upgrade -y

 Install Dependencies
Install required dependencies for adding a new repository:
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common

Add Docker's Official GPG Key
Add the official Docker GPG key to your system:
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

Add Docker's Official Repository
Add the Docker repository to your APT sources:

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

 Install Docker
Update your package list and install Docker:
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io

Verify Installation
Check if Docker is installed and running:
docker --version
sudo systemctl status docker

 Enable and Start Docker
Ensure Docker starts automatically on boot:
sudo systemctl enable docker
sudo systemctl start docker

**INSTALL TERRAFORM**
 Add the HashiCorp GPG Key
wget -O- https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
Correction: Ensure you use double dashes (--dearmor) for the gpg command.
Add the HashiCorp Repository
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list

 Update Package Lists
sudo apt update
sudo apt install terraform -y

 Verify Installation
After installation, verify the version of Terraform:
terraform --version

**INSTALL AWSCLI**
 Download the AWS CLI Installer
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"

 Install unzip (if not already installed)
sudo apt-get install unzip -y
Unzip the AWS CLI Installer

 unzip awscliv2.zip
Run the AWS CLI Installer
sudo ./aws/install

Verify Installation
Check if the AWS CLI is installed correctly:
aws --version
You should see output similar to:
aws-cli/2.x.x Python/3.x.x Linux/x86_64

**INSTAL KUBECTL (KUBENETTES)**
 Install curl This command installs the curl utility, which is required to download files.
sudo apt install curl -y

Download the Latest kubectl Binary
This command downloads the latest stable version of kubectl for Linux (amd64 architecture):
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
Verify Installation
Check if kubectl is installed and accessible:
kubectl version --client

**STEP3** → IAM Role for EC2
IAM role for EC2 → It is used by your ec2 instance to create EKS cluster and manage s3 bucket by applying this IAM role it gives the authenticity to your ec2 to do changes in aws account
Aws dashboard search for and click on it IAM
Create Role
- Click on aws service
- user case - Ec2
- permission- choose administrator acceess

  
<img width="960" alt="2025-01-07 (22)" src="https://github.com/user-attachments/assets/3bb81582-9b1d-428c-9966-9e997f38a080" />

-click on next give your role name
  click on create role
 ** Next step: attach IAM role to Ec2 instance**
  - go to instancce Ec2 section
  - click on action
  - security
  - modifify IAM role
  - click on your role name -mario-game

    
<img width="960" alt="2025-01-07 (26)" src="https://github.com/user-attachments/assets/e4c48c5d-0d63-4030-85ed-88cbc57092d8" />

**STEP4**
Back to the terminal and Create a directory, you can give any name.
mkdir mario-game
cd mario-game 
clone the reposotpry from github
 git clone https://github.com/etaoko333/Deployment-of-super-Mario-on-Kubernetes-using-terraform.git

<img width="960" alt="2025-01-07 (27)" src="https://github.com/user-attachments/assets/b488f074-b5e2-4525-88a6-233867795bcb" />

cd EKS-TF
vim backend to edit your zone
click i - insert mode
esc - to save 
:wq - to exit vim editor
terraform init


<img width="960" alt="2025-01-07 (28)" src="https://github.com/user-attachments/assets/06c09dbb-bdbe-4c4d-b5f4-b59e22ab9faf" />

terraform plan


<img width="960" alt="2025-01-07 (29)" src="https://github.com/user-attachments/assets/8a997a06-327d-4d3d-a920-aa75e88eb3a4" />


terraform apply


<img width="960" alt="2025-01-07 (30)" src="https://github.com/user-attachments/assets/fc4243b9-1a41-4598-8b4e-5e435563ed9b" />

Run this command: This specifies that you're using the AWS CLI to interact with the Amazon Elastic Kubernetes Service (EKS).
aws eks update-kubeconfig --name EKS_CLOUD --region us-west-1


<img width="960" alt="2025-01-07 (31)" src="https://github.com/user-attachments/assets/e2994a55-f8bd-498c-8a51-a43eb4532a12" />


Step 5 → Creation of deployment and service for EKS
change the directory where deployment and service files are stored use the 

create the deployment
kubectl apply -f deployment.yaml 
kubectl apply -f service.yaml

<img width="960" alt="2025-01-07 (31)" src="https://github.com/user-attachments/assets/36b6c9d4-5b1d-4a35-8479-9a0a5d183f01" />

Run this command to get all the running pods.
run → kubectl get all


<img width="960" alt="2025-01-07 (32)" src="https://github.com/user-attachments/assets/9bc61f51-7f79-4309-9789-8333617dfce1" />


Run this command to get your loadbalamcer
kubectl describe service mario-service


<img width="960" alt="2025-01-07 (33)" src="https://github.com/user-attachments/assets/f3a9aa4a-07b1-45c0-94d0-c7bb17caa0dd" />





Step 6 → Destroy all the Insrastructure
kubectl delete service mario-service
kubectl delete deployment mario-deployment
cd EKS-TF
terraform destroy --auto-approve


