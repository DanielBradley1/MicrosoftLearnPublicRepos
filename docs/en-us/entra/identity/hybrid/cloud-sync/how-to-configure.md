<!-- Source: https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/how-to-configure -->
<!-- Sitemap-Last-Modified: 2026-09-14 -->

# Provision Active Directory to Microsoft Entra ID - Configuration

The following document will guide you through configuring Microsoft Entra Cloud Sync for provisioning from Active Directory to Microsoft Entra ID. If you are looking for information on provisioning from Microsoft Entra ID to AD, see [Configure - Provisioning Active Directory to Microsoft Entra ID using Microsoft Entra Cloud Sync](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/how-to-configure-entra-to-active-directory)

The following documentation demonstrates the new guided user experience for Microsoft Entra Cloud Sync.

For additional information and an example of how to configure cloud sync, see the video below.

<iframe src="https://learn-video.azurefd.net/vod/player?id=f88ca6c8-8308-4a63-a1b1-53de75214298" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

## Configure provisioning

To configure provisioning, follow these steps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Hybrid Identity Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#hybrid-identity-administrator).
2. Browse to **Entra ID** > **Entra Connect** > **Cloud sync**.

   [![Screenshot that shows the Microsoft Entra Connect Cloud Sync home page.](https://learn.microsoft.com/en-us/entra/includes/media/cloud-sync-sign-in/cloud-sync-configurations.png)](https://learn.microsoft.com/en-us/entra/includes/media/cloud-sync-sign-in/cloud-sync-configurations.png#lightbox)

3. Select **New configuration**.
4. Select **AD to Microsoft Entra ID sync**.

   <span class="mx-imgBorder">
   <a href="https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/configure-1.png#lightbox" data-linktype="relative-path">
   <img src="https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/configure-1.png" alt="Screenshot of adding a configuration." data-linktype="relative-path">
   </a>
   </span>

5. On the configuration screen, select your domain and whether to enable password hash sync. Click **Create**.

[![Screenshot of a new configuration.](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/new-ux-configure-2.png)](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/new-ux-configure-2.png#lightbox)

6. The **Get started** screen will open. From here, you can continue configuring cloud sync.

[![Screenshot of the getting started screen.](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/new-ux-configure-3.png)](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/new-ux-configure-3.png#lightbox)

7. The configuration is split in to the following 5 sections.

| Section | Description |
| --- | --- |
| 1. Add [scoping filters](#scope-provisioning-to-specific-users-and-groups) | Use this section to define what objects appear in Microsoft Entra ID |
| 2. Map [attributes](#attribute-mapping) | Use this section to map attributes between your on-premises users/groups with Microsoft Entra objects |
| 3. [Test](#on-demand-provisioning) | Test your configuration before deploying it |
| 4. View [default properties](#accidental-deletions-and-email-notifications) | View the default setting prior to enabling them and make changes where appropriate |
| 5. Enable [your configuration](#enable-your-configuration) | Once ready, enable the configuration and users/groups will begin synchronizing |

## Scope provisioning to specific users and groups

By default the provisioning agent will synchronize a subset of the users and groups from your Active Directory. You can further scope the agent to synchronize specific users and groups by using on-premises Active Directory groups or organizational units.

[![Screenshot of scoping filters icon.](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/new-ux-configure-4.png)](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/new-ux-configure-4.png#lightbox)

You can configure groups and organizational units within a configuration.

Note

You cannot use nested groups with group scoping. Nested objects beyond the first level will not be included when scoping using security groups. Only use group scope filtering for pilot scenarios as there are limitations to syncing large groups.

1. On the **Getting started** configuration screen. Click either **Add scoping filters** next to the **Add scoping filters** icon or on the click **Scoping filters** on the left under **Manage**.

[![Screenshot of scoping filters.](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/new-ux-configure-5.png)](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/new-ux-configure-5.png#lightbox)

2. Select the scoping filter. The filter can be one of the following:

   - **All users**: Scopes the configuration to apply to all users that are being synchronized.
   - **Selected security groups**: Scopes the configuration to apply to specific security groups.
   - **Selected organizational units**: Scopes the configuration to apply to specific OUs.

3. For security groups and organizational units, supply the appropriate distinguished name and click **Add**.
4. Once your scoping filters are configured, click **Save**.
5. After saving, you should see a message telling you what you still need to do to configure cloud sync. You can click the link to continue.

   <span class="mx-imgBorder">
   <a href="https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/new-ux-configure-16.png#lightbox" data-linktype="relative-path">
   <img src="https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/new-ux-configure-16.png" alt="Screenshot of the nudge for scoping filters." data-linktype="relative-path">
   </a>
   </span>

6. Once you've changed the scope, you should [restart provisioning](#restart-provisioning) to initiate an immediate synchronization of the changes.

## Attribute mapping

Microsoft Entra Cloud Sync allows you to easily map attributes between your on-premises user/group objects and the objects in Microsoft Entra ID.

[![Screenshot of map attributes icon.](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/new-ux-configure-6.png)](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/new-ux-configure-6.png#lightbox)

You can customize the default attribute-mappings according to your business needs. So, you can change or delete existing attribute-mappings, or create new attribute-mappings.

[![Screenshot of default attribute mappings.](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/new-ux-configure-7.png)](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/new-ux-configure-7.png#lightbox)

After saving, you should see a message telling you what you still need to do to configure cloud sync. You can click the link to continue.  [![Screenshot of the nudge for attribute filters.](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/new-ux-configure-17.png)](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/new-ux-configure-17.png#lightbox)

For more information, see [attribute mapping](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/how-to-attribute-mapping).

## Directory extensions and custom attribute mapping.

Microsoft Entra Cloud Sync allows you to extend the directory with extensions and provides for custom attribute mapping. For more information see [Directory extensions and custom attribute mapping](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/custom-attribute-mapping).

## On-demand provisioning

Microsoft Entra Cloud Sync allows you to test configuration changes, by applying these changes to a single user or group.

[![Screenshot of test icon.](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/new-ux-configure-8.png)](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/new-ux-configure-8.png#lightbox)

You can use this to validate and verify that the changes made to the configuration were applied properly and are being correctly synchronized to Microsoft Entra ID.

[![Screenshot of on-demand provisioning.](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/new-ux-configure-9.png)](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/new-ux-configure-9.png#lightbox)

After testing, you should see a message telling you what you still need to do to configure cloud sync. You can click the link to continue.  [![Screenshot of the nudge for testing.](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/new-ux-configure-18.png)](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/new-ux-configure-18.png#lightbox)

For more information, see [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/how-to-on-demand-provision).

## Accidental deletions and email notifications

The default properties section provides information on accidental deletions and email notifications.

[![Screenshot of default properties icon.](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/new-ux-configure-10.png)](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/new-ux-configure-10.png#lightbox)

The accidental delete feature is designed to protect you from accidental configuration changes and changes to your on-premises directory that would affect many users and groups.

This feature allows you to:

- configure the ability to prevent accidental deletes automatically.
- Set the # of objects \(threshold\) beyond which the configuration will take effect
- set up a notification email address so they can get an email notification once the sync job in question is put in quarantine for this scenario

For more information, see [Accidental deletes](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/how-to-accidental-deletes)

Click the **pencil** next to **Basics** to change the defaults in a configuration.

[![Screenshot of basics.](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/new-ux-configure-11.png)](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/new-ux-configure-11.png#lightbox)

## Enable your configuration

Once you've finalized and tested your configuration, you can enable it.

[![Screenshot of review and enable icon.](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/new-ux-configure-12.png)](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/new-ux-configure-12.png#lightbox)

Click **Enable configuration** to enable it.

[![Screenshot of enabling a configuration.](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/new-ux-configure-13.png)](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/new-ux-configure-13.png#lightbox)

## Quarantines

Cloud sync monitors the health of your configuration and places unhealthy objects in a quarantine state. If most or all of the calls made against the target system consistently fail because of an error, for example, invalid admin credentials, the sync job is marked as in quarantine. For more information, see the troubleshooting section on [quarantines](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/how-to-troubleshoot#provisioning-quarantined-problems).

## Restart provisioning

If you don't want to wait for the next scheduled run, trigger the provisioning run by using the **Restart sync** button.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Hybrid Identity Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#hybrid-identity-administrator).
2. Browse to **Entra ID** > **Entra Connect** > **Cloud sync**.

   [![Screenshot that shows the Microsoft Entra Connect Cloud Sync home page.](https://learn.microsoft.com/en-us/entra/includes/media/cloud-sync-sign-in/cloud-sync-configurations.png)](https://learn.microsoft.com/en-us/entra/includes/media/cloud-sync-sign-in/cloud-sync-configurations.png#lightbox)

4. Under **Configuration**, select your configuration.

[![Screenshot of restarting sync.](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/new-ux-configure-14.png)](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/new-ux-configure-14.png#lightbox)

5. At the top, select **Restart sync**.

## Remove a configuration

To delete a configuration, follow these steps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Hybrid Identity Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#hybrid-identity-administrator).
2. Browse to **Entra ID** > **Entra Connect** > **Cloud sync**.

   [![Screenshot that shows the Microsoft Entra Connect Cloud Sync home page.](https://learn.microsoft.com/en-us/entra/includes/media/cloud-sync-sign-in/cloud-sync-configurations.png)](https://learn.microsoft.com/en-us/entra/includes/media/cloud-sync-sign-in/cloud-sync-configurations.png#lightbox)

3. Under **Configuration**, select your configuration.

[![Screenshot of deletion.](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/new-ux-configure-15.png)](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/media/how-to-configure/new-ux-configure-15.png#lightbox)

4. At the top of the configuration screen, select **Delete configuration**.

Important

There's no confirmation prior to deleting a configuration. Make sure this is the action you want to take before you select **Delete**.

## Agent removal from the portal after uninstall

When you [uninstall](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/how-to-automatic-upgrade#uninstall-the-agent) or stop a Microsoft Entra Cloud Sync agent, the agent isn't removed from the Microsoft Entra admin center immediately. The following timeline describes the agent removal process:

| Timeframe | Portal behavior |
| --- | --- |
| After approximately 1 hour | The agent shows as **Inactive** in the portal. |
| After approximately 10 days | The agent is soft-deleted and no longer appears in the portal. |
| When the agent certificate expires | The agent is permanently removed and can no longer interact with Microsoft services. |

If you don't want to wait for automatic cleanup, you can manually remove the agent configuration from the portal by deleting the configuration associated with the agent.

## Next steps

- [What is provisioning?](https://learn.microsoft.com/en-us/entra/identity/hybrid/what-is-provisioning)
- [What is Microsoft Entra Cloud Sync?](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/what-is-cloud-sync)
