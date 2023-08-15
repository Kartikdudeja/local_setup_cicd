# Setting Up Jenkins, SonarQube, and Nexus with Vagrant for CI/CD Pipeline Project

This repository provides Vagrant configurations to set up Jenkins, SonarQube, and Nexus for creating a Continuous Integration/Continuous Deployment (CI/CD) pipeline environment. With Vagrant, you can easily provision a local development environment that includes these tools to simulate your CI/CD pipeline.

## Prerequisites

Before you begin, make sure you have the following prerequisites:

- [Vagrant](https://www.vagrantup.com/downloads) installed on your local machine.
- [VirtualBox](https://www.virtualbox.org/) or another supported provider installed.

## Getting Started

1. Clone this repository:

   ```bash
   git clone https://github.com/Kartikdudeja/vagrant-ci-cd-pipeline.git
   ```
   
2. Navigate to the project directory:

   ```bash
   cd vagrant-ci-cd-pipeline
   ```

3. Start the Vagrant environment:

   ```bash
   vagrant up
   ```

   This will create and provision the virtual machines for Jenkins, SonarQube, and Nexus.

4. Access the tools:

   - Jenkins: Open your web browser and navigate to `http://localhost:8080` to access Jenkins.
   - SonarQube: Visit `http://localhost:9000` to access SonarQube.
   - Nexus: Access Nexus at `http://localhost:8081`.
  
## Project Structure

The project directory is structured as follows:

```
vagrant-ci-cd-pipeline/
├── Vagrantfile
├── provision/
│   ├── jenkins.sh
│   ├── sonarqube.sh
│   ├── nexus.sh
│   └── blank.sh
└── README.md
```

- `Vagrantfile`: Defines the virtual machines and their provisioning settings.
- `provision/`: Directory containing provisioning scripts for each tool.

## Customization

You can customize the provisioning scripts in the `provision/` directory to match your specific requirements. You can also modify the `Vagrantfile` to adjust virtual machine settings.
