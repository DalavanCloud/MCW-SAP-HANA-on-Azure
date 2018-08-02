
![Microsoft Cloud Workshops](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/master/Media/ms-cloud-workshop.png "Microsoft Cloud Workshops")

<div class="MCWHeader1">
SAP HANA on Azure
</div>

<div class="MCWHeader2">
Before the hands-on lab setup guide
</div>

<div class="MCWHeader3">
December 2017
</div>


Information in this document, including URL and other Internet Web site references, is subject to change without notice. Unless otherwise noted, the example companies, organizations, products, domain names, e-mail addresses, logos, people, places, and events depicted herein are fictitious, and no association with any real company, organization, product, domain name, e-mail address, logo, person, place or event is intended or should be inferred. Complying with all applicable copyright laws is the responsibility of the user. Without limiting the rights under copyright, no part of this document may be reproduced, stored in or introduced into a retrieval system, or transmitted in any form or by any means (electronic, mechanical, photocopying, recording, or otherwise), or for any purpose, without the express written permission of Microsoft Corporation.

Microsoft may have patents, patent applications, trademarks, copyrights, or other intellectual property rights covering subject matter in this document. Except as expressly provided in any written license agreement from Microsoft, the furnishing of this document does not give you any license to these patents, trademarks, copyrights, or other intellectual property.

The names of manufacturers, products, or URLs are provided for informational purposes only and Microsoft makes no representations and warranties, either expressed, implied, or statutory, regarding these manufacturers or the use of the products with any Microsoft technologies. The inclusion of a manufacturer or product does not imply endorsement of Microsoft of the manufacturer or product. Links may be provided to third party sites. Such sites are not under the control of Microsoft and Microsoft is not responsible for the contents of any linked site or any link contained in a linked site, or any changes or updates to such sites. Microsoft is not responsible for webcasting or any other form of transmission received from any linked site. Microsoft is providing these links to you only as a convenience, and the inclusion of any link does not imply endorsement of Microsoft of the site or the products contained therein.

© 2018 Microsoft Corporation. All rights reserved.

Microsoft and the trademarks listed at <https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/Usage/General.aspx> are trademarks of the Microsoft group of companies. All other trademarks are property of their respective owners.

<!-- TOC -->

- [SAP HANA on Azure before the hands-on-lab setup guide](#sap-hana-on-azure-before-the-hands-on-lab-setup-guide)
    - [Requirements](#requirements)
    - [Before the hands-on lab](#before-the-hands-on-lab)
        - [Task 1: Validate the owner role membership in the Azure subscription](#task-1-validate-the-owner-role-membership-in-the-azure-subscription)
        - [Task 2: Validate availability of the SUSE Linux Enterprise Server image](#task-2-validate-availability-of-the-suse-linux-enterprise-server-image)

<!-- /TOC -->

# SAP HANA on Azure before the hands-on-lab setup guide

## Requirements

-   A Microsoft Azure subscription

-   A lab computer running Windows 10 or Windows Server 2016 with:

    -   access to Microsoft Azure

    -   access to the SAP HANA installation media (requires an SAP Online Service System account)

    -   an SSH client e.g. PuTTY, available from <https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html>

    -   WinSCP client available from <https://winscp.net/eng/download.php>

-   SUSE Linux Enterprise Server 60-day free trial subscription (available from <https://www.suse.com/products/sles-for-sap/download/> ) via which you obtain registration code for an evaluation copy of SUSE Linux Enterprise Server for SAP Applications 12 SP3 for x86-64


## Before the hands-on lab

Duration: 10 minutes

To complete this lab, you must verify your account has sufficient permissions to the Azure subscription that you intend to use to deploy Azure VMs. You also need to identify the availability of the SUSE Linux Enterprise Server image that you will use to deploy Azure VMs.

### Task 1: Validate the owner role membership in the Azure subscription

1.  Login to <http://portal.azure.com>, click on **More Services** and, in the service menu, click **Subscriptions**

2.  On the **Subscriptions** blade, click the name of the subscription you intend to use for this lab

3.  On the subscription blade, click **Access control (IAM)**

4.  Review the list of user accounts, and verify that your user account has the Owner role assigned to it

### Task 2: Validate availability of the SUSE Linux Enterprise Server image 

1.  In the Azure portal at <http://portal.azure.com>, click the **Cloud Shell** icon

    ![In the Azure Portal, the Cloud Shell icon is selected.](images/Setup/image2.png "Azure Portal")

2.  If prompted, in the **Welcome to Azure Cloud Shell** window, click **Bash (Linux)**

3.  If prompted, in the **You have no storage mounted** window, click **Create storage**

4.  Once the storage account gets provisioned, at the Bash prompt, run the following: where ***location*** designates the target Azure region that you intend to use for this lab (e.g. ***eastus2***), and verify the output includes an existing image:

    ```
    az vm image list --location location --publisher SUSE --offer SLES-SAP-BYOS --sku 12-SP3 --all --output table
    ``` 
     
You should follow all steps provided *before* performing the Hands-on lab.

