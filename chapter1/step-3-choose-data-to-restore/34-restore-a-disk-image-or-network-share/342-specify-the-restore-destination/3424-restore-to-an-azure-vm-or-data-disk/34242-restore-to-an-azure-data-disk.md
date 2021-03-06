## Restore to Azure Data Disk

This option enables you to restore a disk image to a [Microsoft Azure data disk](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/about-disks-and-vhds).

> The disk size \(the total of all [partitions](/chapter1/step-3-choose-data-to-restore/34-restore-a-disk-image-or-network-share/344-select-partitions.md)\) cannot exceed **4** TB.

![](/assets/restore-azure-data-disk-account.png)

Before running this wizard, you need to create a new user and select a subscription, region, resource groups, as well as create a storage account and virtual network via the [Microsoft Azure Portal](https://portal.azure.com/).

> To be able to restore a disk image, you should use a [general-purpose storage account](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-options) and not a blob storage, because blob storage accounts support only _block_ and _append blobs_, and not _page blobs_ on on which virtual machines are stored. Page blobs are only available in general-purpose accounts and they do not provide [zone-redundant storage \(ZRS\)](https://docs.microsoft.com/en-us/azure/storage/common/storage-redundancy#zone-redundant-storage).
>
> See the following article to learn about managing Azure Active Directory accounts when using CloudBerry Lab products: [Managing Azure Active Directory Accounts](/concepts/managing-azure-active-directory-accounts.md).

Next, you need to select an existing Azure account or create and configure a new one on this wizard page.

After you selected an account, specify the following options:

* **Data disk name**  
  Specifies the name assigned to the target data disk.

* **Resource group**  
  Specifies the container that holds related _resources_ \(such as virtual machines, storage accounts, web apps, databases, and virtual networks\) for an Azure solution. See [Resource groups](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-overview#resource-groups) for more information.

  > Both the restored data disk and the virtual machine on which it is supposed to be mounted should belong to the same resource group and storage.

* **Storage**  
  Specifies the [disk storage](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/about-disks-and-vhds) on the target virtual machine.

  > Both the restored data disk and the virtual machine on which it is supposed to be mounted should belong to the same resource group and storage.

* **Container**  
  Specifies the bucket to which the data disk will be placed.



