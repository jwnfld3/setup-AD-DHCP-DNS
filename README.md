# Setting Up Active Directory, DHCP, and DNS on Windows Server 2022

## Summary

In this lab, Active Directory Domain Services (AD DS), DHCP, and DNS will be set up and configured on a Windows Server 2022 environment. These services are crucial for managing a networked environment, allowing centralized management of users, IP address allocation, and name resolution across a network.

## Lab Requirements

- A physical or virtual machine running **Windows Server 2022**.
- Access to **Server Manager** to install and configure roles.
- Basic knowledge of networking concepts, including IP addressing, subnets, and DNS.
- Administrator privileges on the server to perform role installations and configurations.

## Who, What, When, Where, Why

### Who
- **IT professionals** or **students** seeking to practice setting up essential network services like AD DS, DHCP, and DNS.
- **Network Administrators** interested in automating and managing their organization's infrastructure.

### What
- **Active Directory Domain Services (AD DS)** will be used to create a centralized directory for managing users and computers.
- **DHCP (Dynamic Host Configuration Protocol)** will be configured to automatically assign IP addresses to network devices.
- **DNS (Domain Name System)** will be set up to allow network devices to resolve domain names to IP addresses.

### When
- This lab is useful when setting up a new Windows Server for an organization or a practice environment.

### Where
- This lab is designed for use in a **virtual environment** (e.g., Hyper-V, VMware) or a **physical server** running Windows Server 2022.

### Why
- Setting up **Active Directory**, **DHCP**, and **DNS** is foundational for managing a network of computers and devices in an enterprise environment.
- These services are integral for **network security**, **resource management**, and **network stability**.

---

## Steps to Complete the Lab

### 1. **Install Active Directory Domain Services (AD DS)**

**Active Directory Domain Services (AD DS)** is a core component of Microsoft’s directory service, which provides centralized management and authentication for resources across a network. AD DS is responsible for storing and organizing information about networked resources such as users, computers, and services, and it facilitates access control and security policies.

**Key Features:**
- **Centralized Authentication**: AD DS provides a central authentication mechanism, where users log in with a single set of credentials to access network resources.
- **Directory Structure**: AD DS uses a hierarchical directory structure that includes domains, trees, and forests to organize resources.
- **Group Policies**: It allows for centralized management and configuration of operating systems, applications, and users through Group Policy Objects (GPOs).
- **Access Control**: It helps define who can access what resources on the network and under what conditions.

**Why it matters:**
AD DS is crucial for environments that require centralized management of users, computers, and other resources. It ensures security, simplifies administrative tasks, and allows for easier scalability as organizations grow.

**How it works:**
1. **Domain Controllers**: Servers running the AD DS role, which store the directory database and provide authentication services.
2. **Replication**: AD DS data is replicated across multiple domain controllers to ensure high availability.
3. **Security and Trusts**: AD DS supports the implementation of security policies and cross-domain trusts to enable access to resources across different domains.




