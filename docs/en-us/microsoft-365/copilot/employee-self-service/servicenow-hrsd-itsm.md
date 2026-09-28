<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/servicenow-hrsd-itsm -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# Integrate ServiceNow HRSD and ITSM with your Employee Self-Service deployment

Important

You need to complete the steps to deploy the Employee Self-Service agent before you can configure this supplemental extension pack.

The Employee Self-Service agent is built on Copilot and uses AI to provide relevant information to employees and take actions on their HR data. If your organization uses a human resource management system, the Employee Self-Service agent requires access to that system to function most effectively.

## Functional synopsis

The Employee Self-Service agent acts as a front-end for consuming information from ServiceNow HRSD and ITSM using the Power Platform connector. The following items are the capabilities enabled for this integration:

- Create an HR case
- Update an HR case
- Get case details
- Get case updates
- Get user cases
- Get ticket status
- Get ticket details
- Get ticket list
- Create ticket
- Update ticket

## Technical synopsis

[![Diagram the high-level components comprising overall solution for the Employee Self-Service agent and ServiceNow HRSD integration.](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/agent-service-now-integration.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/agent-service-now-integration.png#lightbox)

This diagram outlines the high-level components comprising overall solution for the Employee Self-Service agent and ServiceNow HRSD integration. There are different activities to be performed as a part of initial deployment and for an ongoing operation. As the solution involves multiple technologies, it's better to spend some time initially in understanding the various components. When you're ready, you can bring in the right stakeholders to set up an environment to deploy and test the Employee Self-Service agent.

## Known issues and limitations

These steps are the known issues and limitations of the Power Platform connector for ServiceNow:

- When using the Create Record action, you can't specify the full record description. The field value is ignored due to ServiceNow REST API limitations.
- The Get Records action might return an "Invalid Table" or other error in Power Apps. For Power Apps implementations the suggested workaround is to use the Get Records action in Power Automate and pass the data back to Power Apps.

For detailed documentation about the connector, see [ServiceNow - Connectors](https://learn.microsoft.com/en-us/connectors/service-now/#known-issues-and-limitations).

## Prerequisites

- Have a ServiceNow HRSD/ITSM instance
- Have a Microsoft 365 tenant
- Install the Employee Self-Service agent
- Install the HRMS plugin

Refer to the Employee Self-Service agent [deployment guide](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/deploy-overview-alm) for installation of the agent and subscription requirements required for the Employee Self-Service agent.

### Deployment role requirements

| Roles/Persona | Description | Activities performed | Configuration Areas |
| --- | --- | --- | --- |
| **ServiceNow Administrator** | A user who can perform administrative tasks | Create a service account and assign a role to provide read access to specific table records | ServiceNow |
| **ServiceNow Security Administrator** | A user who can configure OAuth | Create OAuth Application Registry - *if using OAuth for ServiceNow connector* | ServiceNow |
| **Application Developer** \(*minimum privileged role*\) | A user who can register an application | Create an App registration - *if using Microsoft Entra OAuth for ServiceNow connector* | Microsoft 365 admin center |
| **Environment Maker** | A user who can customize Employee Self-Service agent | Configure and customize the Employee Self-Service agent | Microsoft Copilot Studio |

## ServiceNow configuration

This section outlines the tasks an administrator needs to configure in ServiceNow for Employee Self-Service.

Important

For employee-facing HR and IT scenarios in the Employee Self-Service agent, use **Microsoft Entra ID User sign in** so calls run in each signed-in user's context.

Don't use Basic authentication, certificate-based app-token authentication, or other service-token paths for customer-facing Employee Self-Service deployments. These methods can break delegated user-context behavior in BizChat and can trigger impractical user prompts.

For more information, see [Securely integrate with external systems](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/securely-integrating-with-external-systems).

Note

For all security related tasks in ServiceNow, the logged in user with `admin` or `security_admin` role must elevate their access using "Elevate role" option from the profile menu in the top right of navigation bar.

Tip

Without elevating access, the new security objects can't be created. If **New** button in the top right of configuration pane is missing, then the role isn't elevated to "`security_admin`".

### Microsoft Entra ID user sign-in configuration

This authentication uses delegated user tokens. The user signs in through Microsoft Entra ID and ServiceNow receives calls in that signed-in user's context.

Important

ServiceNow allows only one OIDC provider configuration per tenant because it enforces uniqueness on the **OIDC Metadata URL**. If you also configure the Microsoft Graph Connector for ServiceNow on the same ServiceNow instance using OIDC, both connectors can't share or duplicate the same OIDC configuration. Review [Coexistence with the Microsoft Graph Connector for ServiceNow](#coexistence-with-the-microsoft-graph-connector-for-servicenow) before you start.

#### Task 1: Register an application in Microsoft Entra ID for OIDC integration with ServiceNow

[Learn how to register an app in Microsoft Entra ID.](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app)

1. Sign into the Microsoft Entra admin center as a Global Administrator or Cloud App Administrator.
2. Go to **Applications** then **App registrations**.
3. Select **New registration.**
4. In the new registration form, fill in the following fields:

   - **Name:** Any name that represents the purpose of app registration
   - **Redirect URL:** Not needed

5. Choose **Register** to complete the creation of the new app registration.
6. Select **Token configuration** then **Add optional claim** for adding claims setting.
7. Select **Token type** as **Access** and choose the following claims:

   - *Aud* - for audience validation
   - *Email* - addressable email for user
   - *UPN* - an identifier for the user

8. Select **Add** to complete adding the claims.
9. If it's the first time OpenId Connect being setup using claims like email, UPN, there's a confirmation screen to turn on the Microsoft Graph permissions. If you see the confirmation, check the box, and then select **Add**.

This flow completes the Microsoft Entra piece of configuration.

#### Task 2: Register OIDC provider in ServiceNow

1. Sign in to the ServiceNow instance that needs to be integrated with the Employee Self-Service agent.
2. Elevate access permissions using **Elevate role**. Refer to the section **Error! Reference source not found.** - only the first part and not the tasks.
3. Select **All** in the top navigation bar.
4. Search for "OAuth" in the search box within dropdown navigation menu.
5. Select **System OAuth à Application Registry** from the search results \(if you don't see this option, you don't have sufficient privileges\).
6. Select **New** in the configuration section pane.
7. Select **Configure an OIDC provider to verify ID tokens**.
8. Fill in the following information for the new application registry:
   | Configuration | Description |
   | --- | --- |
   | Name | a meaningful name to identify that this OIDC provider was created for the Employee Self-Service agent |
   | Client ID | The client ID of Microsoft Entra Application created in Task 1 above |
   | Client secret | This value isn't used; can be any value |
   | Scope Restriction | Broadly scoped |
   | OAuth OIDC provider configuration | Add a new OIDC provider configuration by selecting the search icon and choosing **New** in the search popup. Fill in the fields as follows:  <br>**OIDC Provider:** A name that represents the Microsoft Entra tenant from task 1 above.  <br>**OIDC Metadata URL:** `login.microsoftonline.com/<tenant ID>/.well-known/openid-configuration`  <br>Replace < tenant ID > with the Microsoft Entra tenant ID from task 1 above.  <br>**OIDC Configuration Cache Life Span:** 120  <br>**Application:** Global  <br>**User Claim:** oid  <br>**User Field:** User ID  <br>**Enable JTI claim verification:** disabled  <br>Select **Submit** and update the OIDC Entity form. |

After you complete Task 1 and Task 2, add the ServiceNow connector application to the permission scope with Client ID = `c26b24aa-7874-4e06-ad55-7d06b1f79b63`.

Update the **User Claim** in Task 2 to UPN, or to any other claim from the token that identifies the user in ServiceNow. The **User Field** must match the ServiceNow user table field that contains that value. If your ServiceNow user ID isn't an email or UPN \(for example, a salary ID or account name\), see [Match users when the ServiceNow user ID isn't an email or UPN](#match-users-when-the-servicenow-user-id-isnt-an-email-or-upn).

### Match users when the ServiceNow user ID isn't an email or UPN

Some organizations identify users in ServiceNow by a value that isn't an email address or Microsoft Entra user principal name \(UPN\)—for example, a payroll or salary ID such as `M043794`. The default guidance assumes the Microsoft Entra UPN or email matches the ServiceNow user ID, so user resolution fails when the identity key is different. Use the following approach to authenticate these users with the **Microsoft Entra ID OAuth User sign in** method.

#### How user matching works

When a user signs in, Microsoft Entra issues a token that contains claims about the user. The ServiceNow OIDC provider configuration maps one token claim \(the **User Claim**\) to a field on the ServiceNow user record \(the **User Field**\). ServiceNow resolves the signed-in user by matching the value of the **User Claim** against the value stored in the **User Field**. To support a non-email identity key, you need a token claim that carries the same value that ServiceNow stores for the user.

#### Configure Microsoft Entra to emit the identity key

The identity key must exist as an attribute on the user's Microsoft Entra object and then be emitted as a token claim on the application that represents ServiceNow. Both are standard Microsoft Entra tasks. Follow the Microsoft Entra documentation rather than reproducing the steps here:

- **Populate the attribute** on each user through HR-driven provisioning, directory synchronization, or directly on the user object. See [Plan cloud HR application to Microsoft Entra user provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/plan-cloud-hr-provision) and [Microsoft Entra Connect Sync: Attributes synchronized](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/reference-connect-sync-attributes-synchronized).
- **Emit the attribute as a claim** on the ServiceNow application, then note the claim name to use in ServiceNow. See [Customize claims issued in the JSON web token \(JWT\) for enterprise applications](https://learn.microsoft.com/en-us/entra/identity-platform/jwt-claims-customization).

The directory attribute and claim names that are available depend on your tenant configuration. Confirm the attribute is populated for every user who needs ServiceNow access. Users with an empty attribute can't be matched and fail to authenticate.

Important

In the claims mapping configuration, Microsoft Entra sets the claim format to email by default. Because the identity key isn't an email address, change this format setting so that it isn't email format, and choose a format that fits the attribute value you use as the identifier. This setting is easy to miss in the Microsoft Entra admin center. If the format stays set to email, Microsoft Entra doesn't match the non-email identifier, and sign-in fails.

Note

Emitting a customized claim might require a custom signing key or the `acceptMappedClaims` property on the application; otherwise, Microsoft Entra returns an error. For single-tenant apps, you can set `acceptMappedClaims` to `true` in the application manifest. For details, see [Customize claims issued in the JSON web token \(JWT\) for enterprise applications](https://learn.microsoft.com/en-us/entra/identity-platform/jwt-claims-customization).

#### Set the Employee Self-Service OIDC mapping in ServiceNow

Set the following fields in the OIDC provider configuration you created in [Task 2: Register OIDC provider in ServiceNow](#task-2-register-oidc-provider-in-servicenow) so ServiceNow matches users on the identity key instead of email or UPN:

| OIDC configuration field | Value for a non-email identity key |
| --- | --- |
| **User Claim** | The custom claim emitted from Microsoft Entra that carries the identity key \(for example, `salaryid`\), rather than `upn` or `email`. |
| **User Field** | The ServiceNow `sys_user` field that stores the same identity key, for example, the field that holds the employee or account ID. |

Select **Submit** and update the OIDC Entity form.

#### Validate the configuration

After you complete the setup, sign in as a test user and confirm ServiceNow resolves the correct user. A mismatch—an empty claim, a claim value that doesn't match the **User Field**, or a misnamed claim—causes authentication to fail silently rather than return an explicit error. To troubleshoot, inspect the token claims issued by Microsoft Entra and confirm the claim value exactly matches the value stored in the ServiceNow **User Field**.

### Coexistence with the Microsoft Graph Connector for ServiceNow

Some customers can't configure both the Employee Self-Service ServiceNow Power Platform \(PP\) connector and the ServiceNow Microsoft Graph Connector \(GC\) in the same ServiceNow instance. ServiceNow supports only one OIDC configuration per tenant, while the two connectors require different authentication flows and token-claim mappings.

Token expectation differences \(why a single OIDC setup can't satisfy both connectors\):

- **PP connector:** delegated \(user\) tokens; user-centric claims \(such as `oid`\); uses `upn` mapped to the ServiceNow **Email** field.
- **GC connector:** app-only tokens; relies on the `sub` \(or `oid`\) claim mapped to the ServiceNow **User ID** field.

For coexistence guidance and latest options, use the [ServiceNow Knowledge Microsoft Copilot connector documentation](https://learn.microsoft.com/en-us/microsoftsearch/servicenow-knowledge-connector). Keep the Employee Self-Service ServiceNow Power Platform connector on Microsoft Entra ID user sign-in.

### Share connection parameters

The agent maker configures ServiceNow connections, which need to be shared with all users so that the users aren't prompted for authentication the first time the agent's used with a ServiceNow connection.

Follow the steps in the [Create and manage connections](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-connections#share-connection-parameters-for-on-behalf-of-obo-authentication) article to share connection parameters for On-Behalf-Of \(OBO\) authentication.

### Connector preparation

With improvements in the ServiceNow integration, the connector objects should be cleaned up before reinstallation or update to the ServiceNow packages. This cleanup is needed because of platform changes for both Power Platform and Copilot Studio.

### Install ServiceNow HRSD extension pack

The Employee Self-Service agent is designed to have separate extension packs for third-party external system solutions like ServiceNow. As a result, these extension packs must be installed first before starting any configurations or customizations.

The following steps are required to install and enable the ServiceNow HRSD extension pack:

1. **Entitlement**:

   Work with your Employee Self-Service agent private preview product managers for the entitlement process. Once the entitlement process is complete for your tenant, the ServiceNow HRSD extension pack shows up under "Customize" section of the Employee Self-Service agent.

   Note

   "Entitlement" process is a preview workaround until the extension pack installation is streamlined in Microsoft Copilot Studio.
2. **Install the extension**:

   1. Open the Employee Self-Service agent in Copilot Studio.
   2. Navigate to **Settings**.
   3. Select **Customize** from the left navigation under **Settings**.
   4. Select **Employee Self-Service Agent in Microsoft Copilot - ServiceNow HR Service Delivery** and select **Install**.
   5. When prompted, update the connections as described by selecting " ..." or **sign in** buttons on the right hand side for ServiceNow connection.
   6. Use the following parameters to complete the configuration for **Microsoft Entra ID User Login**:
      | Feature | Description |
      | --- | --- |
      | **Authentication Type** | Microsoft Entra ID user login |
      | **Instance Name** | The instance name used to identify the ServiceNow Site URL  <br>For example:  <br>**contoso** - *don't use the full url or domain name, like contoso.service-now.com* |
      | **Resource URI** | The client ID of the Entra organization created in Task 1 of [Microsoft Entra ID user sign-in configuration](#microsoft-entra-id-user-sign-in-configuration) |
   7. ServiceNow asks for sign-in again. Use the same account for ServiceNow configuration as you supplied in the previous steps.
   8. Confirm the consent by selecting **Allow**.
   9. The **Microsoft Dataverse** connection is the user account that should be automatically signed in, if not, select **Sign in**.

### Install ServiceNow ITSM extension pack

The Employee Self-Service agent is designed to have separate extension packs for each third party external system solution like ServiceNow, and so on. As a result, these extension packs must be installed before starting any configurations or customizations.

These steps are required to install and enable the ServiceNow HRSD extension pack:

1. **Entitlement**:

   Work with your Employee Self-Service agent private preview product managers for the entitlement process. Once the entitlement process is complete for your tenant, the ServiceNow HRSD extension pack shows up under "Customize" section of the Employee Self-Service agent.

   Note

   "Entitlement" process is a preview workaround until the extension pack installation is streamlined in Microsoft Copilot Studio.
2. **Install the extension**:

   1. Open the Employee Self-Service agent in Copilot Studio.
   2. Navigate to **Settings**.
   3. Select **Customize** from the left navigation under **Settings**.
   4. Select **Employee Self-Service Agent in Microsoft Copilot - ServiceNow IT Service Management** and select **Install**.
   5. When prompted, update the connections as described by selecting " ..." or **sign in** buttons on the right hand side for ServiceNow connection.
   6. Use the following parameters to complete the configuration for **Microsoft Entra ID User Login**:
      | Feature | Description |
      | --- | --- |
      | **Authentication Type** | Microsoft Entra ID user login |
      | **Instance Name** | The instance name used to identify the ServiceNow Site URL  <br>For example:  <br>**contoso** - *don't use the full url or domain name, like contoso.service-now.com* |
      | **Resource URI** | The client ID of the Entra organization created in Task 1 of [Microsoft Entra ID user sign-in configuration](#microsoft-entra-id-user-sign-in-configuration) |
   7. ServiceNow asks for sign-in again. Use the same account used previously for ServiceNow configuration.
   8. Confirm the consent by selecting **Allow**.

### Set the ServiceNow portal base URL

After you install the ServiceNow HRSD or ServiceNow ITSM extension pack, set the ServiceNow portal base URL for each pack that you installed. The extension packs use this base URL to build the hyperlinks that point back to records in ServiceNow.

If you don't set the base URL, scenarios that return a list of tickets or cases, such as when an employee asks to see all their tickets, can return results without working ServiceNow hyperlinks, or include the links only when the employee explicitly asks for them. Setting the base URL makes sure that ticket and case links resolve to the correct ServiceNow portal.

You set the base URL in a Dataverse environment variable that ships with each extension pack. Environment variable values are preserved when you update the extension packs, so you set the URL once and it persists across future updates.

Each pack has its own environment variable:

| Extension pack | Environment variable display name | Example value |
| --- | --- | --- |
| ServiceNow HRSD | **ServiceNow HRSD Portal Base URI** | `https://contoso.service-now.com/sp` |
| ServiceNow ITSM | **ServiceNow ITSM Portal Base URI** | `https://contoso.service-now.com/esc` |

The value is the portal root: the scheme, host, and portal path. The agent appends the record-specific part of the link. The portal path depends on your ServiceNow portal configuration. Common paths are `/sp` for the Service Portal and `/esc` for the Employee Service Center. Your ServiceNow administrator or maker knows the correct portal URL. In the examples, `contoso` is the ServiceNow instance name.

To set the base URL:

1. Go to the [Power Platform admin center](https://admin.powerplatform.microsoft.com).
2. Select the environment where you installed the extension packs.
3. Select **Settings** > **Environment variables**.
4. Open **ServiceNow HRSD Portal Base URI** for the ServiceNow HRSD pack, or **ServiceNow ITSM Portal Base URI** for the ServiceNow ITSM pack.
5. In **Current value**, enter your ServiceNow portal base URL. For example, enter `https://contoso.service-now.com/sp` for HRSD or `https://contoso.service-now.com/esc` for ITSM.
6. Select **Save**.
7. If you installed both extension packs, repeat these steps for the other variable.

Important

If you set the portal base URL in an earlier release by editing the extension pack's template configuration \(the `msdyn_ServiceNowHRSD` or `msdyn_ServiceNowITSM` record\), set the environment variable now. The template configuration value is reset each time you update the extension pack, but the environment variable persists across updates. The template configuration still works as an automatic fallback when the environment variable isn't set, but use the environment variable going forward.

## ServiceNow - HRSD

### HRSD topics

The following topics are available from the ServiceNow HRSD extension pack:

| Topic | Description |
| --- | --- |
| **ServiceNow HRSD Create Case** | Creating an HR case in ServiceNow. |
| **ServiceNow HRSD Get Case Details** | Gets latest created case details. |
| **ServiceNow HRSD Get Case Updates** | Get case update details in text format. Not as detailed as case details. |
| **ServiceNow HRSD Get User Cases** | List of user cases. |
| **ServiceNow HRSD Update Case** | Update an existing HR case in ServiceNow \(comments, state, close code/notes\). |
| **ServiceNow HRSD Add Attachments or Comments To Case** | Add attachments or comments to an existing HR case. |

Note

You may also see additional system topics in Copilot Studio. Other topics trigger these topics \(the agent doesn't trigger the topics directly\) and this action can't be customized. See [HRSD system topics](#hrsd-system-topics) for details.

#### HRSD system topics

The following system topics are installed with the HRSD extension pack. They appear in the Topics list in Copilot Studio but are triggered by other topics, not directly by the agent. These topics can't be customized.

| Topic | Purpose |
| --- | --- |
| **ServiceNow HRSD System Create Case** | Internal processing for case creation. |
| **ServiceNow HRSD System Get Case Details** | Internal processing for retrieving case details. |
| **ServiceNow HRSD System Get Cases List** | Internal processing for retrieving the user's case list. |
| **ServiceNow HRSD System Get Metadata Cached** | Caches HR service metadata from ServiceNow. |
| **ServiceNow HRSD System Common Execution** | Shared orchestration logic for all HRSD scenarios. |
| **ServiceNow HRSD System Case Details Cache Lookup** | Cache lookup for case details. |
| **ServiceNow HRSD System Graceful Exit** | Handles graceful error recovery. |
| **ServiceNow HRSD System Update Case** | Internal processing for case updates. |
| **ServiceNow HRSD System User Permission Check** | Validates the user has permission to update the case. |

### HRSD flows

The following Flows are available from the ServiceNow HRSD extension pack:

| Flow | Purpose |
| --- | --- |
| **ServiceNow HRSD Common Orchestrator** | Main orchestration flow that routes HRSD scenarios to the appropriate ServiceNow API calls. |
| **ServiceNow HRSD Create Case** | Handles the ServiceNow API call for creating a new HR case. |
| **ServiceNow HRSD Get Cases List** | Retrieves the list of HR cases for a user from ServiceNow. |
| **ServiceNow HRSD Get HR Services with COEs for User** | Fetches available HR services and Centers of Excellence for the current user. |

## ServiceNow - ITSM

### ITSM topics

The following topics are available from the ServiceNow ITSM extension pack:

| Topic | Description |
| --- | --- |
| **ServiceNow ITSM Create Ticket** | Takes user input like description, severity, and so on, and sends these details to the corresponding system topic. Successful creation generates an adaptive card with ticket details. |
| **ServiceNow ITSM Get User Tickets** | Fetches the active or closed tickets, and does a quick check on a global variable used as cache for this data. |
| **ServiceNow ITSM Get Ticket Details** | Acquires the *sysID* and passes it down to corresponding system topic. |
| **ServiceNow ITSM Update Ticket** | Gets the *sysID* and other necessary input required for the update call. Also validates if the user has necessary permission to update that ticket. |
| **ServiceNow ITSM Get Ticket Updates** | Retrieves the latest update of IT support tickets for the user. Fetches the list of tickets and then provides the update related to the latest one. |
| **ServiceNow ITSM Employee Handoff Scenarios** | Handles handoff to a live agent when needed. |

Note

You may also see additional system topics in Copilot Studio. Other topics trigger these topics \(the agent doesn't trigger the topics directly\) and this action can't be customized. See [ITSM system topics](#itsm-system-topics) for details.

#### ITSM system topics

The following system topics are installed with the ITSM extension pack. They appear in the Topics list in Copilot Studio but are triggered by other topics, not directly by the agent. These topics can't be customized.

| Topic | Purpose |
| --- | --- |
| **ServiceNow ITSM System Create Ticket** | Internal processing for ticket creation. |
| **ServiceNow ITSM System Get Ticket Details** | Internal processing for retrieving ticket details. |
| **ServiceNow ITSM System Get Tickets List** | Internal processing for retrieving the user's ticket list. |
| **ServiceNow ITSM System Update Ticket** | Internal processing for ticket updates. |
| **ServiceNow ITSM System Common Execution** | Shared orchestration logic for all ITSM scenarios. |
| **ServiceNow ITSM System User Permission Check** | Validates the user has permission to update a ticket. |

### ITSM flows

The following flows are available from the ServiceNow ITSM extension pack:

| Flow | Purpose |
| --- | --- |
| **ServiceNow ITSM Common Orchestrator** | Main orchestration flow that routes ITSM scenarios to the appropriate ServiceNow API calls. |
| **ServiceNow ITSM Get Tickets List** | Retrieves the list of IT tickets for a user from ServiceNow. |
| **ServiceNow ITSM Request Body Generator** | Constructs the request payload for ServiceNow ITSM API calls. |

### Modify agent starter configurations

For any required modifications to the backend ServiceNow Incident APIs, the starter configurations for each scenario can be adjusted in coordination with updates to the frontend topics.

To access the starter configurations:

1. Navigate to the overview tab within the Employee Self-Service agent and scroll down to the ***Customize*** tab.
2. Select the installed customization titled ***Employee Self Service IT Helpdesk ServiceNow ITSM***.
3. This action redirects you to the installed customization details page, where you can view all the Topics and Flows included in the customization package. Additionally, there's a ***Configuration*** option at the top with a manage button.
4. By selecting the **Manage** button, you're directed to the Dataverse Template Configurations table, which lists all available starter configurations.
5. Select the specific scenario starter configuration. It opens the actual value in the Dynamics 365 webpage in a new tab, which can edit the JSON as needed and save your changes.

### Capabilities for the ServiceNow extension pack

Based on the SNOW connector and public APIs, the Service NOW extension pack includes several capabilities. **The initial version focuses on Incident Management**. Specifically, it offers Create, Read, and Update \(CRU\) functionalities for managing ServiceNow incidents.

#### Get Ticket Status

This function allows users to retrieve the latest status of a ticket using ServiceNow APIs, enabling seamless integration with existing IT workflows. When users access real-time ticket status information, they can efficiently track the progress of reported issues.

#### Get Ticket Details

The Get Ticket Details feature lets users retrieve comprehensive information about a specific ticket within the ServiceNow platform. This functionality provides user details for attributes like the ticket number, short description, full description, and current state. By providing these details, users can gain a complete understanding of the ticket's context and status, allowing more effective communication and issue resolution.

#### Get Ticket List

The Get Ticket List feature lets users retrieve a history of user tickets. This functionality provides essential details about each ticket, like its unique number, a brief description, the status, and the date of the last update.

#### Create Ticket

Provides user the ability to create a ticket for IT helpdesk support. Users can add attachments to the ticket, letting them provide more context for easier resolution.

#### Update Ticket

The Update Ticket feature allows users to modify existing helpdesk tickets by adding comments and attributes. This functionality is crucial for maintaining clear and concise communication between users and support agents, ultimately enhancing the resolution process.

Users can now add attachments to the ticket, letting them provide more context for easier resolution.

### ServiceNow ITSM starter configurations

These JSON configurations are intended for the ServiceNow APIs within the backend. These configurations facilitate the linkage between input and output variables from and to the bot. Each scenario has a corresponding JSON configuration, enabling extension pack users to adjust the parameters utilized in the APIs without altering anything in the backend workflows. The way the backend interacts with bot topics regarding input and output variables is defined within these configurations.

The starter configurations reside within a custom Dataverse table, created through the Employee Self-Service agent base package upon installation in an environment. Extension packs contribute extra rows to this table, each containing a stringified JSON configuration for a specific scenario. These configurations are retrieved at runtime using the Dataverse connectors within Power Automate flows.

### Understanding configurations naming

- **Scenario**: The name of the scenario used as the identifier of the operation. This item is the primary key for the starter configuration and shouldn't be changed.
- **FilterCriteria**: This criterion is used to filter the ServiceNow table by applying the "Operator" on a specific "FieldName". "VariableName" refers to the name of the variable passed from the bot topics containing the actual value. If this variable isn't mandatory, the bot author may choose not to send it.
- **SortCriteria**: Used to sort the list of records from a ServiceNow Table on "FieldName" by "Operator".
- **Limit**: Maximum number of records to return.
- **Offset**: Starting record index for which to begin retrieving records.
- **DisplaySystemReferences**: Flag that indicates the type of data returned, either the actual values from the DB or the display values of the fields.
- **ExcludeReferenceLinks**: Flag that indicates whether to exclude Table API links for reference fields.
- **OutputFieldMapping**: Used to model the ServiceNow Table API output to JSON understood by the bot. Corresponding "FieldName" is mapped to "OutputName".
- **UserParameters \(InputFieldMapping\)**: Values of the fields that need to be passed from the user via the bot to the backend flows. Used when creating and updating.
- **GlobalParameters \(InputFieldMapping\)**: Global values that are consistently passed to the API with each call. Includes essential values such as AssignmentGroup, which remain unchanged in every case.

## References

- [ServiceNow - Connectors](https://learn.microsoft.com/en-us/connectors/service-now/#actions)
- [External ID Token Authentication \(OIDC\) for Rest APIs - Support and Troubleshooting](https://support.servicenow.com/kb?id=kb_article_view&sysparm_article=KB0720547)
- [ServiceNow Catalog Microsoft Copilot connector \| Microsoft Learn](https://learn.microsoft.com/en-us/microsoftsearch/servicenow-catalog-connector#3-authentication-type)

For ServiceNow Knowledge documentation, refer to the following link, which requires ServiceNow logins:

- [Table API](https://www.servicenow.com/docs/bundle/xanadu-api-reference/page/integrate/inbound-rest/concept/c_TableAPI.html)
