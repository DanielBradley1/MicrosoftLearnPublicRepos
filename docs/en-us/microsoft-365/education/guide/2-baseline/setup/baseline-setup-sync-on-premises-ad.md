<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-sync-on-premises-ad -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Step 4: Sync your on-premises Active Directory

After you secured and configured your network, you're ready to sync your on-premises Active Directory with Microsoft 365. This step is crucial for managing your users and groups in one place.

First, choose the right authentication method for your Microsoft Entra hybrid identity solution. Then, install Microsoft Entra Connect Sync or configure Active Directory Federated Services \(AD FS\).

## Choose your authentication method

The following are the three ways to move your identities to Microsoft 365 using an on-premises Active Directory:

- Microsoft Entra Connect with password hash sync \(Recommended path\)

  <span class="mx-imgBorder">
  <a href="https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/setup/hybrid-password-hash-sync.png#lightbox" data-linktype="relative-path">
  <img src="https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/setup/hybrid-password-hash-sync.png" alt="Picture showing password hash sync with Microsoft Entra Connect." data-linktype="relative-path">
  </a>
  </span>

- Microsoft Entra Connect with passthrough authentication

  <span class="mx-imgBorder">
  <a href="https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/setup/hybrid-pass-through-auth.png#lightbox" data-linktype="relative-path">
  <img src="https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/setup/hybrid-pass-through-auth.png" alt="Picture showing Microsoft Entra Connect with Passthrough Authentication." data-linktype="relative-path">
  </a>
  </span>

- Active Directory Federated Services \(AD FS\)

  <span class="mx-imgBorder">
  <a href="https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/setup/hybrid-fed-auth.png#lightbox" data-linktype="relative-path">
  <img src="https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/setup/hybrid-fed-auth.png" alt="Picture showing Active Directory Federated Services." data-linktype="relative-path">
  </a>
  </span>

Note

For education scenarios:

- Entra Connect Sync is only needed if you are syncing users between your on-premises active directory and the cloud Entra ID system.
- [AD FS deployment](https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/ad-fs-deployment) is only needed if you need to create a federated authentication system for collaboration partners that reside outside your own tenant identity.

For more information, see [Choose the right authentication method for your Microsoft Entra hybrid identity solution](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/choose-ad-authn).

## Install Microsoft Entra Connect Sync

To install either cloud sync or Microsoft Entra Connect:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com/) as at least a [Hybrid Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#hybrid-identity-administrator).
2. Browse to **Identity > Hybrid management > Microsoft Entra Connect > Cloud sync**.

   <span class="mx-imgBorder">
   <a href="https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/setup/entra-connect-sync-1.png#lightbox" data-linktype="relative-path">
   <img src="https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/setup/entra-connect-sync-1.png" alt="Screenshot showing admin center for Microsoft Teams." data-linktype="relative-path">
   </a>
   </span>

3. On the left, select **Agent**.
4. Select **Download on-premises agent**, and select Accept terms & download.
5. After the Microsoft Entra provisioning agent package finishes downloading, run the AADConnectProvisioningAgentSetup.exe installation file from your downloads folder.
6. On the splash screen, select **I agree to the license and conditions**, and then select **Install**.
7. After the installation operation completes, the configuration wizard launches. Select **Next** to start the configuration.
8. On the **Select Extension screen**, select HR-driven provisioning **\(Workday and SuccessFactors\) / Microsoft Entra Connect cloud sync** and select **Next**.
9. Sign in with your Microsoft Entra Global Administrator account.
10. On the **Configure Service Account** screen, select a group Managed Service Account \(gMSA\). This account is used to run the agent service. To continue, select **Next**.
11. On the **Connect Active Directory** screen, if your domain name appears under **Configured domains**, skip to the next step. Otherwise, type your Active Directory domain name, and select **Add directory**.
12. Sign in with your Active Directory domain administrator account. Select **OK**, then select **Next** to continue.
13. Select **Next** to continue.
14. On the **Configuration** complete screen, select **Confirm**.
15. Once this operation completes, you should be notified that **Your agent configuration was successfully verified**. You can select **Exit**.
16. If you still get the initial splash screen, select **Close**.

## Configure Active Directory Federated Services \(AD FS\)

Use these links to see instructions on how to install AD FS role service, depending on your method of choice:

- [Via the **Add roles and features** wizard](https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/install-the-ad-fs-role-service#to-install-the-ad-fs-server-role-via-the-add-roles-and-features-wizard)
- [Via Windows PowerShell](https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/install-the-ad-fs-role-service#to-install-the-ad-fs-server-role-via-windows-powershell)

## Next steps

Next, lets learn about user provisioning.

[Next: User provisioning>](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-user-provisioning)
