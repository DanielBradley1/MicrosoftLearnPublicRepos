<!-- Source: https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/how-to-on-demand-provision -->
<!-- Sitemap-Last-Modified: 2026-09-24 -->

# On-demand provisioning - Active Directory to Microsoft Entra ID

You can use the cloud sync feature of Microsoft Entra Connect to test configuration changes by applying these changes to a single user. This on-demand provisioning helps you validate and verify that the changes made to the configuration were applied properly and are being correctly synchronized to Microsoft Entra ID.

This article covers on-demand provisioning for configurations that provision from Active Directory to Microsoft Entra ID. If you're looking for information about provisioning from Microsoft Entra ID to Active Directory, see [On-demand provisioning - Microsoft Entra ID to Active Directory](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/how-to-on-demand-provision-entra-to-active-directory).

Important

When you use on-demand provisioning, the scoping filters are not applied to the user that you selected. You can use on-demand provisioning on users who are outside the organization units that you specified.

For additional information and an example see the following video.

<iframe src="https://learn-video.azurefd.net/vod/player?id=abcf1d11-c101-49a6-ab56-cdc45cc34817" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

## Validate a user

To use on-demand provisioning, follow these steps:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Hybrid Identity Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#hybrid-identity-administrator).
2. Browse to **Entra ID** > **Entra Connect** > **Cloud sync**.

   [![Screenshot that shows the Microsoft Entra Connect Cloud Sync home page.](https://learn.microsoft.com/en-us/entra/includes/media/cloud-sync-sign-in/cloud-sync-configurations.png)](https://learn.microsoft.com/en-us/entra/includes/media/cloud-sync-sign-in/cloud-sync-configurations.png#lightbox)

3. Under **Configuration**, select your configuration.
4. On the left, select **Provision on demand**.
5. Enter the distinguished name of a user and select the **Provision** button.

[![Screenshot of user distinguished name.](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-on-demand-provision/new-ux-2.png)](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-on-demand-provision/new-ux-2.png#lightbox)

6. After provisioning finishes, a success screen appears with four green check marks. Any errors appear to the left.

[![Screenshot of on-demand success.](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-on-demand-provision/new-ux-3.png)](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-on-demand-provision/new-ux-3.png#lightbox)

## Get details about provisioning

Now you can look at the user information and determine if the changes that you made in the configuration have been applied. The rest of this article describes the individual sections that appear in the details of a successfully synchronized user.

### Import user

The **Import user** section provides information on the user who was imported from Active Directory. This is what the user looks like before provisioning into Microsoft Entra ID. Select the **View details** link to display this information.

By using this information, you can see the various attributes \(and their values\) that were imported. If you created a custom attribute mapping, you can see the value here.

[![Screenshot of import user.](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-on-demand-provision/new-ux-4.png)](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-on-demand-provision/new-ux-4.png#lightbox)

### Determine if user is in scope

The **Determine if user is in scope** section provides information on whether the user who was imported to Microsoft Entra ID is in scope. Select the **View details** link to display this information.

By using this information, you can see if the user is in scope.

[![Screenshot of scope determination.](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-on-demand-provision/new-ux-5.png)](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-on-demand-provision/new-ux-5.png#lightbox)

### Match user between source and target system

The **Match user between source and target system** section provides information on whether the user already exists in Microsoft Entra ID and whether a join should occur instead of provisioning a new user. Select the **View details** link to display this information.

By using this information, you can see whether a match was found or if a new user is going to be created.

[![Screenshot of matching user.](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-on-demand-provision/new-ux-6.png)](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-on-demand-provision/new-ux-6.png#lightbox)

The matching details show a message with one of the three following operations:

- **Create**: A user is created in Microsoft Entra ID.
- **Update**: A user is updated based on a change made in the configuration.
- **Delete**: A user is removed from Microsoft Entra ID.

Depending on the type of operation that you've performed, the message varies.

### Perform action

The **Perform action** section provides information on the user who was provisioned or exported into Microsoft Entra ID after the configuration was applied. This is what the user looks like after provisioning into Microsoft Entra ID. Select the **View details** link to display this information.

By using this information, you can see the values of the attributes after the configuration was applied. Do they look similar to what was imported, or are they different? Was the configuration applied successfully?

This process enables you to trace the attribute transformation as it moves through the cloud and into your Microsoft Entra tenant.

[![Screenshot of perform action.](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-on-demand-provision/new-ux-7.png)](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-on-demand-provision/new-ux-7.png#lightbox)

## Next steps

- [What is Microsoft Entra Cloud Sync?](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/what-is-cloud-sync)
- [Install Microsoft Entra Cloud Sync](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/how-to-install)
