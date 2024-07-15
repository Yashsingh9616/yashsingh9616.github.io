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
   -  **Trove (Database Service)** Trove is a database-as-a-service for OpenStack, providing scalable and reliable
        relational and non-relational database engines as a service.
   -  **Ironic (Bare Metal Service)** Ironic is the OpenStack bare metal provisioning service. It is used to 
        provision and manage physical machines instead of virtual machines.
   -  **Sahara (Data Processing Service)** Sahara provides data processing services, allowing users to deploy and 
         manage data processing frameworks like Hadoop, Spark, and Storm on OpenStack
   -  **Zaqar (Messaging Service)** Zaqar is the messaging service for OpenStack, providing multi-tenant cloud 
        messaging for web developers to communicate between distributed applications.
   -  **Barbican (Key Management Service)** Barbican is the key management service designed to manage and store 
        secrets, including passwords, encryption keys, and X.509 certificates.
   -  **Designate (DNS Service)** Designate provides DNS-as-a-service, offering a REST API for managing DNS zones 
        and record sets, and integrating with other OpenStack services.
   -  **Magnum (Container Orchestration Service)**  Magnum provides container orchestration engines like Kubernetes, 
        Swarm, and Mesos as first-class resources in OpenStack.
   -  **Manila (Shared File Systems Service)** Manila provides shared file systems as a service, enabling users to 
        provision and manage shared filesystems.
   -  **Murano (Application Catalog Service)** Murano provides an application catalog, allowing users to deploy and 
        manage applications in an OpenStack environment.
   -  **Aodh (Telemetry Alarming Service)** Aodh provides the alarming service for OpenStack Telemetry, allowing 
        users to set alarms based on defined rules against collected metering data.
   -  ** Gnocchi (Time Series Database Service)** Gnocchi is a multi-tenant timeseries, metrics, and resources 
         database. It is optimized for large-scale metric storage and retrieval.

  ---

    # Resource Quotas

     - In OpenStack, a resource quota is a limit on the amount of resources that a project (or tenant) can consume. These quotas are used to manage and restrict the resources consumed by users to ensure fair usage and prevent any single user or project from exhausting resources that are shared among many users.

    - Key Concepts of Resource Quotas
      - Projects (Tenants): Quotas are typically applied at the project level. Each project can have its own set of 
        quotas for different resources.
      - Resources: Quotas can be set for various resources such as instances (virtual machines), cores (vCPUs), RAM, 
        floating IPs, volumes, snapshots, and more.
      - Hard Limits: These are the maximum limits set for each resource. Users cannot exceed these limits unless the 
        quotas are adjusted.

    - Managing Resource Quotas
      Resource quotas can be managed via the OpenStack Dashboard (Horizon) or through the command-line interface (CLI).

      - Using the CLI
      - List Quotas: To list the quotas for a specific project:

        - #openstack quota show <<project_id>>
      - Update Quotas: To update the quotas for a specific project:

        - #openstack quota set --instances <<number>> --cores <<number>> --ram <<number>> <<project_id>>
    
    - Example:
      - openstack quota set --instances 10 --cores 20 --ram 51200 <<project_id>>
      - Delete Quotas: To delete quotas for a specific project (reset to defaults):

        - #openstack quota delete <<project_id>>   

    - Using the Horizon Dashboard
      - Log in to Horizon: Access the Horizon dashboard via your web browser.
      - Navigate to the Admin Panel: Go to the 'Admin' panel.
      - Projects: Select 'Projects' from the menu.
      - Modify Quotas: Choose the project you want to modify quotas for, and then select 'Modify Quotas'. Adjust the 
        quotas as needed and save the changes.

    - Default quotas provided in OpenStack:

      - Compute (Nova)
        - Instances: 10
        - Cores (vCPUs): 20
        - RAM: 50 GB (51200 MB)
        - Floating IPs: 10
        - Fixed IPs: Unlimited
        - Key Pairs: 100
        - Security Groups: 10
        - Security Group Rules: 20 per security group
        - Server Groups: 10
        - Server Group Members: 10
        - Block Storage (Cinder)
        - Volumes: 10
        - Snapshots: 10
        - Total Volume Storage: 1000 GB
      - Networking (Neutron)
        - Networks: 10
        - Subnets: 10
        - Ports: 50
        - Routers: 10
        - Floating IPs: 10
        - Security Groups: 10
        - Security Group Rules: 100 per security group
      - Object Storage (Swift)
        - Containers: 100
        - Objects: 100,000
      - Total Object Storage: Unlimited (controlled by container and object count)



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
    - $ microstack.openstack server add volume <<sinstance id>> newvolume
  
 - overview of how to configure, view, and store logs for all core OpenStack services.
  
  1. Keystone (Identity Service)
     - Configuration File: /etc/keystone/keystone.conf
     - Log File Location: /var/log/keystone/keystone.log

 1. Nova (Compute Service)
    - Configuration File: /etc/nova/nova.conf
    - Log File Location: /var/log/nova/nova.log  
  
  2. Neutron (Networking Service)
     - Configuration File: /etc/neutron/neutron.conf
     - Log File Location: /var/log/neutron/neutron.log
  
  3. Glance (Image Service)
     - Configuration File: /etc/glance/glance-api.conf
     - Log File Location: /var/log/glance/glance-api.log
  
 2. Cinder (Block Storage Service)
    - Configuration File: /etc/cinder/cinder.conf
    - Log File Location: /var/log/cinder/cinder.log

 3. Swift (Object Storage Service)
    - Configuration File: /etc/swift/swift.conf
    - Log File Location: /var/log/swift/*.log

 4. Heat (Orchestration Service)
    - Configuration File: /etc/heat/heat.conf
    - Log File Location: /var/log/heat/heat.log

 5. Horizon (Dashboard)
    - Configuration File: /etc/openstack-dashboard/local_settings.py
    - Log File Location: /var/log/horizon/horizon.log
  
  6. Trove (Database Service)
     - Configuration File: /etc/trove/trove.conf
     - Log File Location: /var/log/trove/trove.log
 
 6.  Ironic (Bare Metal Service)
     - Configuration File: /etc/ironic/ironic.conf
     - Log File Location: /var/log/ironic/ironic.log

 




























        



#####################################################################################################################