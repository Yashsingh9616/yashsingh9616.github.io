---
 layout: post
 title: OpenShift
---

**OpenShift** is an enterprise-grade Kubernetes platform developed by Red Hat. It provides a comprehensive, automated, and secure environment for managing containerized applications, making it suitable for building, deploying, and scaling applications in a cloud or on-premises infrastructure.

### Key Features of OpenShift:
1. **Kubernetes-Based Platform**: OpenShift is built on Kubernetes and extends its capabilities, offering additional enterprise features like enhanced security, monitoring, and developer-friendly tools.
   
2. **PaaS (Platform as a Service)**: OpenShift offers a PaaS model, which simplifies application deployment by abstracting underlying infrastructure complexities, allowing developers to focus on code while the platform handles the rest.

3. **Multi-Cloud and Hybrid Cloud Support**: OpenShift supports deployment in various environments, including public clouds (AWS, Azure, GCP), private clouds, or hybrid setups, providing flexibility and portability.

4. **Built-in CI/CD Tools**: OpenShift integrates with Jenkins and other CI/CD tools, enabling automated builds, deployments, and version management of applications.

5. **Security and Compliance**: OpenShift includes enhanced security features, such as built-in authentication, role-based access control (RBAC), and automated certificate management to meet enterprise security requirements.

6. **Developer Tools**: It provides an integrated web console, command-line interface (CLI), and a developer-friendly experience with features like source-to-image (S2I), which automates the process of creating Docker images from source code.

7. **Operator Framework**: OpenShift supports Kubernetes Operators, which automate the management of complex applications. Operators extend the capabilities of Kubernetes by enabling the lifecycle management of applications and services.

8. **Container Orchestration**: As a Kubernetes-based platform, OpenShift offers features like container scheduling, scaling, and automated updates, simplifying the deployment and management of microservices and containerized applications.

9. **Integrated Networking and Storage**: OpenShift provides software-defined networking (SDN) and persistent storage options, enabling seamless communication between applications and persistent storage for stateful applications.

### OpenShift Components:
1. **OpenShift Container Platform**: The core product that provides Kubernetes with additional enterprise features.
2. **OpenShift Origin (OKD)**: The open-source version of OpenShift.
3. **OpenShift Online**: A hosted version of OpenShift that runs on the public cloud.
4. **OpenShift Dedicated**: A managed OpenShift cluster running on public clouds, managed by Red Hat.

### Typical Use Cases:
- **Application Modernization**: OpenShift helps enterprises transition from monolithic to microservices architecture.
- **DevOps & CI/CD**: OpenShift’s built-in tools and integrations streamline DevOps workflows.
- **Hybrid Cloud Deployments**: OpenShift enables consistent application deployment across cloud and on-premise infrastructures.
  




###############################################################################################################################################################################################################################################




To set up OpenShift with **1 master** and **2 worker nodes** on Ubuntu, you need a more extensive setup than the local development environment provided by CodeReady Containers (CRC). This guide will focus on deploying an OpenShift cluster using **`openshift-install`** with multiple nodes (one master and two worker nodes) on Ubuntu. The setup involves configuring the control plane (master) and worker nodes manually, often using virtual machines or cloud infrastructure (such as AWS, GCP, or VMware).

Here are the step-by-step instructions for setting up OpenShift with one master node and two worker nodes using **Red Hat OpenShift 4.x** on Ubuntu.

### Prerequisites

1. **Operating System**: Ubuntu 20.04 or later.
2. **Node Requirements**:
   - **Master Node**: Minimum 4 CPUs, 16 GB RAM, and 120 GB disk space.
   - **Worker Nodes**: Minimum 2 CPUs, 8 GB RAM, and 100 GB disk space each.
3. **Domain Name**: A fully qualified domain name (FQDN) is recommended. You can use a public domain or set up a local domain using `/etc/hosts`.
4. **Internet Access**: The nodes need access to the internet to download packages and container images.
5. **DNS Configuration**: Ensure proper DNS setup or use `/etc/hosts` to map node hostnames to IP addresses.

### Step 1: Install Required Dependencies

Install dependencies on all nodes (master and workers):

```bash
sudo apt update
sudo apt install -y python3 python3-pip wget git net-tools bind-utils
```

Additionally, ensure Docker or Podman is installed:

```bash
sudo apt install -y docker.io
sudo systemctl start docker
sudo systemctl enable docker
```

### Step 2: Download the OpenShift Installer

