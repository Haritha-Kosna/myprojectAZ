# Deploying Static Website using Load Balancer by ARM Template

## Project Overview

**Brain Diseases** is a website that The brain is the most complex part of the human body. This three-pound organ is the seat of intelligence, interpreter of the senses, initiator of body movement, and controller of behavior. Lying in its bony shell and washed by protective fluid, the brain is the source of all the qualities that define our humanity. The site aims to simplify the decision-making process by providing users to get better treatment for brain related diseases. 

This project demonstrates the deployment of **Brain Diseases** using Azure's ARM templates and load balancing across two Virtual Machines (VMs) in different availability zones for high availability and scalability.

## Problem Statement

Your brain is your body’s control center. It’s part of the nervous system, which also includes the spinal cord and a large network of nerves and neurons. Together, the nervous system controls everything from your senses to the muscles throughout your body.

When your brain is damaged, it can affect many different things, including your memory, your sensation, and even your personality. Brain disorders include any conditions or disabilities that affect your brain. This includes conditions that are caused by:

Illness
Genetics
Traumatic injury

## Project Goals

- Deploy the ** Brain - Diseases ** website on Azure using ARM templates.
- Set up a **Virtual Network (VNet)** with two **Subnets** and a **Network Security Group (NSG)**.
- Use a **Load Balancer** to distribute traffic between two VMs located in different availability zones.
- Host the static website on these VMs and make it accessible via the load balancer's frontend IP.

## Technologies and Azure Services Used

1. **Azure CLI**: Used to create the resource group and Virtual Network.
2. **ARM Templates**: Automated the creation of VNet, subnets, and NSG.
3. **Azure Virtual Machines (VMs)**: Hosted the Sitara-Hotel website.
4. **Azure Load Balancer**: Distributed the traffic between two VMs to ensure high availability.
5. **Nginx**: Used as a web server on both VMs to serve the static content.
6. **Git**: Cloned the website from GitHub onto the VMs using a custom script.
7. **Custom Script Extension**: Used to automatically configure the VMs upon deployment.

## Project Steps

### 1. Website Development
- ** Brain - Diseases **: A static website allowing users to book doctor's appointment for brain diseases and pay for appointmentcharges online.

