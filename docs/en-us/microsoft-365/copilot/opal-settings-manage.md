<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/opal-settings-manage -->
<!-- Sitemap-Last-Modified: 2026-08-18 -->

# Get started with Opal in Microsoft Copilot

Note

We've introduced updates to the default Opal configuration. Tenants who onboarded to Opal before April must manually make changes in the Opal Admin Center. There are new supported capabilities for admins and users. For more information, see the sections [Default website access behavior](#default-website-access-behavior) and [File interaction support on Windows 365 Cloud PC](#file-interaction-support-on-windows-365-cloud-pc).

Opal helps users complete jobs with CUA on a secure, Entra-joined, and Intune-enrolled [Windows 365 for Agents Cloud PC](https://learn.microsoft.com/en-us/windows-365/overview). The agent operates within a Microsoft Edge browser, and users can supervise the agent to complete the job, intervening when necessary. Common use cases include:

- Collecting evidence for audit reviews
- Submitting timesheets for your team
- Adding multiple users to security groups

This article provides guidance for administrators on how to set up and manage Opal.

## Licensing Requirements

- You must have an Intune license.
- You must have a Microsoft Entra ID P1 license.
- Individual users must have Microsoft Copilot licenses.

## Setting up Opal

Opal is currently available only in the **Microsoft Frontier program** with a Microsoft Copilot subscription. Frontier includes early access to experimental features, which means features might change as Microsoft improves them. For more information, see [Get started with the Microsoft Frontier program](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/get-started-frontier).

1. Go to the [Microsoft 365 admin center](https://admin.microsoft.com).
2. Go to **Copilot** and then **Settings**.
3. Locate the user access setting titled **Opal \(Frontier\)**.
4. Select the group of users who should have access to Opal.

After you enable Opal in the Microsoft 365 admin center, complete more setup in the [Opal Admin Portal](https://go.microsoft.com/fwlink/?linkid=2340266) by using the following steps:

1. **Get Started**

   - Once you land on the Opal Admin page, click **"Get started"**.
   - This initial setup creates a device group, device policy, and assigns the policy to your group. You can find these resources in Intune and they apply to the Cloud PCs created by Opal. Don't delete or adjust these resources. **Any changes you make to these resources might cause the Opal app to not function as expected or break entirely.**

2. **Cloud PC Setup**

   - We have also created a pool of Cloud PCs on your behalf. Come back to this page to adjust the pool at any time.
   - You can choose for Opal to allow all websites with a blocklist, or block all sites with an allowlist. If you choose to block all sites with an allowlist, make sure to set up the allowlist under **Manage Access**.

3. **Tenant Configuration**

   - Write instructions for Opal. Opal remembers the instructions for every job in your organization. Include information such as your organization name, preferred websites, and so on.
   - Configure starters for the Opal home page. Everyone in your organization sees these starters; they help users understand the types of jobs that Opal can accomplish.

## Accessing Opal

Users can find Opal in the Microsoft Copilot app in the top left navigation. When accessed, it opens in an external new tab.

For more information, see [Get started with Opal in Microsoft Copilot](https://go.microsoft.com/fwlink/?linkid=2341525).

### Default website access behavior

Opal now allows access to all websites by default. Administrators can block specific URLs as needed by using Opal policies.

Previously, Opal blocked access to all websites by default. Administrators had to manually allow list individual URLs for Opal to interact with them.

If your organization prefers the previous behavior, re-enable the block-by-default model by using the toggle in the Opal Admin Center.

### File interaction support on Windows 365 Cloud PC

Opal now supports interaction with files stored on Windows 365 Cloud PC. Following internal security reviews, Opal can download and upload files when the appropriate policies are enabled.

To enable file interaction capabilities for existing tenants, administrators must manually update the following Microsoft Intune policies within **Opal App Device Policy**, using Intune.

1. Go to Microsoft Intune.
2. Go to Devices > configuration and find **Opal App Device Policy**.
3. In the policy:
4. Select **Enabled** for **Control use of the File System API for reading**.
5. Select **Allow sites to ask the user to grant read access to files and directories** for **Control use of the File System API for reading \(Device\)**.
6. Select **Enabled** for **Control use of the File System API for writing**.
7. Select **Allow sites to ask the user to grant write access to files and directories** for **Control use of the File System API for writing \(Device\)**.

   ![Screenshot of Opal device policy.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/microsoft-365-copilot-opal-get-started/opal-app-device-policy.png)
8. Select **Enabled** for **Allow download restrictions**.

   ![Screenshot of allow download instructions.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/microsoft-365-copilot-opal-get-started/allow-download-restrictions.png)
9. Select **Block** for **Download restrictions \(Device\)**.
