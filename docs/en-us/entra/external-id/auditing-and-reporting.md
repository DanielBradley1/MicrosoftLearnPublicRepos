<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/auditing-and-reporting -->
<!-- Sitemap-Last-Modified: 2025-04-25 -->

# Auditing and reporting a B2B collaboration user

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to workforce tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) Workforce tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

With guest users, you have auditing capabilities similar to with member users.

## Access reviews

You can use access reviews to periodically verify whether guest users still need access to your resources. The **Access reviews** feature is available in **Microsoft Entra ID** under **ID Governance** > **Access reviews**. To learn how to use access reviews, see [Manage guest access with Microsoft Entra access reviews](https://learn.microsoft.com/en-us/entra/id-governance/manage-guest-access-with-access-reviews).

## Audit logs

The Microsoft Entra audit logs provide records of system and user activities, including activities initiated by guest users. To access audit logs, browse to **Entra ID** > **Monitoring & health** > **Audit logs**. To access audit logs of one specific user, select **Entra ID** > **Users** > select the user > **Audit logs**.

[![Screenshot showing an example of audit log output.](https://learn.microsoft.com/en-us/entra/external-id/media/auditing-and-reporting/audit-log.png)](https://learn.microsoft.com/en-us/entra/external-id/media/auditing-and-reporting/audit-log-large.png#lightbox)

You can dive into each of these events to get the details. For example, let's look at the user management details.

[![Screenshot showing an example of activity details output.](https://learn.microsoft.com/en-us/entra/external-id/media/auditing-and-reporting/activity-details.png)](https://learn.microsoft.com/en-us/entra/external-id/media/auditing-and-reporting/activity-details-large.png#lightbox)

You can also export these logs from Microsoft Entra ID and use the reporting tool of your choice to get customized reports.

## Sponsors field for B2B users

You can also manage and track your guest users in the organization using the sponsors feature. The **Sponsors** field on the user account displays who is responsible for the guest user. A sponsor can be a user or a group. To learn more about the sponsors feature, see [Add sponsors to a guest user](https://learn.microsoft.com/en-us/entra/external-id/b2b-sponsors).

### Related content

- [Troubleshoot B2B collaboration](https://learn.microsoft.com/en-us/entra/external-id/troubleshoot)
