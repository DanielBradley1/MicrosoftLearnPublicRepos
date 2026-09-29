<!-- Source: https://learn.microsoft.com/en-us/defender-for-iot/manage-license -->
<!-- Sitemap-Last-Modified: 2026-08-08 -->

# Manage your Microsoft Defender for IoT license

After setting up a license for Microsoft Defender for IoT, you can manage and update it as needed. To purchase the correct license, you need to know the total number of devices within your network so that you can choose the correct sized license for your network.

This article shows how to make changes to your license, including the steps to choose the best size license to purchase.

Important

This article discusses Microsoft Defender for IoT in the Defender portal \(Preview\).

Some features are not yet available in the Defender portal. If you're interested in these features, or you're an existing customer working on the Azure portal, see the [Defender for IoT on Azure documentation](https://learn.microsoft.com/en-us/azure/defender-for-iot/organizations/overview).

Learn more about the [Defender for IoT management portals](https://learn.microsoft.com/en-us/defender-for-iot/microsoft-defender-iot#what-are-the-different-management-portals-for-microsoft-defender-for-iot).

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

## Calculate the number of IoT devices for licensing

To calculate the number of devices in your network:

1. In the [Microsoft Defender portal](https://security.microsoft.com/machines) menu, select **Assets > Devices**. The device inventory opens.
2. Select the **IoT/OT devices** tab. Note down the total number of devices listed. In this example there are 816 IoT/OT devices detected.

   [![Screenshot showing the list of OT devices in the device inventory for caluculating the total number of devices at the site.](https://learn.microsoft.com/en-us/defender-for-iot/media/manage-licenses/calculate-ot-devices.png)](https://learn.microsoft.com/en-us/defender-for-iot/media/manage-licenses/calculate-ot-devices.png#lightbox)

## Select a Defender for IoT license size in the Microsoft 365 admin center

Purchase the license for your network from the [Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/commerce/licenses/buy-licenses), ensuring it covers enough devices for your site needs.

1. Go to the Microsoft 365 admin center **Billing > Purchase services**. If **Purchase services** isn't available, select **Marketplace** instead.
2. Search for Defender for IoT.
3. Choose the license appropriate for the size of your site. There are five different sized licenses ranging from Extra-large for up to 5,000 devices, to extra-small covering a maximum of 100 devices.

   Make sure to select the number of licenses you want to purchase based on the number of sites you're monitoring. You might need to select licenses of different sizes if the number of devices at each site is different.
4. Complete the purchasing instructions.
