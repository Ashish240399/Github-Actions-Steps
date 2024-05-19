# Setting up GitHub Actions on AWS EC2

This guide will walk you through the process of setting up GitHub Actions on an AWS EC2 instance.

## Prerequisites

- An AWS account with permissions to manage EC2 instances
- A GitHub account with a repository for your project

## Steps

1. **Create an EC2 instance**

    Sign in to your AWS account, navigate to the EC2 dashboard, and initiate the creation of a new instance. Select an Amazon Machine Image (AMI) that fits your requirements. For instance, you might opt for an Ubuntu Server image.

2. **Establish SSH access**

    During the EC2 instance setup, you will be asked to generate a new key pair or use an existing one. This key pair enables SSH access to your EC2 instance. Ensure you download and securely store the key pair.

3. **Connect to your EC2 instance**

    Utilize an SSH client to establish a connection with your EC2 instance. The general command is `ssh -i /path/to/your/key.pem user@ec2-instance-ip-address`.

4. **Install necessary software**

    Your project may require certain software to be installed on your EC2 instance. This could include Git, Docker, Node.js, Python, etc.

    ### Docker Setup
    To install Docker, execute the following commands:
     - `sudo apt-get update`
     - `sudo apt-get install docker.io -y`
     - `sudo systemctl start docker`
     - `sudo docker run hello-world`
     - `docker ps`
     - `sudo chmod 666 /var/run/docker.sock`
     - `sudo systemctl enable docker`
     - `docker --version`

5. **Setup GitHub Runner**

    Navigate to your repository settings on GitHub, select the Actions tab, and then the Runners section. Click on "New self-hosted runner" and select Linux as the runner image. Copy the provided commands and execute them in the EC2 terminal.

6. **Run the GitHub Runner as a service**

    To install and start the GitHub Runner as a service, execute the following commands:
     - `sudo ./svc.sh install`
     - `sudo ./svc.sh start`

7. **Create workflows for GitHub Actions in the repository**

    Create a `.github` directory in your repository. Inside this directory, create a `workflows` directory. Within the `workflows` directory, create a `.yml` file and define your workflow conditions there.