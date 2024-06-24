---
 layout: post
 title: Openstack
---
 - OpenStack is a free and open-source platform that allows you to create and manage public and private clouds.
   It provides a range of software tools for managing compute, storage, and networking resources within a data center. OpenStack is designed to be highly scalable and flexible, enabling users to build and manage large-scale cloud environments.

---
 - Core Components of OpenStack

   -  **Horizon (Dashboard - GUI interface service):** Web-based interface for managing OpenStack services.
   -  **Keystone (Identity Service ):** Centralized service for authentication and authorization of OpenStack 
        services and for managing users, projects, and roles.
   -  **Nova (ComputeService ):** Manages and provisions virtual machines (VMs) and other instances.
   -  **Glance (Image Service):** Stores and retrieves disk images for instances.
   -  **Neutron (Networking Service):** Neutron is a software-defined networking service that helps to create
        networks, subnets, routers, and floating IP addresses
   -   Provides connectivity between the interfaces of OpenStack services.
   -  **Cinder (Block Storage Service):**  Manages block storage devices for use with instances.
   -  **Swift (Object Storage Service):** Stores and retrieves unstructured data objects.
   -    Example- S3 service in AWS Cloud , google drive, drop box and other cloud based online storage.
   -  **Heat (Orchestration):** Automates the deployment of infrastructure through templates.
   -  **Ceilometer (Telemetry):** Collects and stores usage data for billing and monitoring.

   ---
    - Installation

    ---
      - Update the system:
        $ apt-get update -y
        $ sudo apt update -y
        $ sudo apt upgrade -y

      - Install necessary dependencies:
        $ sudo apt install -y python3-dev python3-pip git

      - Install MicroStack

      - Install Snap package manager (if not already installed):
        $ sudo apt install snapd -y
  
      - Install MicroStack:
        $ sudo snap install microstack --devmode --beta

      - To list Microstack:
        $ snap list microstack

      - Initialize MicroStack:
        $ sudo microstack init --auto --control 

     - To check version ofmicrostack.openstack:
       $ microstack.openstack --version

     - To show all images of openstack:
       $ microstack.openstack image list

     - to get admin password, login dashboard at https://machine-ip:
       $ sudo snap get microstack config.credentials.keystone-password

        - Example: password openstack for 140 ip core: 3OykUhX6iskmBF8T6E0SI4L7kdex4E0N

        