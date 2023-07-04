# DevOps Flask Web App Deployment

This Ansible playbook automates the deployment of a Flask web application using Docker. The playbook can set up a build server to build the Docker image and push it to DockerHub. It also deploys the Docker image on a test server to run the Flask web application.

## Prerequisites

Before running this playbook, ensure that the following prerequisites are met on both the build and test servers:

- Operating System: CentOS 7 or compatible (with Python3 and Ansible installed).
- Docker: Install Docker on both servers, and ensure that Docker daemon is running.
- Git: Ensure Git is installed on the build server to clone the Flask web application code from the specified GitHub repository.

## Email Notification on Image Build Success
This Ansible playbook now includes an enhanced feature that sends email notifications whenever a Docker image build is successful on the build server. The email notification provides important details about the Docker image, making it easier to track successful builds and stay informed about the latest changes.

## Configuration

1. Clone this repository to your local machine:

```
git clone https://github.com/your-username/devops-flask-docker-playbook.git
cd devops-flask-docker-playbook
```

2. Update the `hosts` file:

In the `hosts` file, update the IP address of your build server under the `[build]` section, and the IP address of your test server under the `[test]` section. Make sure you have SSH access to the servers.

3. Update playbook variables:

In the `group_vars/all.yml` file, you can modify the following variables:

- `docker_user`: Replace with your DockerHub username.
- `docker_pass`: Replace with your DockerHub password or access token.

## Usage

### Step 1: Build and Push Docker Image

Run the following command to build the Docker image and push it to DockerHub from your build server:

```
ansible-playbook build-docker-image.yml
```

This playbook will install necessary packages (Docker, Git, and Python3), clone the Flask web application code from the specified GitHub repository, build the Docker image, and push it to DockerHub.

### Step 2: Deploy and Run Flask Web App

Run the following command to deploy and run the Flask web application on your test server:

```
ansible-playbook run-docker-container.yml
```

This playbook will install necessary packages (Docker and Python3), pull the Docker image from DockerHub, and run the Flask web application as a Docker container on port 80.

## Additional Information

- The `build-docker-image.yml` playbook handles the setup of the build server, the cloning of the Flask web application code, building the Docker image, and pushing it to DockerHub.
- The `run-docker-container.yml` playbook handles the setup of the test server and running the Flask web application as a Docker container.

Make sure to customize the playbook variables and configurations based on your specific requirements.

If you encounter any issues or have suggestions for improvements, please feel free to open an issue or submit a pull request.

Happy deployment!
