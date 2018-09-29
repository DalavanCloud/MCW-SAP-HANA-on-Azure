![Microsoft Cloud Workshops](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/master/Media/ms-cloud-workshop.png "Microsoft Cloud Workshops")

<div class="MCWHeader1">
SAP HANA on Azure
</div>

<div class="MCWHeader2">
Hands-on lab unguided
</div>

<div class="MCWHeader3">
December 2017
</div>


Information in this document, including URL and other Internet Web site references, is subject to change without notice. Unless otherwise noted, the example companies, organizations, products, domain names, e-mail addresses, logos, people, places, and events depicted herein are fictitious, and no association with any real company, organization, product, domain name, e-mail address, logo, person, place or event is intended or should be inferred. Complying with all applicable copyright laws is the responsibility of the user. Without limiting the rights under copyright, no part of this document may be reproduced, stored in or introduced into a retrieval system, or transmitted in any form or by any means (electronic, mechanical, photocopying, recording, or otherwise), or for any purpose, without the express written permission of Microsoft Corporation.

Microsoft may have patents, patent applications, trademarks, copyrights, or other intellectual property rights covering subject matter in this document. Except as expressly provided in any written license agreement from Microsoft, the furnishing of this document does not give you any license to these patents, trademarks, copyrights, or other intellectual property.

The names of manufacturers, products, or URLs are provided for informational purposes only and Microsoft makes no representations and warranties, either expressed, implied, or statutory, regarding these manufacturers or the use of the products with any Microsoft technologies. The inclusion of a manufacturer or product does not imply endorsement of Microsoft of the manufacturer or product. Links may be provided to third party sites. Such sites are not under the control of Microsoft and Microsoft is not responsible for the contents of any linked site or any link contained in a linked site, or any changes or updates to such sites. Microsoft is not responsible for webcasting or any other form of transmission received from any linked site. Microsoft is providing these links to you only as a convenience, and the inclusion of any link does not imply endorsement of Microsoft of the site or the products contained therein.

© 2018 Microsoft Corporation. All rights reserved.

Microsoft and the trademarks listed at https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/Usage/General.aspx are trademarks of the Microsoft group of companies. All other trademarks are property of their respective owners.

**Contents**

<!-- TOC -->