### 2. Deploying the Website on GitHub
- Frontend of  ** Brain - Diseases ** was uploaded to a public GitHub repository: [Brain-Diseases](https://github.com/Haritha-Kosna/myprojectAZ.git)

### 3. Azure Deployment Using ARM Templates
- **Resource Group**: Created using Azure CLI to hold all the resources.
- **Virtual Network (VNet)**: Set up using an ARM template, which included two subnets for distributing the VMs.
- **Network Security Group (NSG)**: Applied inbound rules to allow traffic on ports 22 (SSH) and 80 (HTTP).
  
### 4. Virtual Machines Setup
- **VM 1**: Created in Availability Zone 1 using Azure Portal. Configured with:
  - Custom Script Extension to clone the website from GitHub.
  - Networking settings to connect to the VNet and assigned Subnet.
  
 Custom Script:
  ```bash
  #!/bin/bash
  sudo apt update
  sudo apt install nginx git -y
  cd /tmp && git clone https://github.com/Haritha-Kosna/Brain-diseases.git mysite
  sudo rm -rf /var/www/html/index.nginx-debian.html
  sudo cp -r /tmp/mysite/* /var/www/html
  cd /var/www/html/
  sudo chown -R www-data:www-data /var/www/html
  sudo chmod -R 755 /var/www/html
  ```
- **VM 2**: Created in Availability Zone 2 with the same configuration as VM 1.

### 5. Load Balancer Configuration
- **Load Balancer**: Configured to distribute traffic between VM 1 and VM 2.
  - **Frontend IP Configuration**: Assigned a new frontend IP for external access.
  - **Backend Pool**: Added both VMs to the backend pool for traffic distribution.
  - **Load Balancing Rule**: Defined to balance HTTP traffic (port 80) across the VMs.
  - **Health Probe**: Set up to monitor the health of the VMs and ensure traffic is routed only to healthy VMs.

# Project Description:
The Brain Diseases Static Web Page project involves Reducing appropritate Brain Diseases for seniors and childrens. The project was deployed on Microsoft Azure using several core services to ensure scalability, reliability, and security.

The infrastructure includes a Virtual Network (VNET) with two subnets, ensuring network security and proper segmentation. Two Virtual Machines (VMs) were created manually and configured within an Availability Set to ensure high availability. A Load Balancer was set up to distribute traffic between the VMs, providing a seamless experience for users. The static web page was deployed using custom code and is hosted on these VMs, accessible via the Load Balancer.

## Azure Services and Tools Used

- **Azure CLI**: Resource group creation and management.
- **Azure Resource Manager (ARM) Templates**: Infrastructure-as-Code to deploy resources.
- **Virtual Network (VNet)**: Networking and subnetting.
- **Network Security Group (NSG)**: Security rules for VM access.
- **Azure Virtual Machines**: Hosting the website on multiple VMs.
- **Azure Load Balancer**: Load balancing between VMs.
- **Nginx**: Web server for hosting static content.
- **Git**: Version control and cloning the website onto VMs.
- **Custom Script Extension**: Automated configuration of VMs.

## Live Website and Resources

- **Website Link**: [Brain-Diseases](https://1drv.ms/v/c/a5bf4445a70cc8aa/EQnqn3qE2bRIjkfeN6yJdLsBJY_Via6aSi0XwNP2dYJsgw?e=MdEU6N)
- **Project Video**: [Project Video](https://1drv.ms/v/c/a5bf4445a70cc8aa/EWdhu_1YTh9Jr4A1hSxzl0EBXdOJ5VJ8VwlYw9UiEal1WQ?e=j7rhPO)
- **Screenshots**:
  **Created Resource Group Screenshot**
  - ![ResourceGroup Screenshot](https://github.com/Haritha-Kosna/myprojectAZ/blob/main/RG.png)
    
  **ResourceGroup Deployment Output**
  - ![RSG-Deployment-output Screenshot](https://github.com/Haritha-Kosna/myprojectAZ/blob/main/RGoutput.png)

  **VNet Subnets RSG ARM Template Output**
  - ![VNetDeploymentoutputSS Screenshot](https://github.com/Haritha-Kosna/myprojectAZ/blob/main/NSG&Vnet.png)

   **Created VNet Screenshot** 
  - ![VNetSS Screenshot](https://github.com/Haritha-Kosna/myprojectAZ/blob/main/Vnet.png)

  **Created Subnets Screenshot**
  - ![SubnetSS Screenshot](https://github.com/Haritha-Kosna/myprojectAZ/blob/main/subnet.png)

   **Deployed VM 1 Screenshot**
  - ![VM1SS Screenshot](https://github.com/Haritha-Kosna/myprojectAZ/blob/main/Vm1.png)

  **Deployed VM 2 Screenshot**
  - ![VM2SS Screenshot](https://github.com/Haritha-Kosna/myprojectAZ/blob/main/Vm2.png)

  **Deployed LoadBalancer Screenshot**
  - ![LoadbalancerSS Screenshot](https://github.com/Haritha-Kosna/myprojectAZ/blob/main/LoadBalancer.png)

  **Website Home Page Screenshot**
  - ![Brain-Diseases Homepage Screenshot](https://github.com/Haritha-Kosna/myprojectAZ/blob/main/Home.png)

  **Generate Book Now after complete Deployment**
  - ![GenerateOutfitsPage Screenshot](https://github.com/Haritha-Kosna/myprojectAZ/blob/main/contact.png)

  **About Doctor's suggestion Page after complete Deployment**
  - ![About appointment Page Screenshot](https://github.com/Haritha-Kosna/myprojectAZ/blob/main/Doctor.png)


## Conclusion

This project showcases the end-to-end process of deploying a static website using Azure's ARM templates and load balancing capabilities. By distributing traffic between two VMs in different availability zones, we ensure high availability and scalability for the **Brain-Diseases** platform. The integration of Azure's powerful tools and services simplified the deployment and configuration process.

## Author

**Kosna Haritha and Vadla Ruthuja**  
Deployed as group as part of learning Azure's cloud infrastructure.
