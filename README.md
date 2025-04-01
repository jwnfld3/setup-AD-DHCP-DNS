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

#### Step 1: Install AD DS Role
1. Open **Server Manager** and click **Manage** > **Add Roles and Features**.
2. Choose **Role-based or feature-based installation**, then select the server and click **Next**.
3. In the **Roles** section, check **Active Directory Domain Services**. Click **Next**.
4. Click **Install** to install the AD DS role. Wait for the installation to complete.

#### Step 2: Promote the Server to Domain Controller
1. After installation, click the notification flag in **Server Manager** and select **Promote this server to a domain controller**.
2. Choose **Add a new forest**, then enter the **Root domain name** (e.g., **example.local**).
3. Set the **Forest functional level** and **Domain functional level** to the appropriate version (e.g., Windows Server 2016 or higher).
4. Enter a **Directory Services Restore Mode (DSRM) password** and click **Next**.
5. Review the DNS options and ensure **Install DNS server** is selected.
6. Review the configuration and click **Install**. The server will restart.

### 2. **Set Up a DHCP Server**

#### Step 1: Install the DHCP Server Role
1. Open **Server Manager** and click **Manage** > **Add Roles and Features**.
2. Select **Role-based or feature-based installation**, choose the server, and click **Next**.
3. In the **Roles** section, check **DHCP Server**, then click **Next**.
4. Click **Install** to install the DHCP role. Wait for the installation to complete.

#### Step 2: Configure the DHCP Server
1. Open the **DHCP Management Console** from **Server Manager** > **Tools** > **DHCP**.
2. Right-click **DHCP** and select **Authorize** to authorize the server.
3. Right-click **IPv4** and select **New Scope**.
4. Configure the scope by entering a **Start IP address**, **End IP address**, **Subnet Mask**, and any **Exclusions** for static IPs.
5. Set the **Lease Duration** and configure the **DHCP Options** such as **Router** and **DNS servers**.
6. Activate the scope and verify clients can obtain IP addresses.

### 3. **Set Up a DNS Server**

#### Step 1: Install the DNS Server Role
1. Open **Server Manager** and click **Manage** > **Add Roles and Features**.
2. Select **Role-based or feature-based installation**, choose the server, and click **Next**.
3. In the **Roles** section, check **DNS Server**, then click **Next**.
4. Click **Install** to install the DNS role.

#### Step 2: Configure the DNS Server
1. Open the **DNS Management Console** from **Server Manager** > **Tools** > **DNS**.
2. Right-click **Forward Lookup Zones** and select **New Zone**.
3. Select **Primary Zone**, enter the **Zone Name** (e.g., **example.local**), and click **Next**.
4. Add **A Records** for DNS resolution (e.g., **server1.example.local**).
5. Configure **Forwarders** to an external DNS server if necessary.

---

## Lab Conclusion

At the end of this lab, **Active Directory Domain Services (AD DS)**, **DHCP**, and **DNS** will be successfully installed and configured on a Windows Server 2022 machine. These services provide essential network functionality, allowing for centralized management of users, dynamic IP address assignment, and domain name resolution across the network.

---

## Additional Resources

- [Microsoft Active Directory Documentation](https://docs.microsoft.com/en-us/windows-server/identity/active-directory-domain-services)
- [DHCP Server Configuration in Windows Server](https://docs.microsoft.com/en-us/windows-server/networking/technologies/dhcp/dhcp-top)
- [DNS Server Configuration in Windows Server](https://docs.microsoft.com/en-us/windows-server/networking/dns/dns-top)
