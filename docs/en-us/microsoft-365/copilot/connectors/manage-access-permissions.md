<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/manage-access-permissions -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# Manage access permissions for connectors

Microsoft 365 Copilot connectors index content from external data sources into Microsoft 365 Copilot and Microsoft Copilot. To ensure secure and compliant access, the access permissions configured during connector setup must reflect your organization's intended visibility model. Incorrect access permission settings, such as granting access to **Everyone**, can lead to oversharing of sensitive content.

You can review and validate access permissions for each Microsoft 365 Copilot connector from the connection details pane in the Microsoft 365 admin center. This article describes how to verify whether the configured permissions align with your intended settings, and how to update them.

## View and update access permissions

To manage access permissions for a configured connector:

1. In the [Microsoft 365 Admin Center](https://admin.microsoft.com), go to **Copilot** > **Connectors** > **Your Connections**.
2. Select the connector you want to review to open the details pane.
3. Under **Permissions**, you can view the permissions set for the connector. One of the following permissions is applied:

   - **Only people with access to this data source**: The connector respects source system access control lists \(ACLs\).
   - **Visible to everyone**: The connector grants access to all users in the organization.

If the access permissions configured for the connector don't match your intended visibility model:

1. In the connector pane, choose **Delete** to delete the existing connection.
2. Recreate the connection using the **Custom setup** flow and explicitly configure access permissions.

Note

Updating access permissions after you create the connection isn't currently supported.

## Related content

- [Deploy Microsoft 365 Copilot connectors](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/deployment-overview)
- [Microsoft-built synced connectors](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/prebuilt-connectors-overview)
