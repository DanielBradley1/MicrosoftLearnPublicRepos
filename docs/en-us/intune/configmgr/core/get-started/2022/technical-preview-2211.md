<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2022/technical-preview-2211 -->
<!-- Sitemap-Last-Modified: 2022-11-30 -->

# Features in Configuration Manager technical preview version 2211

*Applies to: Configuration Manager \(technical preview branch\)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2211. Install this version to update and add new features to your technical preview site.

Review the [technical preview](https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Authorization failure message in admin service now shown in Status message viewer

Audit messages about authorization failure have been introduced in admin service. You can now view request details and status messages. These messages are shown in “All Status Message” at “Status Message Queries” in “Monitoring” ribbon. Previously these failures were logged in log files.

With the new audit messages we intend to avoid inconvenience of log files rollback. Details about the user, resource access attempts and the number of attempts for all the authorized requests made by user in a day will now be available. We're also auditing read operations for HTTPS requests and for cloud-initiated operations. This helps admins to scope permission and roles of users while also determining if there are any malicious users.

For more information, see [Administration Service documentation](https://learn.microsoft.com/en-us/intune/configmgr/develop/adminservice/overview).

## Network Access Account \(NAA\) account usage alert

Network Access Account \(NAA\) account usage alert

If your site is configured with NAA account, you'll see this new prerequisite warning added. To improve the security of distribution points configured with NAA account, review the existing accounts and their relevant permissions. If it has more than minimal required permission, then remove and add a minimal permission account. Don't configure any administrator level permission accounts on the NAA. If the site server is configured with HTTPS / EHTTP, we recommend removing NAA account, which is unused.

For more information, see the description of this [permissions-for-the-network-access-account](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/accounts#permissions-for-the-network-access-account).

## Improvements to Cloud Sync \(Collections to Microsoft Entra group Synchronization\) feature

Starting with Configuration Manager version 2211, the scalability of this feature has been improved with better throttling and error handling. Additionally, dedicated dashboards for user collections and device collections are added in Monitoring workspace to show Cloud Sync status. The dashboard displays the Cloud Sync status per collection with the mapped Microsoft Entra group, total member count, synced member count, status \(success, failed, in progress\) and last sync details.

## Next steps

For more information about installing or updating the technical preview branch, see [Technical preview](https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/technical-preview).

For more information about the different branches of Configuration Manager, see [Which branch of Configuration Manager should I use?](https://learn.microsoft.com/en-us/intune/configmgr/core/understand/which-branch-should-i-use).
