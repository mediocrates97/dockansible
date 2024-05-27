# Containerized React Application with Ansible, Terraform, and Docker

This repository provides a step-by-step guide and accompanying code to containerize a React application and deploy it to an EC2 instance using Ansible, Terraform, and Docker. It covers the following tasks:

- Installing Node.js using Ansible roles

- Creating a Dockerfile for a React application

- Building and pushing the Docker image

- Using multi-stage builds

- Creating an EC2 instance using Terraform

- Configuring the EC2 instance with Ansible

## Prerequisites

Before you begin, ensure you have the following installed:

- Python (Ansible requires Python)

- Ansible

- Terraform

- Docker

## Getting Started

1\. **Install Node.js using Ansible Roles**

   - Install Ansible: `pip install ansible`

   - Create the Ansible role: Follow the steps in [`ansible/roles/nodejs/tasks/main.yml`](ansible/roles/nodejs/tasks/main.yml)

   - Create the Ansible playbook: [`ansible/install_nodejs.yml`](ansible/install_nodejs.yml)

   - Run the playbook: `ansible-playbook ansible/install_nodejs.yml`

2\. **Create a React Application and Dockerize it**

   - Create a React application: `npx create-react-app my-react-app`

   - Add the provided [`Dockerfile`](Dockerfile) to the root directory.

   - Build the Docker image: `docker build -t my-react-app:latest .`

   - Push the image to a registry: `docker push <your-dockerhub-username>/my-react-app:latest`

3\. **Create EC2 Instance using Terraform**

   - Create the Terraform configuration: [`terraform/main.tf`](terraform/main.tf)

   - Apply the configuration: `terraform init` and `terraform apply`

4\. **Configure EC2 Instance with Ansible**

   - Create the Ansible role: [`ansible/roles/nginx/tasks/main.yml`](ansible/roles/nginx/tasks/main.yml)

   - Create the Ansible playbook: [`ansible/configure_ec2.yml`](ansible/configure_ec2.yml)

   - Run the playbook: `ansible-playbook -i <ec2-public-ip>, ansible/configure_ec2.yml`

## Why Use Multi-Stage Docker Builds?

Using multi-stage Docker builds helps create lean and optimized Docker images. By separating the build and runtime stages, we can ensure that only the necessary files are included in the final image, reducing the image size and improving security. The build stage includes all the dependencies and tools needed to compile the application, while the runtime stage only contains the application files and the necessary runtime environment, resulting in a smaller and more efficient Docker image.

## Contributing

Contributions are welcome! If you find any issues or have suggestions for improvements, please open an issue or submit a pull request.

## License

This project is licensed under the [MIT License](LICENSE).

```
