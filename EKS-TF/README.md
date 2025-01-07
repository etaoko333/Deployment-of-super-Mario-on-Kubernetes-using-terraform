
Step 1: Update Your System
Run the following commands to ensure your system is up-to-date:
sudo apt update
sudo apt upgrade -y

Step 2: Install Dependencies
Install required dependencies for adding a new repository:
sudo apt install -y apt-transport-https ca-certificates curl software-prope


The error indicates that the docker.io package is not available from the repositories configured on your system. This could happen for several reasons, such as incorrect or missing repository configurations, or using an outdated or unsupported Ubuntu version.

Here’s how you can resolve the issue and install Docker:

Step 1: Update Your System
Run the following commands to ensure your system is up-to-date:

bash
Copy code
sudo apt update
sudo apt upgrade -y
Step 2: Install Dependencies
Install required dependencies for adding a new repository:
sudo apt install -y apt-transport-https ca-certificates curl software properties-common

Step 3: Add Docker's Official GPG Key
Add the official Docker GPG key to your system:

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg


The error indicates that the docker.io package is not available from the repositories configured on your system. This could happen for several reasons, such as incorrect or missing repository configurations, or using an outdated or unsupported Ubuntu version.

Here’s how you can resolve the issue and install Docker:

Step 1: Update Your System
Run the following commands to ensure your system is up-to-date:

bash
Copy code
sudo apt update
sudo apt upgrade -y
Step 2: Install Dependencies
Install required dependencies for adding a new repository:

bash
Copy code
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
Step 3: Add Docker's Official GPG Key
Add the official Docker GPG key to your system:

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

Step 4: Add Docker's Official Repository
Add the Docker repository to your APT sources:

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
Step 5: Install Docker
Update your package list and install Docker:

sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io
Step 6: Verify Installation
Check if Docker is installed and running:

docker --version
sudo systemctl status docker
Step 7: Enable and Start Docker
Ensure Docker starts automatically on boot:

Copy code
sudo systemctl enable docker
sudo systemctl start docker

Install Terraform
Add the HashiCorp GPG Key
wget -O- https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
Correction: Ensure you use double dashes (--dearmor) for the gpg command.

Add the HashiCorp Repository
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list

Next Steps
Update Package Lists

sudo apt update
Install Terraform

sudo apt install terraform -y
Verify Installation
After installation, verify the version of Terraform:
terraform --version

Download the AWS CLI Installer

bash
Copy code
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
Install unzip (if not already installed)

bash
Copy code
sudo apt-get install unzip -y
Unzip the AWS CLI Installer

bash
Copy code
unzip awscliv2.zip
Run the AWS CLI Installer

bash
Copy code
sudo ./aws/install
Verify Installation
Check if the AWS CLI is installed correctly:

bash
Copy code
aws --version
You should see output similar to:

bash
Copy code
aws-cli/2.x.x Python/3.x.x Linux/x86_64

Install curl
This command installs the curl utility, which is required to download files.

bash
Copy code
sudo apt install curl -y
Download the Latest kubectl Binary
This command downloads the latest stable version of kubectl for Linux (amd64 architecture):

bash
Copy code
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
Install kubectl
This command installs the downloaded kubectl binary to /usr/local/bin with appropriate permissions:

bash
Copy code
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
Verify Installation
Check if kubectl is installed and accessible:

bash
Copy code
kubectl version --client


