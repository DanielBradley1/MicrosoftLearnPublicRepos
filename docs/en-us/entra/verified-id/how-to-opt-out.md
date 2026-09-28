<!-- Source: https://learn.microsoft.com/en-us/entra/verified-id/how-to-opt-out -->
<!-- Sitemap-Last-Modified: 2026-03-17 -->

# Opt out of Microsoft Entra Verified ID

## Overview

Opting out is the process of resetting your Microsoft Entra Verified ID environment.

## When do you need to opt out?

Opting out is a one-way operation. After the process finishes, your Microsoft Entra Verified ID environment is reset. You might need to opt out to:

- Enable new service capabilities.
- Reset your service configuration.
- Switch between the ION and web trust systems.

## What happens to your data?

When you finish opting out of the Microsoft Entra Verified ID service, the following actions occur:

- The decentralized identifier \(DID\) keys in Azure Key Vault are [soft deleted](https://learn.microsoft.com/en-us/azure/key-vault/general/soft-delete-overview).
- The issuer object is deleted from the database.
- The tenant identifier is deleted from the database.
- All the verifiable credentials contracts are deleted from the database.

After an opt-out action takes place, you can't recover your DID or conduct any operations on your DID. This step is a one-way operation, and you need to onboard again. Onboarding again creates a new environment.

## Effect on existing verifiable credentials

All verifiable credentials already issued continue to exist. For the ION trust system, they aren't cryptographically invalidated because your DIDs remain resolvable through ION. However, when relying parties call the status API, they always receive a failure message.

## Opt out of Microsoft Entra Verified ID

1. From the **Azure portal**, search for verifiable credentials.
2. Select **Organization Settings** on the leftmost menu.
3. In the section **Reset your organization**, select **Delete all credentials and reset service**.

   ![Screenshot that shows the section on the Organization settings page where you reset your organization.](https://learn.microsoft.com/en-us/entra/verified-id/media/how-to-opt-out/settings-reset.png)
4. Read the warning message and select **Delete & opt out** to continue.

   ![Screenshot that shows Delete & opt out.](https://learn.microsoft.com/en-us/entra/verified-id/media/how-to-opt-out/delete-and-opt-out.png)

## Next steps

- Set up verifiable credentials on your [Azure tenant](https://learn.microsoft.com/en-us/entra/verified-id/verifiable-credentials-configure-tenant).
