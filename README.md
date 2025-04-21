# AWS CI/CD Pipeline: Code Deployment to EC2 Instance

This project demonstrates a complete CI/CD pipeline using **AWS CodeDeploy**, **CodePipeline**, and **EC2** to automate the deployment of a static website.

## 🧰 Tech Stack

- **AWS EC2** - Hosting the application
- **AWS CodeDeploy** - Deployment service
- **AWS CodePipeline** - CI/CD pipeline
- **GitHub** - Source code repository
- **Apache HTTP Server** - Web server to serve HTML content
- **Amazon Linux 2023** - OS for the EC2 instance

## 📁 Project Structure

AWS-CI-CD-Pipeline-Code-Deployment-to-AWS-EC2-Instance/ ├── appspec.yml # AWS CodeDeploy config ├── index.html # Static HTML file to be deployed ├── scripts/ │ ├── install_dependencies.sh # Installs Apache and required packages │ ├── start_server.sh # Starts Apache web server │ └── stop_server.sh # Stops Apache web server

yaml
Copy
Edit

## 🚀 Deployment Steps

### 1. Launch an EC2 Instance

- OS: Amazon Linux 2023
- Install Apache manually:
  ```bash
  sudo yum update -y
  sudo yum install httpd -y
  sudo systemctl enable httpd
2. Install CodeDeploy Agent
bash
Copy
Edit
sudo yum install ruby -y
sudo yum install wget -y
cd /home/ec2-user
wget https://aws-codedeploy-us-east-1.s3.us-east-1.amazonaws.com/latest/install
chmod +x ./install
sudo ./install auto
sudo systemctl start codedeploy-agent
3. Configure IAM Role
Attach an IAM role with the following policies:

AmazonEC2RoleforAWSCodeDeploy

AmazonS3ReadOnlyAccess

AWSCodeDeployFullAccess

4. Setup CodeDeploy
Create a CodeDeploy application and deployment group in AWS Console.

Choose "GitHub" as the source provider.

5. Setup CodePipeline
Use the AWS Console to create a pipeline:

Source: GitHub

Build: (Skip or use CodeBuild if needed)

Deploy: AWS CodeDeploy

6. Push Code to GitHub
Any changes pushed to this repository will automatically trigger the pipeline and deploy the latest code to your EC2 instance.

📌 Notes
Make sure port 80 is open in the EC2 security group.

Ensure that the EC2 instance has the correct permissions and Apache is running.

🙌 Acknowledgements
AWS Documentation

CodeDeploy User Guide
