<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/commerce/licenses/download-vl-products?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-05-13 -->

# Download volume licensing products

If you bought products via volume licensing \(VL\), you can download the products either as Executable \(EXE\) files or as ISO \(International Standards Organization\) image files from the **Downloads** page in the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).

## Before you begin

- You must have the VL Administrator or Product download manager roles for the corresponding License ID to access downloads in the admin center. For information about VL roles, see [Manage volume licensing user roles](https://learn.microsoft.com/en-us/microsoft-365/commerce/licenses/manage-user-roles-vl?view=o365-worldwide).
- Unless their permissions are removed by an Administrator, or the user no longer exists in Microsoft Entra ID, a user's permissions to access the VL downloads tab continues beyond the agreement end date.
- You must have, or buy, a license for the products that you plan to download.
- To install VL download files, you might need a valid product key.
- You must have either the VL Administrator or Product keys reader role to access VL product keys.

## Find out if a product is available to download

1. In the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339) go to the **Billing** > [**Your products**](https://go.microsoft.com/fwlink/p/?linkid=842054) page, then select the [Volume licensing](https://go.microsoft.com/fwlink/p/?linkid=2244144) tab.
2. In the **Products and services** section, select **View downloads and keys**.
3. Select the product or select the **Downloads** button to view the downloadable ISO files.

   Not all products are available to download. If there's no software download file, you see "This product is not available for download."
4. Choose the **Language** and **Operating System Type** and select a download action or the download icon.

Note

Pop-up blockers can block downloads. Make sure pop-up blockers are disabled when you download software from the admin center.

## About downloading volume licensing products

This section explains the file types for which you can download products, limitations of the VL download catalog, and products that don't require downloads.

### Understand volume licensing product and keys catalog

It's important to understand that being able to view a software download file or product key doesn't automatically entitle customers to download and install that product or its latest version for all their VL agreements.

The Microsoft VL download catalog lets users see the entire range of Microsoft products and services available in Microsoft's VL program offers while the user has access to any active VL agreement. However, users might have access to multiple VL agreements with different products or subscriptions purchased under them, or might still have access to agreements that are no longer active. This situation allows access to downloads for perpetual licenses of products ordered under agreements that have since expired.

Users with access only to expired agreements only see downloads released by the last active agreement end date. However, users who also have permissions to currently active agreements see the most current VL downloads catalog.

Customers are required to have existing perpetual or subscription licenses, or Software Assurance, ordered under the particular VL ID for any products downloaded from the catalog. To understand what licenses you have, see [View Contract Details](https://learn.microsoft.com/en-us/microsoft-365/commerce/licenses/view-vl-contracts).

### File types available for downloads

When you download products from the admin center, you can choose between the following file types:

- **Executable \(EXE\) files** are downloaded and installed on the same computer, but you can't create separate boot disks for installation on other computers.
- **ISO \(International Standards Organization\) image files** are exact representations of the content. You can install these files on the computer that's used to download the package or write the files to disks for distribution and installation on other computers.

Note

Not all products are available in all languages and in all formats.

### Products not available to download

In general, the VL catalog contains the most recent versions of software. However, there are some limited exceptions for older editions of products \(N-2 and beyond\) that might be available.

If you want to exercise your VL "downgrade right" to use prior versions of the software editions that you licensed, but the products are no longer available as Microsoft VL downloads, you might be able to source CD/DVD media from past shipments of "comprehensive kits" or "subscription kits" that you received. Alternatively, your Microsoft Resellers might still have inventory. However, Microsoft doesn't provide physical media for products bought through VL contracts

For more information on downgrade rights, download the following brief: [Downgrade rights for Microsoft Commercial Licensing](https://download.microsoft.com/download/3/D/4/3D42BDC2-6725-4B29-B75A-A5B04179958B/Licensing_brief_PLT_Downgrade_Rights.pdf)

### Client Access Licenses \(CALs\) don't require downloads

A Client Access License \(CAL\) is a license that gives a user the right to access the services of the server. You don't need a software download file or product key to activate a CAL. Instead, the product is activated and installed through the activation wizard directly from your computer.

Examples of CALs include:

- Windows Server
- SQL Server
- Exchange Server
- Skype for Business Server
- SharePoint Server
- System Center
- Project Server

## Save ISO files to disk or mount as a virtual drive

This section describes your options to either save ISO image files to a CD-R or DVD-R disk, or to mount the ISO files as a virtual drive.

### Save ISO image files to a disk

If you're using a PC with the Windows operating system, you don't need extra software to burn a CD-R or DVD-R disk. Double-click the ISO file that you downloaded, then follow the steps in the Image Burner Wizard.

If you're using an operating system other than Windows, you might need extra software. If your computer is equipped with a CD/DVD burner, the software is probably loaded on your PC. Most CD-R/DVD-R writing software lets you create a disk from an image file. To access this feature, select a menu item such as **Copy Image to CD** or **Burn Image to access**.

### Mount and access ISO files as a virtual drive

If you don't have a CD/DVD burner installed on your computer or media isn't available, you can mount the ISO file as a virtual drive. When you create a virtual drive, your computer believes that the file is a real disk drive, and can read files from it.

Important

We recommend that you only use a virtual drive to install apps like those for Microsoft 365 or for minor system upgrades. You can't install an operating system by using a virtual drive because the virtual drive disappears during the installation.

## Download volume licensing versions for PC and Mac

This section provides information about how to download VL software for PC and Mac.

### Download volume licensing versions of Office for PC

There are no full ISO Download files for the 2019, 2021 or 2024 versions of Office in the [admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339) under **Volume licensing**. Only Office Online Server has an ISO download. Instead, the installation files are available on the Office Content Delivery Network \(CDN\).

The VL download catalog includes the [Office Deployment Tool \(ODT\)](https://www.microsoft.com/download/details.aspx?id=49117) which you can download. The ODT provides more information about installation procedures.

For more information for IT Pros, see [Deployment Guide for Office 2024](https://learn.microsoft.com/en-us/office/ltsc/2024/deploy).

For non-IT Pros, the step-by-step instructions in [How to install Office 2019 installation files not found in VLSC](https://learn.microsoft.com/en-us/office/troubleshoot/installation/how-to-download-office-install-not-in-vlsc).

### Download Microsoft 365 for Mac

To run a VL version of Microsoft 365 for Mac, you must download and install the following files:

- The [Volume License \(VL\) Serializer](https://learn.microsoft.com/en-us/deployoffice/mac/volume-license-serializer) package located in the Microsoft 365 for Mac download file.
- The [Microsoft 365 for Mac installation package](https://learn.microsoft.com/en-us/officeupdates/update-history-office-for-mac#most-current-packages-for-office-for-mac). Installer package files for individual applications are also available in the admin center. Microsoft 365 for Mac doesn't require a product key because the VL Serializer is used to activate a volume licensed version of Microsoft 365 for Mac.
- Office for Mac versions 16.107 or later uses a unified first-run and sign-in experience that, in a volume licensing scenario, means sign-in prompts can appear during initial launch to support cloud-connected and hybrid scenarios, even on pre-licensed devices. To configure Office sign-in behavior to handle identity initialization automatically without prompting end users, see [Set suite-wide preferences for Office for Mac](https://learn.microsoft.com/en-us/microsoft-365-apps/mac/preferences-office).

## Convert from evaluation versions to volume licensing download versions

This section contains information about how to convert evaluation editions of Windows Server or Microsoft SQL Server to VL versions.

### Convert Windows Server evaluation edition

Before you deploy Windows Server VL download files, there are important considerations if you're upgrading from an Evaluation Edition of Window Server.

As described in [Windows Server Upgrade and Conversion Options](https://learn.microsoft.com/en-us/windows-server/get-started/upgrade-conversion-options), we recommend that you first [convert your evaluation version to a retail](https://learn.microsoft.com/en-us/windows-server/get-started/supported-upgrade-paths#converting-a-current-evaluation-version-to-a-current-retail-version) and then [convert your retail version to a volume licensing version](https://learn.microsoft.com/en-us/windows-server/get-started/supported-upgrade-paths#converting-a-current-retail-version-to-a-current-volume-licensed-version). While this process requires more effort, Microsoft Technical Support supports both upgrade paths.

Before you proceed, we highly recommend that you review the [Windows Server Installation and Upgrade documentation](https://learn.microsoft.com/en-us/windows-server/get-started/installation-and-upgrade), including the following articles:

- [Feature update, clean install, or migrate to Windows Server](https://learn.microsoft.com/en-us/windows-server/get-started/install-upgrade-migrate)
- [Perform a Feature Update of Windows Server](https://learn.microsoft.com/en-us/windows-server/get-started/perform-in-place-upgrade)
- [Upgrade and conversion options for Windows Server](https://learn.microsoft.com/en-us/windows-server/get-started/upgrade-conversion-options)

If you need further assistance during product installation or activation, you can reach the appropriate Microsoft Technical Support by [creating a technical support case](https://support.serviceshub.microsoft.com/supportforbusiness/create).

### Convert a Microsoft SQL Server evaluation version

It's possible to upgrade from an evaluation edition of Microsoft SQL Server to a production version without having to do a full install. To upgrade, you must perform an Edition Upgrade, which requires that you input a SQL license key. The license key is embedded in the software's activation wizard and isn't displayed in the VL product catalog.

To find the key, follow the steps in [Find out if a product is available to download](#find-out-if-a-product-is-available-to-download) to download the SQL ISO file. On your computer, open the *..\\x64* folder, then open the *DefaultSetup.ini* file to find the SQL License key.

If you already installed the evaluation version with a valid VLK ISO, run the Installation Center, and select the **Edition Upgrade** option. The VLK product key is automatically detected.

Before you attempt to upgrade, make sure to back up your existing version and review the documentation about the [SQL installation process](https://learn.microsoft.com/en-us/sql/database-engine/install-windows/install-sql-server?view=sql-server-ver16&preserve-view=true) and the [different supported upgrade paths from SQL Server versions](https://learn.microsoft.com/en-us/sql/database-engine/install-windows/supported-version-and-edition-upgrades-2019?view=sql-server-ver16&preserve-view=true).

If you need assistance with troubleshooting technical issues during product installation, you can reach the appropriate Microsoft Technical Support by [creating a technical support case](https://support.serviceshub.microsoft.com/supportforbusiness/create).

## Get technical support for downloaded products

Microsoft doesn't provide technical support as part of VL purchases. For technical support specific to the activation or installation of products bought through VL, customers must use other support options.

Customers can often resolve issues without assistance by using [Microsoft technical documentation](https://learn.microsoft.com/en-us/) or self-help articles like [How to install Office LTSC installation files not found in VLSC](https://learn.microsoft.com/en-us/office/troubleshoot/installation/how-to-download-office-install-not-in-vlsc).

Alternatively, you can [create a Microsoft technical support case](https://support.microsoft.com/oas). If your organization didn't buy a support plan, a fee might apply.

## Contact volume licensing support

Volume Licensing Services can help you navigate the VL experience in Microsoft 365 admin center, and confirm the availability of specific download files in the VL catalog.

Submit a case in the admin center > [Help & Support](https://go.microsoft.com/fwlink/p/?linkid=2166757). If you can't access the admin center, see [Contact volume licensing support](https://learn.microsoft.com/en-us/microsoft-365/commerce/licenses/contact-vl-support?view=o365-worldwide).

Tip

Creating your support case online before you phone support is faster, because your contact information is captured upfront and you immediately receive a case number to give to our support team when you call.

## Related content

[Product keys Frequently Asked Questions](https://learn.microsoft.com/en-us/microsoft-365/commerce/licenses/product-keys-faq?view=o365-worldwide) \(article\)  
[Manage volume licensing user roles](https://learn.microsoft.com/en-us/microsoft-365/commerce/licenses/manage-user-roles-vl?view=o365-worldwide) \(article\)
