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

 ---
  - **If you get erroe like this**
      The request you have made requires authentication. (HTTP 401) (Request-ID: req-4f33ec46-4c40-4b30-888f-91d1a1dab1fc)  
    
      than you can use this command like this 

    - $ sudo microstack init --auto --control --setup-loop-based-cinder-lvm-backend --loop-device-file-size 70


 ---

  - List Available server:
    - $ microstack.openstack server list

  - List Available Services:
    - $ microstack.openstack service list

  - List Projects:
    - $ microstack.openstack project list

  - Create a New Project:
    - $ microstack.openstack project create myproject

  - List Users:
    - $ microstack.openstack user list

  - Create a New User:
    - $ microstack.openstack user create --project myproject --password mypassword myuser

  - List Available Images:
    - $ microstack.openstack image list

  - Upload a new image
    - $ microstack.openstack image create "Ubuntu 20.04" --file /path/to/ubuntu-20.04.qcow2 --disk-format qcow2 --container-format bare --public

     **or**

    - $ microstack.openstack image create "Ubuntu" --file /root/ubuntu-20.04.6-live-server-amd64.iso  
  --disk-format qcow2 --container-format bare --public

  - List Flavors:
    - $ microstack.openstack flavor list

  - Create a New Flavor:
    - $ microstack.openstack flavor create --ram 2048 --disk 20 --vcpus 2 myflavor

  - Create a Network:
    - $ microstack.openstack network create mynetwork

***********If you want to delete image,service,network,subnet, volume and so on************

    - $  microstack.openstack network delete mynetwork

  - Create a Subnet:
    - $ microstack.openstack subnet create --network mynetwork --subnet-range 192.168.0.0/24 mysubnet

  - Launch a New Instance:
    - $ microstack.openstack server create --flavor myflavor --image "Ubuntu 20.04" --network mynetwork myinstance

**or**

    - $ microstack.openstack server create --flavor myflavor --image "Ubuntu" --network mynetwork myvm


  - List Instances:
    - $ microstack.openstack server list

  - Show Instance Details:
    - $ microstack.openstack server show myinstance

  - Delete an Instance:
    - $ microstack.openstack server delete myinstance

  - List all volumes:
    - $ microstack.openstack volume list

  - Create a new volume:
    - $  microstack.openstack volume create --size 10 newvolume

  ***
   Attach a Volume to an Instance
  ***
  - List all instances to find the instance ID:
    - $ microstack.openstack server list

  - Attach the volume to an instance:
    - $ microstack.openstack server add volume <instance id> newvolume
        



#####################################################################################################################