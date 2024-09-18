---
 layout: post
 title: Active-directory
---

**Active Directory (AD)** is a directory service developed by Microsoft for Windows domain networks. It provides a central repository for managing and organizing users, computers, groups, and other resources in a network. Active Directory handles authentication, authorization, and directory services, allowing administrators to control access to resources, enforce policies, and manage the network structure efficiently.

### Key Functions of Active Directory:
- **Authentication**: Verifies user identities using credentials (username and password).
- **Authorization**: Controls access to resources based on user roles and permissions.
- **Directory Services**: Stores and organizes information about objects in a network (e.g., users, groups, devices).
- **Group Policies**: Enforces security and configuration settings across the network.

### Types of Active Directory Services:

1. **Active Directory Domain Services (AD DS)**:
   - The core component of Active Directory that manages and stores information about network resources and application data.
   - Provides authentication and authorization services.
   - **Example**: A centralized system to manage user login permissions, passwords, and access to shared resources.

2. **Active Directory Lightweight Directory Services (AD LDS)**:
   - A lightweight version of AD DS.
   - Designed for applications that require directory-enabled capabilities without the need for a full domain setup.
   - Supports multiple instances on the same machine, making it flexible for use with web applications or in environments where full AD DS is not needed.

3. **Active Directory Federation Services (AD FS)**:
   - Provides single sign-on (SSO) capabilities across multiple systems and domains, including external systems or services (e.g., cloud services).
   - Enables secure sharing of identity information between trusted organizations (federated systems).
   - **Example**: Allowing users to authenticate into third-party services like Microsoft 365 with their corporate credentials.

4. **Active Directory Certificate Services (AD CS)**:
   - Manages public key infrastructure (PKI) to issue, manage, and revoke digital certificates.
   - Used for securing data through encryption, SSL/TLS certificates, and email security.
   - **Example**: Issuing SSL certificates for securing internal websites or encrypting data transmissions.

5. **Active Directory Rights Management Services (AD RMS)**:
   - Provides information protection by securing and controlling how files and documents are used and shared within the network.
   - Helps to prevent unauthorized access to sensitive information, even when files are shared outside the organization.
   - **Example**: Controlling who can view, edit, print, or forward a document.

---
