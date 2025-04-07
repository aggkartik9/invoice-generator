# 🚀 React App Deployment using Docker & Jenkins
This project demonstrates how to build and deploy a React application using Docker and Jenkins, without using Kubernetes, Terraform, or Ansible.

The app is built using React, served with Nginx, and packaged inside a Docker container. Jenkins automates the CI/CD pipeline, handling everything from code checkout to deployment. Docker ensures the application is containerized for consistent delivery across environments.

The project includes:

A Dockerfile using a multi-stage build to compile and serve the app

Nginx configuration to serve the React app

A Jenkins pipeline (Jenkinsfile) that automates build and deployment steps

Optional integration points for GitHub

This setup allows developers to continuously deliver updates to the application with minimal manual intervention.
