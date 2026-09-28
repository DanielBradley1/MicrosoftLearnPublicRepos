<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/connect-an-on-premises-network-to-a-microsoft-azure-virtual-network?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2025-02-27 -->

# Connect an on-premises network to a Microsoft Azure virtual network

A cross-premises Azure virtual network is connected to your on-premises network, extending your network to include subnets and virtual machines hosted in Azure infrastructure services. This connection lets computers on your on-premises network to directly access virtual machines in Azure and vice versa.

For example, a directory synchronization server running on an Azure virtual machine needs to query your on-premises domain controllers for changes to accounts and synchronize those changes with your Microsoft 365 subscription.

To set up a cross-premises Azure virtual network using a site-to-site virtual private network \(VPN\) connection, see [VPN Gateway documentation](https://learn.microsoft.com/en-us/azure/vpn-gateway).

Here is your resulting configuration.

![The virtual network now hosts virtual machines that are accessible from the on-premises network.](https://learn.microsoft.com/en-us/microsoft-365/media/86ab63a6-bfae-4f75-8470-bd40dff123ac.png?view=o365-worldwide)

## Next step

[Deploy Microsoft 365 Directory Synchronization in Microsoft Azure](https://learn.microsoft.com/en-us/microsoft-365/enterprise/deploy-microsoft-365-directory-synchronization-dirsync-in-microsoft-azure?view=o365-worldwide)