#### Step 1: Install AD DS Role
1. Open **Server Manager** and click **Manage** > **Add Roles and Features**.
![image](https://github.com/user-attachments/assets/7c69a4e8-bc71-4afd-bcff-0eef781166ee)
![image](https://github.com/user-attachments/assets/f111417d-b36a-4390-a147-67471e9f0dba)

2. Choose **Role-based or feature-based installation**, then select the server and click **Next**.
![image](https://github.com/user-attachments/assets/8fc360ae-e30e-450b-8c4f-d059b314f9dd)
![image](https://github.com/user-attachments/assets/84870e15-369d-45e6-be40-9154ff2592a4)

3. In the **Roles** section, check **Active Directory Domain Services**. Click **Next**.

![image](https://github.com/user-attachments/assets/82238dd9-c8e8-46b6-aea0-f47fec4e7a70)
![image](https://github.com/user-attachments/assets/f8666a6d-c5a8-4008-b3b9-330f1caaecd6)
![image](https://github.com/user-attachments/assets/cec71e66-5b54-415d-8d54-abf48c585447)
![image](https://github.com/user-attachments/assets/4fed33d2-243d-4e5d-8d25-c7bee3f6f0a9)
![image](https://github.com/user-attachments/assets/0ea3486f-735d-426b-8fbd-4d169a000733)
![image](https://github.com/user-attachments/assets/9609b242-71de-45b2-ac15-f9758a63f39e)

4. Click **Install** to install the AD DS role. Wait for the installation to complete.
![image](https://github.com/user-attachments/assets/4a40a9cb-ed28-437d-8ba4-ff7c448386bb)


#### Step 2: Promote the Server to Domain Controller
1. After installation, click the notification flag in **Server Manager** and select **Promote this server to a domain controller**.
![image](https://github.com/user-attachments/assets/1e0636b3-ad7c-4cbd-bb0b-b1e12e2f1549)

2. Choose **Add a new forest**, then enter the **Root domain name** (e.g., **example.local**).
![image](https://github.com/user-attachments/assets/06a0959c-b4e7-445a-9347-018aa6b851d9)

3. Set the **Forest functional level** and **Domain functional level** to the appropriate version (e.g., Windows Server 2016 or higher).
4. Enter a **Directory Services Restore Mode (DSRM) password** and click **Next**.
![image](https://github.com/user-attachments/assets/42768bd6-beb4-4c10-8bee-0242e9b61708)
![image](https://github.com/user-attachments/assets/d783f817-9f98-47a7-94d5-cc7a8ac1621c)

5. Set the NetBIOS domain name.

***NetBIOS (Network Basic Input/Output System)***

This was widely used in early Windows networks and is still supported for backward compatibility. Some older applications, devices, or systems that haven't transitioned to DNS (Domain Name System) may still rely on NetBIOS names to identify and connect to resources on the network.
![image](https://github.com/user-attachments/assets/3b32e589-6da3-4104-bafa-4cd2e3081f7a)
![image](https://github.com/user-attachments/assets/7ba7a483-4f89-4961-8a77-15a3c0d9a456)
![image](https://github.com/user-attachments/assets/f5586158-b7ba-4b21-b291-8f7681c471ed)

6. Review the DNS options and it was discovered that a DNS server will be installed during the process.
![image](https://github.com/user-attachments/assets/9b6b886f-6738-44d7-871e-e1a9a87c56d2)
![image](https://github.com/user-attachments/assets/d421db5d-6399-4884-a256-763a9bcca104)

7. Review the configuration and click **Install**. The server will restart.
![image](https://github.com/user-attachments/assets/fb69ccf8-3a13-4c5e-9bc8-70a83d75d8de)

### 2. **Set Up a DHCP Server**

#### Step 1: Install the DHCP Server Role
1. Open **Server Manager** and click **Manage** > **Add Roles and Features**.
2. Select **Role-based or feature-based installation**, choose the server, and click **Next**.
![image](https://github.com/user-attachments/assets/1f8b77b8-c44d-4664-ad60-073897782341)
![image](https://github.com/user-attachments/assets/f111417d-b36a-4390-a147-67471e9f0dba)
![image](https://github.com/user-attachments/assets/84870e15-369d-45e6-be40-9154ff2592a4)

3. In the **Roles** section, check **DHCP Server**, then click **Next**.
![image](https://github.com/user-attachments/assets/40d915c3-f810-4553-a07f-99409e0a8077)
![image](https://github.com/user-attachments/assets/00b21d58-4192-4919-a78d-97d9bf2c007e)
![image](https://github.com/user-attachments/assets/2222aea0-c2d1-4616-b426-ef90410061cc)
![image](https://github.com/user-attachments/assets/9dd1bf83-2dee-4733-aabf-19536232e274)
![image](https://github.com/user-attachments/assets/31f911f5-1163-44f3-a3f3-ffc4302d47ea)

4. Click **Install** to install the DHCP role. Wait for the installation to complete.
![image](https://github.com/user-attachments/assets/cb8f9580-ca1a-45cf-b37a-45bc885f3a8a)
![image](https://github.com/user-attachments/assets/eea7e81e-32db-42bf-8fc1-6e9711ba5e5e)



#### Step 2: Configure the DHCP Server
1. Open the **DHCP Management Console** from **Server Manager** > **Tools** > **DHCP**.
![image](https://github.com/user-attachments/assets/b8e472c1-48a5-445a-ae40-a66024959744)

2. Right-click **IPv4** and select **New Scope**.
![image](https://github.com/user-attachments/assets/8b1cafa3-014a-45fe-8eea-77372d257d8d)
![image](https://github.com/user-attachments/assets/4b6c7114-2230-4764-8682-dd6cde12f035)
![image](https://github.com/user-attachments/assets/f3ef4a1f-d891-4f6d-b886-1f3bce1420fe)

3. Configure the scope by entering a **Start IP address**, **End IP address**, **Subnet Mask**, and any **Exclusions** for static IPs.
![image](https://github.com/user-attachments/assets/2df23822-a856-4aa4-9d84-4bee708a9e46)

Be sure to exclude the IP address of the server so there isn't an IP conflict.
![image](https://github.com/user-attachments/assets/a6088942-77f3-42a4-a16f-71c0f6b6e793)

4. Set the **Lease Duration** and configure the **DHCP Options** such as **Router** and **DNS servers**.
### Large Office/Corporate Network
In a larger network with many devices, such as in an office or enterprise environment, devices are typically more stable and remain connected for long periods of time. In this case, a longer lease duration is ideal.

**Recommended Lease Duration**: 1 day to 7 days

A longer lease ensures that devices don't need to renew leases too frequently, reducing the workload on the DHCP server. This is especially useful when most devices stay connected for extended periods (e.g., workstations, desktops, etc.).

![image](https://github.com/user-attachments/assets/257fad89-e29a-4ba6-8bb7-4cdcba401484)
![image](https://github.com/user-attachments/assets/9186dbba-ab14-4d09-abaa-8f38d3ce5ab9)

This is a virtual machine so this will not be required.
![image](https://github.com/user-attachments/assets/12b610e6-568f-4f93-931b-678c50a9bd79)
![image](https://github.com/user-attachments/assets/3d42afe0-d67c-434f-877c-09e1aad94c4a)
![image](https://github.com/user-attachments/assets/295d6f17-df60-4d56-b108-84b4875f4d0d)

5. Activate the scope and verify clients can obtain IP addresses.
![image](https://github.com/user-attachments/assets/dbcaf2ef-fb85-42e5-a318-357614c61467)
![image](https://github.com/user-attachments/assets/ad70e30a-aa1f-4da1-a68e-02dd29305202)
![image](https://github.com/user-attachments/assets/8fc360ae-e30e-450b-8c4f-d059b314f9dd)
![image](https://github.com/user-attachments/assets/84870e15-369d-45e6-be40-9154ff2592a4)


#### Step 2: Configure the DNS Server
1. Open the **DNS Management Console** from **Server Manager** > **Tools** > **DNS**.
![image](https://github.com/user-attachments/assets/84a284e9-c022-4c98-9a92-2d7e7288b4c2)

2. Right-click **Forward Lookup Zones** and select **New Zone**.
![image](https://github.com/user-attachments/assets/0ec25fb7-0078-489d-8200-2b1bc86caa08)
![image](https://github.com/user-attachments/assets/cb427e7b-2859-4af9-870f-8c89d384f23b)

3. Select **Primary Zone**, enter the **Zone Name** (e.g., **example.local**), and click **Next**.
![image](https://github.com/user-attachments/assets/719fc0cf-a9ff-42bc-9f5b-31817a8e62b0)
![image](https://github.com/user-attachments/assets/23762ba8-c48b-4eb7-8cf3-aca6cb92321e)
![image](https://github.com/user-attachments/assets/6ffca554-59c7-4428-bcef-11d210f01125)
![image](https://github.com/user-attachments/assets/5adbf34a-5334-462e-b866-25cca2f6ad5d)
![image](https://github.com/user-attachments/assets/a62c6172-76c9-4ac6-94bf-5e2762a7d438)


---

## Lab Conclusion

At the end of this lab, **Active Directory Domain Services (AD DS)**, **DHCP**, and **DNS** will be successfully installed and configured on a Windows Server 2022 machine. These services provide essential network functionality, allowing for centralized management of users, dynamic IP address assignment, and domain name resolution across the network.

---

## Additional Resources

- [DHCP Server Configuration in Windows Server](https://docs.microsoft.com/en-us/windows-server/networking/technologies/dhcp/dhcp-top)
- [DNS Server Configuration in Windows Server](https://docs.microsoft.com/en-us/windows-server/networking/dns/dns-top)
