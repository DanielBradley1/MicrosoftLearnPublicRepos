<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/servicenow-knowledge-setup-scripts -->
<!-- Sitemap-Last-Modified: 2026-08-13 -->

# Set up ServiceNow Knowledge connector prerequisites by using background scripts

You can run background scripts that automate the configuration steps for the [ServiceNow Knowledge Microsoft 365 Copilot connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/servicenow-knowledge-overview). These scripts perform the same configuration as the manual steps described in [Set up the ServiceNow service](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/servicenow-knowledge-admin-setup), [Grant table access](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/granting-table-access-servicenow-knowledge), and [Federated Auth](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/servicenow-knowledge-deployment#federated-auth-federated-identity-credentials). They don't introduce any extra permissions, plugins, or external connections.

The scripts are hosted in the [ServiceNow Knowledge connector setup scripts GitHub repo](https://github.com/microsoft/copilot-servicenow-connector-setup-scripts).

## Prerequisites

The scripts require the following prerequisites:

- ServiceNow admin account with the `security_admin` role elevated.
- Access to **System Definition > Scripts - Background** in your ServiceNow instance.

## Scripts overview

The following table lists and describes the scripts.

| Script | What it does | Equivalent manual steps |
| --- | --- | --- |
| [federated\_auth\_setup.js](https://github.com/microsoft/copilot-servicenow-connector-setup-scripts/blob/main/federated_auth_setup.js) | Configures Federated Auth \(OIDC\): the provider configuration, Application Registry entity, `useraccount` auth scope, and machine integration user. For Federated Auth deployments only. | [Federated Auth](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/servicenow-knowledge-deployment#federated-auth-federated-identity-credentials) |
| [row\_level\_acl\_setup.js](https://github.com/microsoft/copilot-servicenow-connector-setup-scripts/blob/main/row_level_acl_setup.js) | Creates service account, custom role, and row-level READ ACLs for all required tables | [Create service account and set up permissions](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/servicenow-knowledge-admin-setup#create-service-account-and-set-up-permissions-to-index-items) and [Grant table access](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/granting-table-access-servicenow-knowledge) |
| [field\_level\_acl\_setup.js](https://github.com/microsoft/copilot-servicenow-connector-setup-scripts/blob/main/field_level_acl_setup.js) | Creates field-level READ ACLs \(`table.*`\) for tables where field values are restricted | [Grant field-level access](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/granting-table-access-servicenow-knowledge#grant-field-level-access) |
| [scripted\_rest\_api\_setup.js](https://github.com/microsoft/copilot-servicenow-connector-setup-scripts/blob/main/scripted_rest_api_setup.js) | Creates the Scripted REST API endpoint for the Advanced connector flow | [Set up REST API](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/servicenow-knowledge-admin-setup#set-up-rest-api) |

All scripts are:

- **Idempotent** — Safe to run multiple times. The scripts reuse existing records and don't create duplicates.
- **Non-destructive** — The scripts don't modify, delete, or overwrite any existing records.
- **Self-contained** — No external dependencies or network calls outside your ServiceNow instance.

## Set up federated authentication

If you deploy the connector by using the **Federated Auth \(Federated Identity Credentials\)** authentication option, run the `federated_auth_setup.js` script first. It configures the OpenID Connect \(OIDC\) provider, the Application Registry entity, the `useraccount` auth scope, and the machine integration user that the connector authenticates as. For other authentication methods, such as Basic auth or OAuth 2.0, skip this section.

1. Elevate your role to `security_admin` in ServiceNow.
2. Go to **All** > **System Definition** > **Scripts - Background**.
3. Copy the script from [federated\_auth\_setup.js](https://github.com/microsoft/copilot-servicenow-connector-setup-scripts/blob/main/federated_auth_setup.js) and paste it into the script editor.

   Tip

   Set the `SP_OBJECT_ID` \(service principal object ID\) and `TENANT_ID` \(Microsoft Entra tenant ID\) variables in the **CONFIGURATION** section before you run the script. To find these values, see [Federated Auth](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/servicenow-knowledge-deployment#federated-auth-federated-identity-credentials).
4. Select **Run script**.
5. Review the output summary to confirm all steps completed successfully.

When you run the `row_level_acl_setup.js` script in the next step, set its `USER_ID` to the same service principal object ID so that the read role and ACLs are assigned to the integration user that the connector maps to.

## Step 1: Create service account and grant row-level access

The `row_level_acl_setup.js` script creates a service account user, a custom role, assigns the role to the user, and creates row-level READ ACLs for all tables required by the connector.

1. Elevate your role to `security_admin` in ServiceNow.
2. Go to **All > System Definition > Scripts - Background**.
3. Copy the script from [row\_level\_acl\_setup.js](https://github.com/microsoft/copilot-servicenow-connector-setup-scripts/blob/main/row_level_acl_setup.js) and paste it into the script editor.

   Tip

   Review the **CONFIGURATION** section at the top of the script before running. You can change the role name, user ID, and user name to match your organization's naming conventions.
4. Select **Run script**.
5. Review the output summary to confirm all steps completed successfully.

**What the script doesn't do:**

- It doesn't grant field-level access. If the service account can view rows but field values aren't visible, you need to grant field-level access separately. See [Step 3](#step-3-grant-field-level-access-if-needed).
- It doesn't set the service account password. You must set the password manually after running the script.

## Step 2: Verify row-level access

After running the row-level script, verify that the service account can access the required tables.

1. Set a strong, unique password for the service account that complies with your organization's password policy.
2. Use a REST client \(for example, curl or Postman\) to query a table as the service account:

   ```http
   GET https://<instance>.service-now.com/api/now/table/kb_knowledge?sysparm_limit=1
   ```


   Authenticate with the service account credentials \(Basic Auth\).

3. Confirm that rows are returned in the response.

Note

On Zurich and later releases, the script marks the service account as a machine identity \(`identity_type = machine`\), which automatically enables "Web service access only". Machine identity accounts can't be impersonated through the ServiceNow UI. Use the REST API to verify access instead.

If rows are returned with field values populated, skip to [Step 4](#step-4-set-up-rest-api-for-advanced-flow). If rows are returned but field values are empty, continue to Step 3.

## Step 3: Grant field-level access \(if needed\)

If the service account can view rows but field values appear empty, run the `field_level_acl_setup.js` script. This script creates a field-level READ ACL \(`table.*`\) for each configured table and links it to the custom role created in Step 1.

1. Elevate your role to `security_admin` in ServiceNow.
2. Go to **All > System Definition > Scripts - Background**.
3. Copy the script from [field\_level\_acl\_setup.js](https://github.com/microsoft/copilot-servicenow-connector-setup-scripts/blob/main/field_level_acl_setup.js) and paste it into the script editor.

   Tip

   If your role name differs from the default \(`copilot_connector`\), update the `TARGET_ROLE_NAME` variable at the top of the script before running it. You can also add or remove tables from the `TABLES` list based on which tables have restricted field values on your instance.
4. Select **Run script**.
5. Review the output summary to confirm all steps completed successfully.

**How to verify:**

1. Use a REST client to query a table as the service account \(same approach as Step 2\).
2. Confirm that both rows **and** field values are now returned in the response.

## Step 4: Set up REST API for advanced flow

If your ServiceNow instance uses advanced scripts in user criteria \(rather than simple user or group-based criteria\), select the **Advanced** flow when you configure the connector in the Microsoft 365 admin center. Run the `scripted_rest_api_setup.js` script to create the Scripted REST API endpoint that the connector calls to resolve user criteria at query time.

To determine whether your instance uses advanced user criteria, see [Check for advanced scripts and hierarchical permissions](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/servicenow-knowledge-admin-setup#check-for-advanced-scripts-and-hierarchical-permissions-in-servicenow).

1. Elevate your role to `security_admin` in ServiceNow.
2. Go to **All > System Definition > Scripts - Background**.
3. Copy the script from [scripted\_rest\_api\_setup.js](https://github.com/microsoft/copilot-servicenow-connector-setup-scripts/blob/main/scripted_rest_api_setup.js) and paste it into the script editor.

   Tip

   By default, the scripts use the `copilot_connector` role for the crawling service account. If your service account uses a different custom role, update the `ROLE_NAME` variable at the top of the script before you run it. For example: `var ROLE_NAME = 'copilot_connector';`.
4. Choose **Run script** and review the output summary. A successful run ends with:

   ```
   All steps completed successfully. No manual actions needed.
   ```


   If any step can't be completed automatically \(for example, on older ServiceNow versions\), the output lists specific manual follow-ups.

**How to verify:**

1. Go to **Scripted REST APIs** > **Microsoft Copilot**. Under **Security**, confirm **Default ACLs** shows **Microsoft Copilot, Scripted REST External Default**.
2. Open the **GetAllUserCriteria** resource. Under **Security**, confirm **Requires authentication** and **Requires ACL authorization** are checked, and **ACLs** shows **Microsoft Copilot, Scripted REST External Default**.
3. Note the **Resource path** \(for example, `/api/<namespace>/microsoft_copilot/user_criteria`\). The Microsoft 365 admin enters the `<namespace>` value when they [deploy the ServiceNow Knowledge connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/servicenow-knowledge-deployment).

## Configuration options

Each script includes a clearly marked **CONFIGURATION** section at the top where you can customize:

- **Role name** — Default: `copilot_connector`
- **Service account user ID** — Default: `microsoft.copilot`
- **Table lists** — Add or remove tables based on your instance requirements

## Verify service account permissions

After you run the scripts, use the **Copilot Connector Checker Tool** to confirm that all required permissions are configured correctly:

1. Open the [Copilot Connector Checker Tool](https://testconnectivity.microsoft.com/tests/CopilotServiceNowGraphConnectors/input).
2. Choose the authentication type in the **Authentication Type** field: Basic or OAuth \(recommended\).
3. Complete the fields and choose **Perform Test**.
4. The tool automatically validates connectivity, verifies credentials, checks table-level permissions, provides a summary of results, and recommends next steps as needed.

## Related content

- [Set up the ServiceNow service for connector ingestion](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/servicenow-knowledge-admin-setup)
- [Grant table access to a service account in ServiceNow](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/granting-table-access-servicenow-knowledge)
- [Deploy the ServiceNow Knowledge connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/servicenow-knowledge-deployment)
- [Setup scripts GitHub repo](https://github.com/microsoft/copilot-servicenow-connector-setup-scripts)