1. Go to the [Red Hat OpenShift Downloads Page](https://cloud.redhat.com/openshift/install).
2. Select **Bare Metal** as the infrastructure.
3. Download the **OpenShift 4 CLI Tools** (`openshift-install` and `oc`).

Alternatively, you can download via `wget`:

```bash
wget https://mirror.openshift.com/pub/openshift-v4/clients/ocp/stable/openshift-install-linux.tar.gz
wget https://mirror.openshift.com/pub/openshift-v4/clients/ocp/stable/openshift-client-linux.tar.gz
```

Extract the binaries:

```bash
tar -xvf openshift-install-linux.tar.gz
tar -xvf openshift-client-linux.tar.gz
sudo mv openshift-install oc kubectl /usr/local/bin/
```

### Step 3: Create an OpenShift Cluster Configuration

Generate an OpenShift cluster configuration file using the `openshift-install` tool:

```bash
openshift-install create install-config
```

This command will prompt you for information such as the cluster name, domain, and platform. Choose **bare metal** or another appropriate platform, such as **AWS**, depending on your environment. The configuration file (`install-config.yaml`) will be created in your working directory.

Edit the configuration to define the master and worker nodes. A typical `install-config.yaml` file will look like this:

```yaml
apiVersion: v1
baseDomain: example.com    	-->> yoc can mention your domain name 
metadata:
  name: my-openshift-cluster
platform:
  none: {}  # Use 'none' for bare metal
controlPlane:
  name: master
  replicas: 1
compute:
- name: worker
  replicas: 2
networking:
  networkType: OpenShiftSDN
  clusterNetwork:
  - cidr: 10.128.0.0/14
    hostPrefix: 23
  serviceNetwork:
  - 172.30.0.0/16
```

ORRRRRR


//////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

apiVersion: v1
baseDomain: example.com 
controlPlane: 
  hyperthreading: Enabled   
  name: master
  platform:
    aws:
      zones:
      - us-west-2a
      - us-west-2b
      rootVolume:
        iops: 4000
        size: 500
        type: io1
      type: m5.xlarge 
  replicas: 3
compute: 
- hyperthreading: Enabled 
  name: worker
  platform:
    aws:
      rootVolume:
        iops: 2000
        size: 500
        type: io1 
      type: c5.4xlarge
      zones:
      - us-west-2c
  replicas: 3
metadata:
  name: test-cluster 
networking:
  clusterNetwork:
  - cidr: 10.128.0.0/14
    hostPrefix: 23
  machineCIDR: 10.0.0.0/16
  networkType: OpenShiftSDN
  serviceNetwork:
  - 172.30.0.0/16
platform:
  aws:
    region: us-west-2 
    userTags:
      adminContact: jdoe
      costCenter: 7536
pullSecret: '{"auths": ...}' 
sshKey: ssh-ed25519 AAAA... 


//////////////////////////////////////////////////////////////////////////////////////////////////////////////////////



### Step 4: Install OpenShift

Run the following command to start the installation process:

```bash
openshift-install create cluster --dir=<directory>
```

This will create and set up your OpenShift cluster. The installer will generate ignition configuration files for the master and worker nodes.

### Step 5: Set Up the Master Node

1. Use a virtual machine, physical server, or cloud instance to set up the master node.
2. Boot the master node using the ignition file generated by the installer for the master node.

To do this, use the generated `.ign` file for the master node, typically located in the `bootstrap.ign` file, and provide it during the boot process.

### Step 6: Set Up Worker Nodes

Repeat the same process for the worker nodes by booting them using the respective ignition files generated for the worker nodes.

### Step 7: Verify Cluster Setup

Once the cluster is set up, log into the OpenShift cluster using the `oc` command-line tool:

```bash
oc login -u kubeadmin -p <password> https://api.<cluster-name>.<base-domain>:6443
```

You can check the status of the nodes:

```bash
oc get nodes
```

This command should return a list of nodes (1 master and 2 workers) with a status of `Ready`.

### Step 8: Access the OpenShift Web Console

OpenShift provides a web-based management interface for managing the cluster. Use the console URL to access it:

```bash
https://console-openshift-console.apps.<cluster-name>.<base-domain>
```

Log in with the `kubeadmin` credentials provided during the installation process.

### Step 9: Post-Installation (Optional)

- **Scaling the Cluster**: You can scale the cluster by adding more worker nodes using the `oc scale` command.
- **Storage Setup**: OpenShift supports various storage solutions, such as NFS or GlusterFS. You'll need to configure storage based on your application's requirements.
- **Monitoring & Metrics**: OpenShift comes with built-in monitoring tools like Prometheus and Grafana, which you can configure for your applications.

### Summary of Commands:

1. **Install dependencies**:
   ```bash
   sudo apt update
   sudo apt install -y python3 python3-pip wget git net-tools bind-utils docker.io
   sudo systemctl start docker
   sudo systemctl enable docker
   ```

2. **Download and extract OpenShift installer**:
   ```bash
   wget https://mirror.openshift.com/pub/openshift-v4/clients/ocp/stable/openshift-install-linux.tar.gz
   wget https://mirror.openshift.com/pub/openshift-v4/clients/ocp/stable/openshift-client-linux.tar.gz
   tar -xvf openshift-install-linux.tar.gz
   tar -xvf openshift-client-linux.tar.gz
   sudo mv openshift-install oc kubectl /usr/local/bin/
   ```

3. **Create installation config**:
   ```bash
   openshift-install create install-config
   ```

4. **Install OpenShift cluster**:
   ```bash
   openshift-install create cluster --dir=<directory>
   ```

5. **Access OpenShift Console**:
   ```bash
   https://console-openshift-console.apps.<cluster-name>.<base-domain>
   ```

6. **Check nodes**:
   ```bash
   oc get nodes
   ```

This setup will create an OpenShift cluster with 1 master and 2 worker nodes. Make sure you adjust resources, DNS, and network configurations as needed based on your infrastructure.