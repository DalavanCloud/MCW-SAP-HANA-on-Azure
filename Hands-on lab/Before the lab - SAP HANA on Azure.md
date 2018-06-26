
# SAP HANA on Azure setup

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

1.  Login to <http://portal.azure.com>, click on **More Services** and, in the service menu, click **Subscriptions**.

2.  On the **Subscriptions** blade, click the name of the subscription you intend to use for this lab.

3.  On the subscription blade, click **Access control (IAM)**.

4.  Review the list of user accounts, and verify that your user account has the Owner role assigned to it

### Task 2: Validate availability of the SUSE Linux Enterprise Server image 

1.  In the Azure portal at <http://portal.azure.com>, click the **Cloud Shell** icon.

    ![In the Azure Portal, the Cloud Shell icon is selected.](images/Setup/image2.png "Azure Portal")

2.  If prompted, in the **Welcome to Azure Cloud Shell** window, click **Bash (Linux)**.

3.  If prompted, in the **You have no storage mounted** window, click **Create storage**.

4.  Once the storage account gets provisioned, at the Bash prompt, run the following: where ***location*** designates the target Azure region that you intend to use for this lab (e.g. ***eastus2***), and verify the output includes an existing image:
    ```
    az vm image list --location location --publisher SUSE --offer SLES-SAP-BYOS --sku 12-SP3 --all --output table
    ``` 
