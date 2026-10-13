<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/granting-table-access-servicenow-knowledge -->
<!-- Sitemap-Last-Modified: 2026-10-12 -->

# Grant table access to an account in ServiceNow Knowledge

This article explains how to grant table access to a service account in ServiceNow Knowledge. The process involves creating a role, assigning it to a user, and configuring row-level and field-level access controls.

Tip

Instead of following the manual steps in this article, you can run background scripts that create the user, role, and ACLs automatically. For more information, see [Set up prerequisites using background scripts](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/servicenow-knowledge-setup-scripts).

## Prerequisites

- Admin access in ServiceNow.
- Elevate to the `security_admin` role to make changes to access control lists \(ACLs\).

## Create a user

To create a user:

1. Go to **User Administration** > **Users**.
2. Select **New** to create a new user.
3. Fill in the user details:

   - For the **User ID**: `microsoft.copilot`. The **User ID** is required for successful crawls.
   - For the **First Name** and **Last Name**: `Microsoft` and `Copilot`.
   - Set **Identity Type** to `Machine`. For earlier versions of ServiceNow, check **Web service access only**.

4. Select **Submit** to save the user.

## Create a role

To create a role:

1. Go to **User Administration** > **Roles**.
2. Select **New**.
3. Enter a unique name for the role, such as `Copilot Connector Account`.
4. Select **Submit** to save the role.

## Assign the role to a user

To assign the role to a user:

1. Go to **User Administration** > **Users**.
2. Open the user record for the intended user, such as `Microsoft Copilot`.
3. In the **Roles** related list, select **Edit**.
4. Add the newly created role \(`Copilot Connector Account`\).

   Note

   - To index knowledge articles without blocking ACL problems, you might also assign the following roles to the service account: `knowledge_admin`, `user_criteria_admin`, and `user_admin`. Assigning these roles is optional.
   - If your ServiceNow instance uses the HR Service Delivery module with knowledge bases in the **Human Resources: Core** \(`sn_hr_core`\) application scope, also assign `sn_hr_core.content_reader` \(or `sn_hr_core.admin` for broader access\). Without one of these roles, the service account can't read HR-scoped user criteria, and HR articles might be indexed as accessible to all users. For more information, see [Additional roles for HR Service Delivery \(HRSD\) content](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/servicenow-knowledge-admin-setup#additional-roles-for-hr-service-delivery-hrsd-content).

5. Select **Save** to finalize the assignment.
6. Select **Update** to update the user record.

## Grant row-level access

To grant access to rows within a specific table, follow these steps:

1. Elevate to the `security_admin` role.
2. Go to **System Security** > **Access Control \(ACL\)**.
3. Select **New** to create a new ACL record.
4. Fill in the following fields:

   - **Type**: Select **record**.
   - **Operation**: Choose the `read` operation.
   - **Name**: Enter the table name \(for example, `sys_dictionary`\).

5. In the **Roles** section, add the previously created role \(`Copilot Connector Account`\).
6. Select **Submit** to save the ACL.

## Verification

1. Impersonate the user \(for example, `Microsoft Copilot`\).
2. Access the target table \(for example, `sys_dictionary`\) and confirm that rows are visible.

If the user can view the rows, but the field values aren't visible, you need to [grant field-level access](#grant-field-level-access).

## Grant field-level access

If the user can view rows but not field values, configure field-level access.

Warning

Creating a field-level read ACL named `<table>.*` can **remove field read access for other users** on any table that doesn't already have a field-level read ACL. ServiceNow grants a field read when an ACL matches, or when no field ACL exists at all. There's no default `*.*` read ACL to fall through to, so once `<table>.*` exists, it's the only match. Because it requires the connector role, every user **without** that role loses field read access on that table \(record and row access is unchanged, because table and field ACLs are combined\). This is standard ServiceNow behavior, not a bug. Create field-level ACLs only on tables where you verified the service account can see rows but not field values, and prefer the least-privilege per-field approach for shared, platform-wide tables such as `sys_user`, `sys_user_group`, `sys_dictionary`, `sys_properties`, and `core_company`.

To grant read access to **all** fields on a table \(simplest, but restricts every field for users without the role\):

1. Go to **System Security** > **Access Control \(ACL\)**.
2. Select **New** to create a new ACL record.
3. Fill in these fields:

   - **Type**: Select **record**.
   - **Operation**: Choose the `read` operation.
   - **Name**: Enter the table name \(for example, `sys_dictionary`\) and use `*` in the field name to apply to all fields.

4. In the **Roles** section, add the previously created role \(`Copilot Connector Account`\).
5. Select **Submit** to save the ACL.

To grant read access to **only specific fields** \(recommended least-privilege approach, especially for shared, platform-wide tables\):

1. Follow the same steps, but in **Name**, select the specific field instead of `*` \(for example, `sys_properties` with the `value` field\). Create one ACL per field the connector needs.
2. This limits the restriction to only those fields, so other users keep read access to the rest of the table.

Note

If you select **Admin overrides** on the ACL \(the background setup script sets this\), admins keep access and **can't reproduce** the restriction under their own accounts. Verify the effect as an affected non-admin user who doesn't have the connector role. Don't rely on the service account for this check. It has the connector role, so it keeps access and would report success even if other users lost it.

## Final verification

To verify access to the table:

1. Impersonate the user \(for example, `Microsoft Copilot`\).
2. Confirm that you can see both rows and field values within the target table.

You successfully granted table access to a service account in ServiceNow.

## Verify service account permissions

Use the **Copilot Connector Checker Tool** to confirm that all required permissions for ServiceNow Knowledge Base \(KB\) tables are configured correctly:

1. Open the [Copilot Connector Checker Tool](https://testconnectivity.microsoft.com/tests/CopilotServiceNowGraphConnectors/input).
2. Choose the authentication type in the **Authentication Type** field: Basic or OAuth \(recommended\).
3. Complete the fields and select **Perform Test**.
4. The tool automatically validates connectivity, verifies credentials, checks table-level permissions, provides a summary of results, and recommends next steps as needed.

If you have feedback about the tool, select the **Feedback** link at the bottom of the page.
