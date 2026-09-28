<!-- Source: https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/cross-tenant-synchronization-directory-extensions -->
<!-- Sitemap-Last-Modified: 2026-03-25 -->

# Map directory extensions in cross-tenant synchronization

## Overview

Directory extensions enable you to extend the schema in Microsoft Entra ID with your own attributes. You can map these directory extensions when provisioning users in cross-tenant synchronization. [Custom security attributes](https://learn.microsoft.com/en-us/entra/fundamentals/custom-security-attributes-overview) are different and aren't supported in cross-tenant synchronization.

This article describes how to map directory extensions in cross-tenant synchronization.

## Prerequisites

- [Hybrid Identity Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#hybrid-identity-administrator) role to configure cross-tenant synchronization.
- [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator) or [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator) role to assign users to a configuration and to delete a configuration.

## Create directory extensions

If you don't already have directory extensions, you must create one or more directory extensions in the source or target tenant. You can create extensions using Microsoft Entra Connect or Microsoft Graph API. For information on how to create directory extensions, see [Syncing extension attributes for Microsoft Entra Application Provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning-sync-attributes-for-mapping).

## Map directory extensions

![Icon for the source tenant.](https://learn.microsoft.com/en-us/entra/media/common/icons/entra-id-purple.png)  
**Source tenant**

Once you have one or more directory extensions, you can use them when mapping attributes in cross-tenant synchronization.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) of the source tenant.
2. Browse to **Entra ID** > **External Identities** > **Cross-tenant synchronization**.
3. Select **Configurations** and then select your configuration.
4. Select **Provisioning** and expand the **Mappings** section.

   [![Screenshot that shows the Provisioning page with the Mappings section expanded.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/common/provisioning-mappings.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/common/provisioning-mappings.png#lightbox)
5. Select **Provision Microsoft Entra ID Users** to open the **Attribute Mapping** page.
6. Scroll to the bottom of the page and select **Add new mapping**.

   [![Screenshot that shows the Attribute Mappings page with the Add new mapping link.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-directory-extensions/provisioning-mappings-new-mapping.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-directory-extensions/provisioning-mappings-new-mapping.png#lightbox)
7. In the **Source attribute** drop-down list, select a source attribute.

   If you created a directory extension in the source tenant, select the directory extension.

   [![Screenshot that shows the Edit attribute page with the directory extension listed in Source Attribute.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-directory-extensions/provisioning-mappings-source-attribute.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-directory-extensions/provisioning-mappings-source-attribute.png#lightbox)

   If the directory extension isn't listed, make sure that the directory extension was created successfully. You can also try to manually add the directory extension to the attribute list as described in the next section.
8. In the **Target attribute** drop-down list, select a target attribute.

   If you created a directory extension in the target tenant, select the directory extension.
9. Select **Ok** to save the mapping.

## Manually add directory extensions to the attribute list

![Icon for the source tenant.](https://learn.microsoft.com/en-us/entra/media/common/icons/entra-id-purple.png)  
**Source tenant**

If your directory extension wasn't automatically discovered, you can try the following steps to manually add the directory extension to the attribute list.

1. Sign in to the Microsoft Entra admin center of the source tenant using the following link:

   [https://entra.microsoft.com/?Microsoft\_AAD\_Connect\_Provisioning\_forceSchemaEditorEnabled=true](https://entra.microsoft.com/?Microsoft_AAD_Connect_Provisioning_forceSchemaEditorEnabled=true)
2. Browse to **Entra ID** > **External Identities** > **Cross-tenant synchronization**.
3. Select **Configurations** and then select your configuration.
4. Select **Provisioning** and expand the **Mappings** section.
5. Select **Provision Microsoft Entra ID Users** to open the **Attribute Mapping** page.
6. Scroll to the bottom and select the **Show advanced settings** checkbox.

   [![Screenshot of the Attribute Mapping page with advanced options displayed.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-directory-extensions/provisioning-mappings-advanced-settings.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-directory-extensions/provisioning-mappings-advanced-settings.png#lightbox)

   Tip

   If you don't see the **Edit attribute list** links, be sure that you are signed in to the Microsoft Entra admin center using the link in Step 1.
7. If you created a directory extension in the source tenant, select the **Edit attribute list for Microsoft Entra ID** link.
8. If you created an extension in the target tenant, select the **Edit attribute list for Azure Active Directory \(target tenant\)** link.
9. Add the directory extension and select the appropriate options.

   [![Screenshot of Edit Attributes List page with a directory extension added.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-directory-extensions/provisioning-mappings-advanced-settings-directory-extension.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-directory-extensions/provisioning-mappings-advanced-settings-directory-extension.png#lightbox)
10. Select **Save**.
11. Refresh the browser.
12. Browse to the **Attribute mappings** page and try to map the directory extension as described earlier in this article.

## Manually add directory extensions by editing the schema

![Icon for the source tenant.](https://learn.microsoft.com/en-us/entra/media/common/icons/entra-id-purple.png)  
**Source tenant**

Follow these steps to manually add directory extensions to the schema by using the schema editor.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) of the source tenant.
2. Browse to **Entra ID** > **External Identities** > **Cross-tenant synchronization**.
3. Select **Configurations** and then select your configuration.
4. Select **Provisioning** and expand the **Mappings** section.
5. Select **Provision Microsoft Entra ID Users** to open the **Attribute Mapping** page.
6. Scroll to the bottom and select the **Show advanced settings** checkbox.

   [![Screenshot of the Attribute Mapping page with link to schema editor.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-directory-extensions/provisioning-mappings-advanced-settings.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-directory-extensions/provisioning-mappings-advanced-settings.png#lightbox)
7. Select the **Review your schema here** link to open the **Schema editor** page.

   [![Screenshot of the Schema editor page the options to edit the schema in JSON.](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-directory-extensions/provisioning-mappings-schema-editor.png)](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/media/cross-tenant-synchronization-directory-extensions/provisioning-mappings-schema-editor.png#lightbox)
8. Download an original copy of the schema as a backup.
9. Modify the schema following your required configuration.
10. Select **Save**.
11. Refresh the browser.
12. Browse to the **Attribute mappings** page and try to map the directory extension as described earlier in this article.

## Next steps

- [Syncing extension attributes for Microsoft Entra Application Provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning-sync-attributes-for-mapping)
- [Configure cross-tenant synchronization](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/cross-tenant-synchronization-configure)