- [SAP HANA on Azure hands-on lab unguided](#sap-hana-on-azure-hands-on-lab-unguided)
    - [Abstract and learning objectives](#abstract-and-learning-objectives)
    - [Overview](#overview)
    - [Requirements](#requirements)
    - [Exercise 1: Provision Azure infrastructure](#exercise-1-provision-azure-infrastructure)
        - [Help references](#help-references)
        - [Task 1: Deploy an Azure virtual machine running Windows](#task-1-deploy-an-azure-virtual-machine-running-windows)
            - [Tasks to complete](#tasks-to-complete)
            - [Exit criteria](#exit-criteria)
        - [Task 2: Create a virtual network subnet for the HANA database tier](#task-2-create-a-virtual-network-subnet-for-the-hana-database-tier)
            - [Tasks to complete](#tasks-to-complete-1)
            - [Exit criteria](#exit-criteria-1)
        - [Task 3: Deploy an Azure Resource Manager QuickStart template](#task-3-deploy-an-azure-resource-manager-quickstart-template)
            - [Tasks to complete](#tasks-to-complete-2)
            - [Exit criteria](#exit-criteria-2)
        - [Task 4: Configure IP settings of Azure VMs running Linux](#task-4-configure-ip-settings-of-azure-vms-running-linux)
            - [Tasks to complete](#tasks-to-complete-3)
            - [Exit criteria](#exit-criteria-3)
        - [Task 5: Configure storage of Azure VMs](#task-5-configure-storage-of-azure-vms)
            - [Tasks to complete](#tasks-to-complete-4)
            - [Exit criteria](#exit-criteria-4)
    - [Exercise 2: Configure operating system on Azure VMs running Linux](#exercise-2-configure-operating-system-on-azure-vms-running-linux)
        - [Help references](#help-references-1)
        - [Task 1: Connect to Azure Linux VMs and register SUSE Linux Enterprise Server image](#task-1-connect-to-azure-linux-vms-and-register-suse-linux-enterprise-server-image)
            - [Tasks to complete](#tasks-to-complete-5)
            - [Exit criteria](#exit-criteria-5)
        - [Task 2: Add YaST packages, update the Linux operating system, and install HA Extensions](#task-2-add-yast-packages-update-the-linux-operating-system-and-install-ha-extensions)
            - [Tasks to complete](#tasks-to-complete-6)
            - [Exit criteria](#exit-criteria-6)
        - [Task 3: Enable cross-node password-less SSH access](#task-3-enable-cross-node-password-less-ssh-access)
            - [Tasks to complete](#tasks-to-complete-7)
            - [Exit criteria](#exit-criteria-7)
        - [Task 4: Configure storage](#task-4-configure-storage)
            - [Tasks to complete](#tasks-to-complete-8)
            - [Exit criteria](#exit-criteria-8)
        - [Task 5: Configure name resolution](#task-5-configure-name-resolution)
            - [Tasks to complete](#tasks-to-complete-9)
            - [Exit criteria](#exit-criteria-9)
    - [Exercise 3: Configure clustering on Azure VMs running Linux](#exercise-3-configure-clustering-on-azure-vms-running-linux)
        - [Help references](#help-references-2)
        - [Task 1: Configure clustering](#task-1-configure-clustering)
            - [Tasks to complete](#tasks-to-complete-10)
            - [Exit criteria](#exit-criteria-10)
        - [Task 2: Configure corosync](#task-2-configure-corosync)
            - [Tasks to complete](#tasks-to-complete-11)
            - [Exit criteria](#exit-criteria-11)
    - [Exercise 4: Install SAP HANA](#exercise-4-install-sap-hana)
        - [Help references](#help-references-3)
        - [Task 1: Copy installation media to Linux VMs](#task-1-copy-installation-media-to-linux-vms)
            - [Tasks to complete](#tasks-to-complete-12)
            - [Exit criteria](#exit-criteria-12)
        - [Task 2: Run hdblcm on both Linux VMs](#task-2-run-hdblcm-on-both-linux-vms)
            - [Exit criteria](#exit-criteria-13)
    - [Exercise 5: Configure SAP HANA replication](#exercise-5-configure-sap-hana-replication)
        - [Help references](#help-references-4)
        - [Task 1: Create HANA DATA ADMIN user account](#task-1-create-hana-data-admin-user-account)
            - [Tasks to complete](#tasks-to-complete-13)
            - [Exit criteria](#exit-criteria-14)
        - [Task 2: Configure keystore and perform a backup](#task-2-configure-keystore-and-perform-a-backup)
            - [Tasks to complete](#tasks-to-complete-14)
            - [Exit criteria](#exit-criteria-15)
        - [Task 3: Create the primary and the secondary sites](#task-3-create-the-primary-and-the-secondary-sites)
            - [Tasks to complete](#tasks-to-complete-15)
            - [Exit criteria](#exit-criteria-16)
    - [Exercise 6: Configure cluster framework](#exercise-6-configure-cluster-framework)
        - [Help references](#help-references-5)
        - [Task 1: Configure STONITH clustering options](#task-1-configure-stonith-clustering-options)
            - [Tasks to complete](#tasks-to-complete-16)
            - [Exit criteria](#exit-criteria-17)
        - [Task 2: Create an Azure AD application for the STONITH device](#task-2-create-an-azure-ad-application-for-the-stonith-device)
            - [Tasks to complete](#tasks-to-complete-17)
            - [Exit criteria](#exit-criteria-18)
        - [Task 3: Grant permissions to Azure VMs to the service principal of the STONITH app](#task-3-grant-permissions-to-azure-vms-to-the-service-principal-of-the-stonith-app)
            - [Tasks to complete](#tasks-to-complete-18)
            - [Exit criteria](#exit-criteria-19)
        - [Task 4: Configure the STONITH cluster device](#task-4-configure-the-stonith-cluster-device)
            - [Tasks to complete](#tasks-to-complete-19)
            - [Exit criteria](#exit-criteria-20)
        - [Task 5: Create SAPHanaTopology cluster resource agent](#task-5-create-saphanatopology-cluster-resource-agent)
            - [Tasks to complete](#tasks-to-complete-20)
        - [Task 6: Create SAPHana cluster resource agent](#task-6-create-saphana-cluster-resource-agent)
            - [Tasks to complete](#tasks-to-complete-21)
            - [Exit criteria](#exit-criteria-21)
    - [Exercise 7: Test the deployment](#exercise-7-test-the-deployment)
        - [Help references](#help-references-6)
        - [Task 1: Install SAP HANA Studio Administration on the Azure VM running Windows](#task-1-install-sap-hana-studio-administration-on-the-azure-vm-running-windows)
            - [Tasks to complete](#tasks-to-complete-22)
            - [Exit criteria](#exit-criteria-22)
        - [Task 2: Modify Azure Internal Load Balancer configuration](#task-2-modify-azure-internal-load-balancer-configuration)
            - [Tasks to complete](#tasks-to-complete-23)
            - [Exit criteria](#exit-criteria-23)
        - [Task 3: Connect to HANA cluster by using SAP HANA Studio Administration](#task-3-connect-to-hana-cluster-by-using-sap-hana-studio-administration)
            - [Tasks to complete](#tasks-to-complete-24)
            - [Exit criteria](#exit-criteria-24)
        - [Task 4: Connect to HANA cluster by using Hawk](#task-4-connect-to-hana-cluster-by-using-hawk)
            - [Tasks to complete](#tasks-to-complete-25)
            - [Exit criteria](#exit-criteria-25)
        - [Task 5: Test a manual failover (from s03-db-0 to s03-db-1)](#task-5-test-a-manual-failover-from-s03-db-0-to-s03-db-1)
            - [Tasks to complete](#tasks-to-complete-26)
            - [Exit criteria](#exit-criteria-26)
        - [Task 6: Test a migration (from s03-db-1 to s03-db-0)](#task-6-test-a-migration-from-s03-db-1-to-s03-db-0)
            - [Tasks to complete](#tasks-to-complete-27)
            - [Exit criteria](#exit-criteria-27)
        - [Task 7: Test fencing](#task-7-test-fencing)
            - [Tasks to complete](#tasks-to-complete-28)
            - [Exit criteria](#exit-criteria-28)
    - [After the hands-on lab](#after-the-hands-on-lab)
        - [Task 1: Remove the resource group containing all Azure resources deployed in this lab](#task-1-remove-the-resource-group-containing-all-azure-resources-deployed-in-this-lab)

<!-- /TOC -->

# SAP HANA on Azure hands-on lab unguided

## Abstract and learning objectives 

In this hands-on lab, you will step through the implementation of a highly available SAP HANA deployment on Microsoft Azure virtual machines running SUSE Linux Enterprise Server. 

After its completion, you will be able to provision Azure infrastructure components necessary to support highly available SAP HANA deployments, configure Azure virtual machines to support highly available SAP HANA installations, implement SUSE Linux Enterprise clustering, install SAP HANA, configure SAP HANA system replication, and test failover scenarios.

## Overview

In this hands-on lab, you are working with Contoso to develop a process of implementing a highly available deployment of SAP HANA on Azure virtual machines (VMs). Your tasks will include provisioning of Azure infrastructure components of the deployment, setting up a clustered pair of Azure Linux VMs running SUSE Linux Enterprise Server to support SAP HANA, installing SAP HANA instance on each of the Azure VMs, and configuring SAP HANA system replication between them.

## Requirements

-   A Microsoft Azure subscription

-   A lab computer running Windows 10 or Windows Server 2016 with:

    -   access to Microsoft Azure

    -   access to the SAP HANA installation media (requires an SAP Online Service System account)

    -   an SSH client e.g. PuTTY, available from <https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html>

    -   WinSCP client available from <https://winscp.net/eng/download.php>

-   SUSE Linux Enterprise Server 60-day free trial subscription (available from <https://www.suse.com/products/server/download/> ) via which you obtain registration code for an evaluation copy of SUSE Linux Enterprise Server for SAP Applications 12 SP3 for x86-64

## Exercise 1: Provision Azure infrastructure

In this exercise, you will deploy Azure infrastructure prerequisites for implementing SAP HANA on Azure virtual machines (VMs). This will include creating such resources as an Azure virtual network, Azure VMs in the same availability set, an Azure load balancer, and Azure Storage accounts as well as assigning static IPs to each VM.

### Help references

|    |            |
|----------|:-------------:|
| **Description** | **Links** |
| High Availability of SAP HANA on Azure Virtual Machines (VMs) | <https://docs.microsoft.com/en-us/azure/virtual-machines/workloads/sap/sap-hana-high-availability/> |

### Task 1: Deploy an Azure virtual machine running Windows

#### Tasks to complete

-   Deploy an Azure virtual machine with the following settings:

    -   Subscription: *the name of your Azure subscription*

    -   Resource group: *the name of a new resource group* **hana-s03-RG**

    -   Virtual machine name: **s03-hana-0**

    -   Region: *the Azure region you identified in the Before the Hands-on Lab section*

    -   Availability Options: **No infrastructure redundancy required**
    
    -   Image: **Windows Server 2016 Datacenter**
    
    -   Size: **Standard DS1 v2**
    
    -   Username: **demouser**

    -   Password: **demo\@pass123**

    -   Public inbound ports: **Allow selected ports**
    
    -   Select inbound ports: **RDP**
    
    -   Already have a Windows license?: **No**

    -   OS disk type: **Standard HDD**
    
    -   Use unmanaged disks: **No**

    -   Virtual network: create a new virtual network named **(new) hana-s03-RG-vnet** with the following settings:

        -   Name: **hana-s03-RG-vnet**
        
        -   Address space: **172.16.0.0/20**

        -   Subnet name: **subnet-0**

        -   Subnet address range: **172.16.0.0/24**

    -   Subnet: **subnet-0**

    -   Public IP: *accept the default value*

    -   Network security group: **Basic**
    
    -   Public inbound ports: **Allow selected ports**
    
    -   Select inbound ports: **RDP**
    
    -   Accelerated networking: **Off**
    
    -   Boot diagnostics: **Off**

    -   OS guest diagnostics: **Off**
    
    -   Managed service identity: **Off**
    
    -   Enable auto-shutdown: **Off**
        
    -   Enable backup: **Off**
 
#### Exit criteria 

-   A resource group named **s03-hana-RG** containing a Windows VM **s03-hana-0** on **subnet-0** of a virtual network named **hana-s03-RG-vnet**

### Task 2: Create a virtual network subnet for the HANA database tier

#### Tasks to complete

-   Create a virtual network subnet for the HANA database tier

    -   Name: **subnet-1**

    -   Address range: **172.16.1.0/24**

    -   Network security group: **None**

    -   Route table: **None**

    -   Service endpoints (Preview): **0 selected**

#### Exit criteria 

-   A resource group named **s03-hana-RG** containing a **subnet-0** and **subnet-1** of a virtual network named **hana-s03-RG-vnet**

    -   Service endpoints (Preview): **0 selected**



### Task 3: Deploy an Azure Resource Manager QuickStart template

#### Tasks to complete

-   Deploy an Azure Resource Manager QuickStart template

    -   Use the template <https://github.com/Azure/azure-quickstart-templates/tree/master/sap-3-tier-marketplace-image-multi-sid-db-md>

    -   Use the following deployment parameters

        -   Subscription: *the name of your Azure subscription*

        -   Resource group: **s03-hana-RG**

        -   Location: *the Azure region you identified in the Before the Hands-on Lab section*

        -   Sap System Id: **S03**

        -   Os Type: **SLES 12 BYOS**

        -   Dbtype: **HANA**

        -   SAP System Size: **Demo**

        -   System Availability: **HA**

        -   Admin Username: **demouser**

        -   Admin Password: **demo\@pass123**

        -   Subnet id: reference the **subnet-1** you created in the previous task

        -   \_artifacts Location: *accept the default value*

        -   \_artifacts Location SaS Token: *accept the default value*

#### Exit criteria 

-   A resource group named **s03-hana-RG** containing all resources included in the ARM template available at <https://github.com/Azure/azure-quickstart-templates/tree/master/sap-3-tier-marketplace-image-multi-sid-db-md>

### Task 4: Configure IP settings of Azure VMs running Linux

#### Tasks to complete

-   Configure IP settings of Azure VMs running Linux

    -   Set **s03-pip-db-0** to the static IP address 172.16.0.10

    -   Set **s03-pip-db-1** to the static IP address 172.16.0.11

    -   Assign a DNS name label to the public IP addresses of s03-db-0 and s03-db-1

#### Exit criteria 

-   A resource group named **s03-hana-RG** containing two Linux VMs named **s03-db-0** and **s03-db-1** with DNS name label and static IP addresses of 172.16.0.10 and 172.16.0.11 assigned to each (respectively)

## Exercise 2: Configure operating system on Azure VMs running Linux

In this exercise, you will configure operating system settings on Azure VMs running SUSE Linux Enterprise Server to accommodate subsequent clustered installation of SAP HANA

### Help references

|    |            |
|----------|:-------------:|
| **Description** | **Links** |
| High Availability of SAP HANA on Azure Virtual Machines (VMs) | <https://docs.microsoft.com/en-us/azure/virtual-machines/workloads/sap/sap-hana-high-availability/> |

### Task 1: Connect to Azure Linux VMs and register SUSE Linux Enterprise Server image

#### Tasks to complete

-   Connect to the s03-db-0 and s03-db-1 Azure VMs via SSH and register SUSE Linux Enterprise Server image

#### Exit criteria 

-   Successfully registered SUSE Linux Enterprise Server image.

### Task 2: Add YaST packages, update the Linux operating system, and install HA Extensions

#### Tasks to complete

-   On both s03-db-0 and s03-db-1,

    -   use YaST to add **Extensions and Modules from Registration Server** package

    -   use zypper to update all installed packages

    -   use zypper to install **sle-ha-release fence-agents**

#### Exit criteria

-   Successfully installed **Extensions and Modules from Registration Server** package, installed **sle-ha-release fence-agents**, and successfully updated all installed packages

### Task 3: Enable cross-node password-less SSH access

#### Tasks to complete

-   Generate passphrase-less key pairs on each Linux VM and store the resulting public keys from each VM in the **/root/.ssh/authorized\_keys** file on the other VM

#### Exit criteria 

-   The ability to establish SSH session from each of the two VMs to the other VM without being prompted for a password

### Task 4: Configure name resolution

#### Tasks to complete

-   Add entries to **/etc/hosts** on both Linux VM s03-db-0 and s03-db-1 to facilitate resolution of their names to their respective private IP addresses

#### Exit criteria 

-   Successful name resolution of s03-db-0 and s03-db-1 names to their respective IP addresses from both VMs

### Task 5: Configure storage

#### Tasks to complete

-   On each of the two Linux VMs, s03-db-0 and s03-db-1, create s03-db-0, create a directory that will be used to host the SAP HANA installation media in /hana/shared/media

#### Exit criteria 

-   Use **ls** to verify that the directory was successfully created


## Exercise 3: Configure clustering on Azure VMs running Linux

In this exercise, you will configure clustering on Azure VMs running Linux.

### Help references

|    |            |
|----------|:-------------:|
| **Description** | **Links** |
| High Availability of SAP HANA on Azure Virtual Machines (VMs) | <https://docs.microsoft.com/en-us/azure/virtual-machines/workloads/sap/sap-hana-high-availability/> |

### Task 1: Configure clustering

#### Tasks to complete

-   From **s03-db-0**, run **ha-cluster-init**

-   From **s03-db-1**, run **ha-cluster-join**

-   Change the password of hacluster account to **demo\@pass123**

#### Exit criteria 

-   Cluster successfully created and the password of the hacluster user account set to **demo\@pass123**

### Task 2: Configure corosync 

#### Tasks to complete

-   Modify the **/etc/corosync/corosync.conf** file on both s03-db-0 and s03-db-1 to add the references to both cluster nodes

-   Restart the corosync service on both cluster nodes

#### Exit criteria 

-   Corosync reconfigured to include references to both cluster nodes

## Exercise 4: Install SAP HANA

In this exercise, you will install SAP HANA.

### Help references

|    |            |
|----------|:-------------:|
| **Description** | **Links** |
| High Availability of SAP HANA on Azure Virtual Machines (VMs) | <https://docs.microsoft.com/en-us/azure/virtual-machines/workloads/sap/sap-hana-high-availability/> |


### Task 1: Copy installation media to Linux VMs

#### Tasks to complete

-   Copy the SAP HANA installation media to the /hana/shared/media directory on both s03-db-0 and s03-db-1

#### Exit criteria 

-   SAP HANA installation media residing in the /hana/shared/media directory on both s03-db-0 and s03-db-1

### Task 2: Run hdblcm on both Linux VMs

####Tasks to complete

-   Run hdblcm on both s03-db-0 and s03-db-1 with the following settings:

    -   Enter selected system index \[3\]: **1**

    -   Enter comma-separated list of the selected indices \[3\]: **1**

    -   Enter Installation Path \[/hana/shared\]: *accept the default*

    -   Enter Local Host Name \[s03-db-0\]: *accept the default*

    -   Do you want to add additional hosts to the system? (y/n) \[n\]: *accept the default*

    -   Enter SAP HANA System ID: **S03**

    -   Enter Instance Number \[00\]: *accept the default*

    -   Select Database Mode / Enter Index \[1\]: *accept the default*

    -   Select System Usage / Enter Index \[4\]: **4**

    -   Enter Location of Data Volumes \[/hana/data/S03\]: *accept the default*

    -   Enter Location of Log Volumes \[/hana/log/S03\]: *accept the default*

    -   Enter Certificate Host Name For Host \'s03-db-0\' \[s03-db-0\]: *accept the default*

    -   Enter SAP Host Agent User (sapadm) Password: **demo\@pass123**

    -   Confirm SAP Host Agent User (sapadm) Password: **demo\@pass123**

    -   Enter System Administrator (s03adm) Password: **demo\@pass123**

    -   Confirm System Administrator (s03adm) Password: **demo\@pass123**

    -   Enter System Administrator Home Directory \[/usr/sap/S03/home\]: *accept the default*

    -   Enter System Administrator Login Shell \[/bin/sh\]: *accept the default*

    -   Enter System Administrator User ID \[1001\]: *accept the default*

    -   Enter ID of User Group (sapsys) \[79\]: *accept the default*

    -   Enter Database User (SYSTEM) Password: **Demo\@pass123**

    -   Confirm Database User (SYSTEM) Password: **Demo\@pass123**

    -   Restart system after machine reboot? \[n\]: *accept the default*

#### Exit criteria 

-   SAP HANA installed successfully on both s03-db-0 and s03-db-1

## Exercise 5: Configure SAP HANA replication

In this exercise, you will configure SAP HANA replication.

### Help references

|    |            |
|----------|:-------------:|
| **Description** | **Links** |
| High Availability of SAP HANA on Azure Virtual Machines (VMs) | <https://docs.microsoft.com/en-us/azure/virtual-machines/workloads/sap/sap-hana-high-availability/> |

### Task 1: Create HANA DATA ADMIN user account

#### Tasks to complete

-   On s03-db-0, create a HANA DATA ADMIN user account with non-expiring password and the following settings

    -   User name: **s03hasync**

    -   Password: **C0mpl3xp\@55w0rd**

#### Exit criteria 

-   Successfully created HANA DATA ADMIN user account with non-expiring password, named **s03hasync** with the password set to **C0mpl3xp\@55w0rd**

### Task 2: Configure keystore and perform a backup

#### Tasks to complete

-   On both s03-db-0 and s03-db-1, configure keystore

-   On s03-db-0, run HANA system backup

#### Exit criteria 

-   Keystore created on both s03-db-0 and s03-db-1 and a HANA backup completed on s03-db-0

### Task 3: Create the primary and the secondary sites

#### Tasks to complete

-   On s03-db-0, create a site named SITE1 and configure it as system replication source site

-   On s03-db-1, stop the HANA DB instance and create a site named SITE2 configured as synchronously replicated system replication destination

#### Exit criteria 

-   Synchronous replication between the HANA DB instance on s03-db-0 and s03-db-1

## Exercise 6: Configure cluster framework

In this exercise, you will configure SAP HANA replication.

### Help references

|    |            |
|----------|:-------------:|
| **Description** | **Links** |
| High Availability of SAP HANA on Azure Virtual Machines (VMs) | <https://docs.microsoft.com/en-us/azure/virtual-machines/workloads/sap/sap-hana-high-availability/> |

### Task 1: Configure STONITH clustering options

#### Tasks to complete

-   On s03-db-0, configure the following STONITH clustering options:

        property \$id=\"cib-bootstrap-options\" \\

        no-quorum-policy=\"ignore\" \\

        stonith-enabled=\"true\" \\

        stonith-action=\"reboot\" \\

        stonith-timeout=\"150s\"

        rsc\_defaults \$id=\"rsc-options\" \\

        resource-stickiness=\"1000\" \\

        migration-threshold=\"5000\"

        op\_defaults \$id=\"op-options\" \\

        timeout=\"600\"

#### Exit criteria 

-   Successfully applied STONITH clustering options

### Task 2: Create an Azure AD application for the STONITH device

#### Tasks to complete

-   In the Azure AD tenant associated with the Azure subscription hosting the lab deployment, register a new application with the following settings:

    -   Name: **Stonith app**

    -   Application type: **Web app /API**

    -   Sign-on URL: **http://localhost**

-   Identify *subscription\_id, resource\_group, tenant\_id, login\_id,* and *password* values corresponding to the Azure subscription, the Azure AD tenant, and the new application

#### Exit criteria 

-   An application named **Stonith app** created in the Azure AD tenant associated with the Azure subscription hosting the lab deployment

### Task 3: Grant permissions to Azure VMs to the service principal of the STONITH app

#### Tasks to complete

-   From the Azure portal, assign the Owner role to the service principal associated with the Stonith app to s03-db-0 and s03-db-1 Azure VMs

#### Exit criteria 

-   The service principal associated with the Stonith app assigned the Owner role to s03-db-0 and s03-db-1 Azure VMs

### Task 4: Configure the STONITH cluster device

#### Tasks to complete

-   From s03-db-0, configure the STONITH cluster device by associating it with Azure AD Stonith app

#### Exit criteria 

-   Configured STONITH cluster device, associated with Azure AD Stonith app

### Task 5: Create SAPHanaTopology cluster resource agent

#### Tasks to complete

-   From s03-db-0, create the SAPHanaTopology cluster resource agent

#### Exit criteria 

-   Create SAPHanaTopology cluster resource agent successfully added to the cluster

### Task 6: Create SAPHana cluster resource agent

#### Tasks to complete

-   From s03-db-0, create the SAPHana cluster resource agent

#### Exit criteria 

-   Create SAPHana cluster resource agent successfully added to the cluster

## Exercise 7: Test the deployment

In this exercise, you will test the HANA deployment.

### Help references

|    |            |
|----------|:-------------:|
| **Description** | **Links** |
| High Availability of SAP HANA on Azure Virtual Machines (VMs) | <https://docs.microsoft.com/en-us/azure/virtual-machines/workloads/sap/sap-hana-high-availability/> |

### Task 1: Install SAP HANA Studio Administration on the Azure VM running Windows

#### Tasks to complete

-   Copy the DATA\_UNITS\\HDB\_STUDIO\_WINDOWS\_X86\_64 folder from the installation media to the s03-hana-0 Azure VM

-   On the s03-hana-0 Azure VM, install **SAP HANA Studio Administration**

#### Exit criteria

-   **SAP HANA Studio Administration** installed on the s03-hana-0 Azure VM

### Task 2: Modify Azure Internal Load Balancer configuration

#### Tasks to complete

-   The template-based deployment of Azure components that form the SAP HANA infrastructure configures load balancer with the default value of its Health Probe ports and load balancing rules set for the instance 03 of SAP HANA. In this task, you need to modify the load balancer configuration in order to account for the fact that you deployed instance 00.

#### Exit criteria 

-   The health probe and load balancing rules modified to account for the fact that you deployed instance 00

### Task 3: Connect to HANA cluster by using SAP HANA Studio Administration

#### Tasks to complete

-   On the s03-hana-0 Azure VM, modify the **C:\\Windows\\System32\\drivers\\etc\\hosts** file to allow connectivity to cluster and its nodes by using the following names:

    -   172.16.1.10 s03-db-0

    -   172.16.1.11 s03-db-1

    -   172.16.1.4 s03-db-ha-01

-   From the s03-hana-0 Azure VM connect to **SAP HANA Studio Administration** by using the name s03-db-ha-01 and the following database user credentials:

    -   User Name: **SYSTEM**

    -   Password: **Demo\@pass123**

#### Exit criteria 

-   In **SAP HANA Studio Administration**, navigate to the **Configuration and Monitoring** view and examine the **Overview** tab. Verify that all services are started, active, and in sync. Switch to the **Alerts** tab and verify that they are not indicating any operational issues.

### Task 4: Connect to HANA cluster by using Hawk

#### Tasks to complete

-   From the s03-hana-0 Azure VM, start Internet Explorer and browse to **https://s03-db-0:7630**. On the **SUSE Hawk Sign in** page, sign in as **hacluster** with the password **demo\@pass123**.

#### Exit criteria 

-   In the **SUSE Hawk** interface, examine the state of the HANA resources including **SAPHANATopology** and **SAPHana**

### Task 5: Test a manual failover (from s03-db-0 to s03-db-1)

#### Tasks to complete

-   From an SSH session to s03-db-0, stop the pacemaker service

-   Use Hawk to verify that a failover took place and ensure that you can connect to the cluster via SAP HANA Administration Console

-   Restart the pacemaker service on s03-db-0

-   Use Hawk to verify that the SAPHana clustered resource on s03-db-0 failed to start

-   From the SSH session to s03-db-0, re-establish HANA system replication and clean up the failed state

-   Use Hawk to verify that the SAPHana clustered resource on s03-db-0 started successfully

#### Exit criteria 

-   In the SUSE Hawk interface, verify that SAPHANA clustered resource is operational, with s03-db-1 as master and s03-db-0 as slave

### Task 6: Test a migration (from s03-db-1 to s03-db-0)

#### Tasks to complete

-   From an SSH session to s03-db-1, migrate the SAPHana master node and the group containing the virtual IP address of the cluster to s03-db-0

-   Use Hawk to verify that the migration took place and that that the SAPHana clustered resource on s03-db-1 failed to start as secondary.

-   From the SSH session to s03-db-1, reestablish the HANA system replication

-   Use Hawk to remove all location constraints

-   From the SSH session to s03-db-1, clean up the failed state

-   Use Hawk to verify that the SAPHana clustered resource is operational on both nodes with s03-db-0 as the master

-   Use SAP HANA Administration Console to verify that SAP HANA is running at this point on the s03-db-0 node and is operational

#### Exit criteria 

-   In the SUSE Hawk interface, verify that SAPHANA clustered resource is operational, with s03-db-0 as master and s03-db-1 as slave.

### Task 7: Test fencing

#### Tasks to complete

-   From an SSH session to s03-db-0, shut down the eth0 network interface

-   From the Azure portal, verify that the s03-db-0 virtual machine gets automatically restarted

-   Use Hawk to verify that the cluster resources are automatically moved to s03-db-1

-   Use SAP HANA Administration Console to verify that SAP HANA is running at this point on the s03-db-1 node and is operational

-   Use the Azure portal to ensure that the s03-db-0 virtual machine is running again

-   From the SSH session to s03-db-0, reestablish the HANA system replication and clean up the failed state

-   Use Hawk to verify that the SAPHana clustered resource is operational on both nodes with s03-db-1 as the master

-   Use SAP HANA Administration Console to verify that the SAP HANA system replication status is active

#### Exit criteria

-   Use SAP HANA Administration Console to verify that the SAP HANA system replication status is active.

## After the hands-on lab 

Duration: 10 minutes

After completing the hands-on lab, you will remove the resource group and all of its resources.

### Task 1: Remove the resource group containing all Azure resources deployed in this lab

1.  From the lab computer, in the Azure portal at <http://portal.azure.com> , click the **Cloud Shell** icon

2.  If prompted, in the **Welcome to Azure Cloud Shell** window, click **Bash (Linux)**

3.  At the Bash prompt, run the following:

```
az group delete \--name s03-hana-RG \--no-wait \--yes
```

You should follow all steps provided *after* the Hands-on lab.
