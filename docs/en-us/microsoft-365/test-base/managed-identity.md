<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/test-base/managed-identity?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# Grant Test Base managed identities to your Key Vault account

Important

**Test Base for Microsoft 365 will transition to end-of-life \(EOL\) on May 31, 2024.** We're committed to working closely with each customer to provide support and guidance to make the transition as smooth as possible. If you have any questions, concerns, or need assistance, [submit a support request](https://aka.ms/TestBaseSupport).

This article includes step-by-step guidance to grant Test Base access to your key vault secrets so that you can authorize Test Base access to other platforms during your compatibility tests in a secure way.

**In this article,**

- [Prerequisite](#Prerequisite)
- [Grant Test Base managed identities to your Key Vault account](#GrantTestBaseAccess)

**Relevant links**

- [Importing Intune Credential in Test Base](https://aka.ms/testbase-doc-IntuneEnrollment)

### Prerequisite

- Resource group and Subscription are already known for your project.
- Test Base Account and Azure Key Vault Accounts are created.

*Reference*

1. [*Creating a Test Base Account \| Microsoft Learn*](https://learn.microsoft.com/en-us/microsoft-365/test-base/createaccount?view=o365-worldwide)
2. [*Creating an Azure Key Vault Account*](https://learn.microsoft.com/en-us/azure/key-vault/general/quick-create-portal)

### Grant Test Base managed identities to your Key Vault account

1. Turn on **System assigned** identity in Test Base: Go to **Manage** > **Identity** > **System assigned** to enable managed identity in Test Base

[![Screenshot of the identity page.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/manage-identities-1.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/manage-identities-1.png?view=o365-worldwide#lightbox)

2. Click on the copy button \( ![icon of the copy button.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/manage-identities-copy-button.png?view=o365-worldwide) \) to copy Test Base system assigned **Object ID**
3. Assign Key Vault access to Test Base:

   Before assigning Key Vault access, please check your Key Vault configuration: Go to **Settings** > **Access configuration**.  [![Screenshot of the access configuration page.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/manage-identities-2.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/manage-identities-2.png?view=o365-worldwide#lightbox) Depending on your permission model, please select below guidance:

   > a. [Grant Key Vault access to Test Base **when your Permission model is Azure role-based access control**.](#KeyVaultRBAC)  
   > b. [Grant Key Vault access to Test Base **when your Permission model is Vault access policy**.](#KeyVaultAccessPolicy)


   1. Grant Key Vault access to Test Base **when your Permission model is Azure role-based access control**.

      Reference: [Grant a user access to Azure resources using the Azure portal - Azure RBAC \| Microsoft Learn](https://learn.microsoft.com/en-us/azure/role-based-access-control/quickstart-assign-role-user-portal)

      1\). Open your Test Base account, select **Manage** > **Identity** > **Azure role assignments**.  [![Screenshot for showing the Azure role assignments button.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/manage-identities-3.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/manage-identities-3.png?view=o365-worldwide#lightbox) 2\). Click on **Add role assignment**.  [![Screenshot of add role assignment.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/manage-identities-4.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/manage-identities-4.png?view=o365-worldwide#lightbox) 3\). Set Scope as **Key Vault**. Select Subscription and Resource. Select the Role as **Key Vault Secrets User**.  [![Screenshot of add role assignment preview.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/manage-identities-5.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/manage-identities-5.png?view=o365-worldwide#lightbox) 4\). Repeat step b-c and select the Role as **Key Vault Reader**.
   2. Grant Key Vault access to Test Base **when your Permission model is Vault access policy**.

      Reference: [Assign an Azure Key Vault access policy \(CLI\) \| Microsoft Learn](https://learn.microsoft.com/en-us/azure/key-vault/general/assign-access-policy?tabs=azure-portal)

      1\). Select **Access policies** , then select **Create**  [![Screenshot of Access policies page.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/manage-identities-6.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/manage-identities-6.png?view=o365-worldwide#lightbox) 2\). **Select all** permissions under **Secret** permissions  [![Screenshot of create an access policy.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/manage-identities-7.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/manage-identities-7.png?view=o365-worldwide#lightbox) 3\). Under the **Principal** selection pane, paste **Test Base Object ID**  [![Screenshot of the principal of create an access policy.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/manage-identities-8.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/manage-identities-8.png?view=o365-worldwide#lightbox) 4\). Click **Next** to continue.

      5\). Review the access policy changes and select **Create** to save the access policy  [![Screenshot of review and create.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/manage-identities-9.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/manage-identities-9.png?view=o365-worldwide#lightbox)
