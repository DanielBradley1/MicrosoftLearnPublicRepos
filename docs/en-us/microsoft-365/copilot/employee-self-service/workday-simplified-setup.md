<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/workday-simplified-setup -->
<!-- Sitemap-Last-Modified: 2026-10-06 -->

# Set up the simplified Workday integration for Employee Self-Service

Important

This article covers a **new** Workday integration for the Employee Self-Service agent.

- You need to complete the steps to deploy the Employee Self-Service agent before you can configure this supplemental extension pack.
- If your tenant already uses the integration system user \(ISU\) and Reports as a Service \(RaaS\) configuration and you want to move to the simplified setup, see [Upgrade an existing Workday integration to the simplified setup](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/workday-upgrade-to-simplified).
- If you aren't ready to move to the simplified setup, your existing configuration continues to work. See [Integrate Workday with your Employee Self-Service deployment](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/workday) for the legacy reference.

The Employee Self-Service agent is built on Copilot and uses AI to provide relevant information to employees and take actions on their HR data.

If your organization uses a human resource management system, the Employee Self-Service agent requires access to that system to function most effectively. This article guides you through the simplified Workday integration, in which the Employee Self-Service agent connects to Workday using the signed-in user's identity through a single OAuth connection.

## Technical synopsis

[![Infographic that describes the components of the Employee Self-Service agent and the simplified Workday integration.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/ess/workday-simplified-1.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/ess/workday-simplified-1.png#lightbox)

This diagram outlines the high-level components that make up the overall solution for the Employee Self-Service agent and the simplified Workday integration. The Employee Self-Service agent connects to Workday using a single OAuth connection. Workday REST and SOAP endpoints are accessed through that same connection, and the signed-in user's identity is used at runtime for every Workday API call.

Important

SOAP calls don't require integration system users \(ISUs\) in the simplified Employee Self-Service Workday integration. Both SOAP and REST calls run as the signed-in user through the same OAuth connection. This guidance applies to the simplified Employee Self-Service integration, not to every Workday integration.

The simplified integration uses the APIs for different purposes:

- **REST:** The `/workers/me` call retrieves user context once per session. The worker ID is cached and reused for the rest of the session, replacing the legacy ISU-based user-context RaaS report.
- **SOAP:** Existing employee scenarios, such as reading employee data, updating a phone number or email address, and requesting time off, continue to use SOAP with the signed-in user's identity. Their Workday audit trail is unchanged.

The simplified setup doesn't move all Workday scenarios to REST. It removes the ISU and user-context RaaS dependencies while retaining SOAP for existing scenarios.

Different roles need to perform various activities for both initial deployment and ongoing operation. As this solution involves multiple platforms, we recommend that you read through the documentation and understand the process before beginning integration. A first step is to identify stakeholders to set up an environment to [deploy the Employee Self-Service agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/deploy-overview-alm).

Note

Workday integration is currently configured to retrieve only Employee details and doesn't work for external staff or non-Employees.

## Prerequisites

### Subscription prerequisites

- A Microsoft Entra user account with active subscription
- Workday single sign-on \(SSO\) enabled subscription

You also need to meet the [prerequisites to deploy the Employee Self-Service agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/prerequisites).

### Supported authentication

The simplified Employee Self-Service Workday integration requires Microsoft Entra single sign-on \(SSO\) with OAuth. Use **Microsoft Entra ID Integrated** for the Workday connection. The supported identity provider \(IdP\) configurations are:

- **Microsoft Entra ID directly:** Workday uses Microsoft Entra ID for SSO.
- **A third-party IdP federated with Microsoft Entra ID:** Microsoft Entra federates to the third-party IdP, which is configured as Workday's IdP. Workday resolves the user from the SAML claims it receives.

Important

Basic authentication isn't supported for the simplified Employee Self-Service Workday integration, including testing and proof-of-concept \(POC\) deployments. A third-party Workday IdP that isn't federated with Microsoft Entra ID isn't supported either. Other authentication choices exposed by the Power Platform connector don't make them supported alternatives for this integration.

Before you start a POC or production deployment, confirm that the target Workday environment uses one of these supported configurations. For identity matching when Microsoft Entra UPNs don't match Workday login IDs, see [Identity resolution for non-UPN tenants](#step-7-identity-resolution-for-non-upn-tenants).

### Set up Copilot Studio capacity

We recommend that you set up Copilot Studio capacity to monitor capacity usage of the Employee Self-Service agent over time. [Learn more about the deployment process for the Employee Self-Service agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/deploy-overview-alm).

## Deployment role requirements

| Role | Description | Activities performed | Configuration area |
| --- | --- | --- | --- |
| Workday administrator | User who can perform administrative tasks | 1. Create X.509 public key  <br>1. Edit tenant setup - security  <br>1. Manage authentication policies  <br>1. Register API client | Workday |
| Application administrator **or** Cloud application administrator **or** application owner | User who can configure SSO integration with Workday | 1. Add Workday from gallery  <br>1. Configure Microsoft Entra SSO  <br>1. Configure Workday  <br>1. Test SSO | Microsoft Entra  <br>Workday |
| Environment Maker | User who can customize the Employee Self-Service agent | 1. Install and configure Workday extension pack  <br>1. Manage Workday topics  <br>1. Set up user context | Microsoft Copilot Studio |
| InfoSec/IT Infrastructure/Change control board | User committee responsible for security infrastructure changes | Configure IT platform services such as network and firewall rules | Network firewall policies |

## Infrastructure setup for third-party external system solution integration

Most enterprise organizations secure their HR management systems and knowledge sources from external networks, as it's critical to protect sensitive information about employees, organizations, knowledge assets, and more.

When you integrate these enterprise systems into the Employee Self-Service agent, it becomes a more reliable source for providing information to your users. To integrate these systems, you need to make them accessible to the Power Platform environment where the Employee Self-Service agent is hosted.

You need to configure these systems with allowlists for the source IP addresses from which the Employee Self-Service agent is hosted and executed, such as the Power Platform environment. See the following documentation for information on retrieving the list of IP address ranges to configure in the network environment:

- [Learn about overall Power Platform URLs and IP address ranges](https://learn.microsoft.com/en-us/power-platform/admin/online-requirements).
- [Learn about Managed connectors outbound IP addresses](https://learn.microsoft.com/en-us/connectors/common/outbound-ip-addresses#power-platform).

For Workday integration, the Employee Self-Service agent uses the Workday REST and SOAP endpoints through a single OAuth connection. Work with your InfoSec team to allowlist the Employee Self-Service agent to communicate with both endpoints. Most existing SOAP firewall rules cover the REST endpoint; some customers might require a separate review.

If any more data security requirements need to be met for SOAP and REST exchange, work with your security specialists to increase the security for data in transit.

## Set up SSO for Workday with Microsoft Entra

Note

You can ignore this step if SSO is already established for Workday with Microsoft Entra.

Refer to this documentation to set up SSO for Workday with Microsoft Entra: [Microsoft Entra single sign-on \(SSO\) integration with Workday](https://learn.microsoft.com/en-us/entra/identity/saas-apps/workday-tutorial).

### Set up the Workday connector in Microsoft Entra

1. Open [https://portal.azure.com](https://portal.azure.com).
2. Navigate to **App registrations**.
3. Locate the application created for the Workday SSO setup.
4. Note the **Application ID URI** for later.
5. Go to **Manage** > **Expose an API**.
6. Add a scope for `user_impersonation`:

   - Select **+ Add a scope**.
   - **Scope name**: `user_impersonation`
   - **Who can consent**: Admins and users
   - Fill in consent display names and descriptions.

7. Under **Authorized client applications**, add the following Workday connector app ID: `4e4707ca-5f53-46a6-a819-f7765446e6ff`.
8. Ensure that the new client application has the `user_impersonation` scope added in the previous step. Under **API permissions**, add the `openid`, `profile`, and `User.Read` Microsoft Graph permissions:

   - Select **+ Add a permission**.
   - Select **Microsoft Graph**.
   - Choose **Delegated permission**.
   - Select `openid`, `profile`, and `User.Read`.

9. Select **Grant admin consent**.

## Configure Workday for the Employee Self-Service agent

The following configuration tasks need to be done in Workday by a Workday Administrator:

Note

Ensure SSO is already set up using [Configure Workday for Single sign-on with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/saas-apps/workday-tutorial). Also ensure that the **Service Provider ID** \(in **Edit Tenant Setup - Security**\) matches the application identifier for the application principal created \(**Microsoft Entra** > **Enterprise Applications** > Workday SSO application\).

1. [Create the X.509 public key](#task-1-create-the-x509-public-key)
2. [Edit tenant setup - security](#task-2-edit-tenant-setup---security)
3. [Manage authentication policies](#task-3-manage-authentication-policies)
4. [Register API client](#task-4-register-api-client)
5. [Security configuration](#task-5-security-configuration)

### Task 1: Create the X.509 public key

Use the X.509 public key provided by Microsoft Entra to create a new key in Workday.

### Task 2: Edit tenant setup - security

1. Configure your redirection URL.

   ![Screenshot of the page where you configure the redirection URL.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/ess/workday-simplified-2.png)
2. Enable OAuth 2.0 clients and SAML authentication by choosing **Yes** in the **OAuth 2.0 Clients Enabled** and **Enable SAML Authentication** sections.
3. Configure the SAML Identity Provider. Verify the following fields if SSO is already configured for Workday with Microsoft Entra:

| Field | Description |
| --- | --- |
| Identity provider name | Can be any name. |
| Issuer | Enter the unique identifier for your SAML IdP, which must match the Issuer ID in SAML messages that the IdP sends. You can get this identifier from your IdP. For Microsoft Entra, this entry should be "Microsoft Entra Identifier". |
| X.509 Certificate | Select or create the X.509 public certificate to use to verify the signature on SAML sign-in and sign-out requests. You can get this information from your SAML provider. |
| SP initiated | Select to specify SP-initiated SAML authentication. |
| Service Provider ID | Identifies Workday as the service provider in the Issuer element of SAML messages sent to the IdP.  <br>Service Provider ID needs to be unique \(the IdP requires this value to be unique on their end\).  <br>This information needs to match the **Identifier \(Entity ID\)** field on Microsoft Entra.  <br>These formats are examples \(remove the spaces for your own URL\):  <br>http:// www .workday .com/sbx  <br>\*http:// www .workday .com/prod  <br>\*http:// www .workday .com/< tenant name > |
| Sign SP-initiated Request | Set to "No" if your SAML provider isn't using Workday's public key. |
| Do Not Deflate SP-initiated Request | Select this checkbox to ensure that Workday doesn't deflate the message again if the IdP deflates the authentication request message. |
| Always require IdP Authentication | Don't select. |
| IdP SSO Service URL | Enter the URL to which Workday sends SAML authentication requests. You can get this URL from your SAML IdP.  <br>For Microsoft Entra, you can get this URL from the **Login URL** field. |

### Task 3: Manage authentication policies

Edit the authentication policy for the Workday tenant. If there are no authentication policies configured yet, create one first.

1. Run the report **Manage Authentication policies**. Then select the **Edit** button for the policy for the tenant.
2. Scope the authentication policy to the OAuth client identity used by the Employee Self-Service agent. Integration system users aren't used in the simplified setup.
3. Select **SAML** as **Allowed Authentication Type** for the Employee Self-Service users. Other authentication methods needed by unrelated Workday integrations don't replace this requirement.
4. Make sure you have the SAML option enabled for the **All Employees** security group, along with any other required method in your Workday environment.
5. Execute the task **Activate All Pending Authentication Policy Changes** to activate all pending authentication policy changes. This step is required to finalize all authentication policy changes.

### Task 4: Register API client

This task is required to invoke Workday APIs from an external system such as the Employee Self-Service agent.

Sign in to Workday as an administrator who can manage API clients. In the Workday global search, enter **register api client**, and then select **Register API Client** from the results.

[![Screenshot of Workday global search results for api client showing View API Clients, Register API Client, and Maintain API Client Access.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/ess/workday-upgrade-2-search-api-client.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/ess/workday-upgrade-2-search-api-client.png#lightbox)

When configuring **Scope \(Functional Areas\)** on the API client, add the following functional areas required for the simplified Employee Self-Service setup:

- **Core Payroll**
- **Organizations and Roles**
- **Staffing**
- **Time Off and Leave**

These four functional areas are the **minimum scope** required for the out-of-the-box Employee Self-Service experience. If you plan to extend Employee Self-Service with custom topics or flows that use additional Workday domains \(for example, Recruiting, Learning, or Expenses\), add the corresponding functional areas as well.

Set **Include Workday Owned Scope** to **Yes** so that Workday-owned web services \(for example, the REST `/workers/me` endpoint used for user-context lookup\) are included alongside the functional areas you select.

The Client ID and the endpoints autogenerated after the client is created must be shared securely with Microsoft Entra Administrators for Microsoft Entra configuration for the Employee Self-Service agent.

[![Screenshot of the Workday API client Scope \(Functional Areas\) section showing Core Payroll, Organizations and Roles, Staffing, and Time Off and Leave selected, with Include Workday Owned Scope enabled.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/ess/workday-simplified-3.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/ess/workday-simplified-3.png#lightbox)

Note

Confirm the API clients are set up with the required scopes for the operations supported by the Employee Self-Service agent.

### Task 5: Security configuration

Configure domain security permissions in Workday so employees can retrieve the information needed by the Employee Self-Service agent. The agent uses the signed-in user's identity, so grant the required permissions to the security group containing the employees who will use the agent.

Start with **Worker Data: Public Worker Reports**, which provides employee context information. Access to this domain doesn't grant access to all data in the **Core Payroll**, **Organizations and Roles**, **Staffing**, or **Time Off and Leave** functional areas. The API client scopes configured in Task 4 don't replace domain security permissions.

1. Open the **View Domain** task.
2. Enter the domain name: **Worker Data: Public Worker Reports**.
3. Select the magnifying-glass icon next to **Domain Security Policy** to edit the domain security permissions.

   [![Screenshot of the Workday View Domain task for Worker Data: Public Worker Reports, showing the Domain Security Policy field.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/ess/workday-security-config-view-domain.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/ess/workday-security-config-view-domain.png#lightbox)
4. Under **Integration Permissions**, add the appropriate security group and grant **Get** access. Grant access at the **Integration Permissions** level, not at the **Report/Task** level.

Choose the security group for your deployment:

- **Production rollout:** Use **All Employees** when deploying to the entire workforce.

  [![Screenshot of Workday Integration Permissions showing the All Employees security group with Get access.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/ess/workday-security-config-integration-permissions.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/ess/workday-security-config-integration-permissions.png#lightbox)
- **Testing or limited rollout:** Use a security group containing only the employees participating in the deployment. Expand access when you're ready to roll out more broadly.

#### Resolve authorization errors for additional employee data

The domain that governs specific employee data can vary by tenant configuration. For example, a phone number might be governed by **Worker Data: Public Worker Reports** or another domain, such as **Personal Data**, **Staffing**, or **Worker Data: Dependents**.

If an employee receives a "Task not authorized" error for a question such as "What is my phone number?":

1. Ask your Workday administrator to identify the security domain that governs the requested data in your tenant.
2. Follow the same domain-security process to grant the required permissions under **Integration Permissions** to **All Employees**, or to the security group used for testing or limited rollout.
3. Retest the question as an employee in that security group.

Grant only the permissions required for the employee scenarios you intend to support. The example domains aren't a list of permissions that every deployment requires.

Note

The existing tasks for creating `ISU_WQL_COPILOT` and `ISU_Generic_COPILOT` integration system users, `ISSG_WQL_COPILOT` and `ISSG_Generic_COPILOT` security groups, and the `WD_User_Context` RaaS report aren't part of the simplified setup. They're intentionally omitted from this page.

## Install the Workday extension pack for the Employee Self-Service agent

The Employee Self-Service agent is designed to have separate extension packs for each third-party external system solution. You need to install the extension pack before starting any configurations or customizations.

The following steps are required to install and enable the Workday extension pack.

### Step 1: Install the extension

1. Open the Employee Self-Service agent in Copilot Studio.
2. Navigate to **Settings**.
3. Select **Customize** from the left navigation.
4. Select **Workday** and choose **Install**. Existing customers can update an installed package by selecting **Workday** under **Settings** > **Customize** and choosing **Update**. The package update doesn't affect the production agent until you take it.
5. When prompted, update the connections as described by selecting the ellipses \(**...**\) on the right side for each connection.

### Step 2: Set up connection authentication

Select **Microsoft Entra ID Integrated** for the Workday connection. Complete the [supported SSO configuration](#supported-authentication) before you set up this connection. This method uses OAuth in the signed-in user's context, supports automatic connection establishment through SSO, and refreshes tokens seamlessly. Don't select Basic authentication for a simplified Employee Self-Service deployment or POC.

When you install the Workday connector, the first step is to set up connections using the form. Fill out the following fields.

#### Microsoft Entra resource URL \(Application ID URI\)

Microsoft Entra's app registration created for Workday SSO. [Learn how to access app registrations](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app).

1. Select **All applications**.
2. Choose the correct application created for Workday SSO.
3. In the **Overview** section, use the **Application ID URI** under the **Essentials** tab.

#### Workday OAuth token URL and Client ID

Workday API client settings have the OAuth token URL.

1. Sign in to Workday with privileges to **View API Client**.
2. Identify the correct API client entry from the table and open it \(created when setting up SSO in **Edit tenant setup - security** in Workday\).
3. In the **View API Client** page, look for **Token Endpoint**.
4. The value for **Client ID** appears above the Token Endpoint.

#### SOAP base URL

The Workday **Public Web Services** report provides the SOAP base URL. The simplified setup doesn't use Reports as a Service \(RaaS\), so use the following steps to find the SOAP endpoint URL.

1. In the Workday search bar, enter **Public Web Services**, and then open the **Public Web Services** report.

   [![Screenshot of the Workday Public Web Services report with Human Resources \(Public\) in the web service list.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/ess/workday-soap-base-url-1-public-web-services.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/ess/workday-soap-base-url-1-public-web-services.png#lightbox)
2. Locate the web service that you need, such as Human Resources, Staffing, or Recruiting. This example uses **Human Resources \(Public\)**.
3. Select the **Related Actions** \(three-dot\) menu next to the web service, and then select **Web Service** > **View WSDL**.

   [![Screenshot of the Related Actions menu for Human Resources \(Public\) with Web Service then View WSDL selected.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/ess/workday-soap-base-url-2-view-wsdl.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/ess/workday-soap-base-url-2-view-wsdl.png#lightbox)
4. When the WSDL page opens, search for `soapbind:address`.
5. Copy the value of the `location` attribute on the `soapbind:address` element. This value is the SOAP endpoint URL to use for the integration.

   [![Screenshot of the WSDL output showing the soapbind:address element. The location attribute value is redacted.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/ess/workday-soap-base-url-3-soapbind-address.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/ess/workday-soap-base-url-3-soapbind-address.png#lightbox)

The `location` value has the following form:

```text
https://<tenant>/ccx/service/<service_name>/<version>
```

#### Workday REST base URL

The Workday REST base URL is exposed in the same Workday API client **View** page used to retrieve the OAuth token URL and Client ID. Provide the REST base URL in the connection configuration. This field is a new field for the simplified setup.

Copy the **Workday REST API Endpoint** value as Workday displays it—the host and path vary by Workday deployment, so don't reconstruct or template the URL by hand. Then trim the copied value so it ends at `/api`. Remove everything after `/api` \(for example, the tenant suffix or any `/v1` or resource path that Workday appends\). The **REST base URL** field expects the endpoint up to `/api` only; leaving the trailing path in causes the simplified flow to fail silently.

Important

The **REST base URL** field is mandatory for the simplified setup. Without it, the simplified flow fails silently and the agent falls back to the legacy ISU-based Reports as a Service \(RaaS\) path.

Enter this value even if the connection form shows the field as optional.

### Step 3: Configure connections

During the Workday extension pack installation process, you're prompted for the following connection configurations:

| Connection reference name | Connection reference ID | Expected connection user account |
| --- | --- | --- |
| OAuthUser | new\_sharedworkdaysoap\_ff0df | Maker \(signed-in user\) |
| Microsoft Dataverse | msviess\_sharedcommondataserviceforapps\_92b66 | Maker \(signed-in user\) |

Ensure that each connection is explicitly set up with its own account, even though the connection status might turn green after the first connection setup.

### Step 4: Turn on Allow permission to share parameters

In the Workday connection, open the **Connection parameters** tab and turn **Allow permission to share parameters** to **On**. Confirm that all parameter fields \(including **REST base URL**\) are populated, and then select **Save**.

[![Screenshot of the Workday connection Connection parameters tab with Allow permission to share parameters set to On and all parameter values populated.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/ess/workday-upgrade-7-share-parameters.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/ess/workday-upgrade-7-share-parameters.png#lightbox)

Tip

If the parameter fields \(including **REST base URL**\) appear empty when you open the **Connection parameters** tab, the connection might already have **Allow permission to share parameters** set to **On**. A known platform issue prevents the values from rendering in that case. To force them to repopulate, turn the toggle **Off**, select **Save**, turn it back **On**, and then select **Save** again. The parameter fields then show the expected values.

Note

Changing connection parameters can put the Workday connection into a stale state. If the connection isn't in the **Ready** state after you save, reconnect it to restore the connection. This is standard Power Platform behavior when connection settings change.

### Step 5: Confirm the Workday flows are turned on

1. Open the **Workday** solution from the Solutions page.
2. Select **Cloud flows** from the sidebar and verify that both workflows are turned on.
3. If the cloud flows aren't turned on, select the display names to open the cloud flow and select **Turn on** in the toolbar.

### Step 6: Set up the user context topic

Confirm that the user context topic is set to the V2 version. In Microsoft Copilot Studio, go to **Agents** > **ESS HR/IT** > **Topics** and open the **\[Admin\] - User Context - Setup** topic. In the **Topic** node, check the referenced topic:

- If it's already **Workday \[System\] - 1: Set User Context V2**, no change is needed.
- If it isn't, select the existing topic reference, choose **Select a topic**, search for `v2`, and then select **Workday \[System\] - 1: Set User Context V2**. Save the topic.

[![Screenshot of the Admin - User Context - Setup topic in Microsoft Copilot Studio with the Select a topic picker open and the Workday System Set User Context V2 topic highlighted.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/ess/workday-upgrade-8-user-context-v2.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/ess/workday-upgrade-8-user-context-v2.png#lightbox)

For more information about the user context variables the agent uses and how to reference them in your agent, see [Design best practices for the Employee Self-Service agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/design-best-practices).

### Step 7: Identity resolution for non-UPN tenants

Workday uses an identity provider \(IdP\) for sign-in. The simplified setup works when Workday's IdP is either Microsoft Entra ID directly, or a third-party IdP that Microsoft Entra is federated with. See [Supported authentication](#supported-authentication) for the requirements that apply to both configurations.

For tenants where Microsoft Entra UPNs match Workday login IDs, no further action is required. The Microsoft Entra ID Integrated authentication path resolves the signed-in user's identity automatically.

For tenants where Microsoft Entra UPNs don't match Workday login IDs and Workday's IdP is a third-party IdP that Microsoft Entra is federated with, Workday resolves the user's identity from the SAML claims it receives from the third-party IdP. A custom non-UPN runtime mapping topic isn't required for most deployments.

## Customizations for Workday integration

Use **Templates** to complete the customizations required for Workday integration. Templates are XML objects that define connection information and data extraction information. Here, you use Templates to retrieve information from Workday.

### Templates included in the solution

The following Templates and their associated Copilot topics are listed here:

| Workday Template name | Employee Self-Service agent associated topic |
| --- | --- |
| HRWorkdayHCMEmployeeGetBaseCompensation | Workday Get BaseCompensation |
| HRWorkdayHCMEmployeeGetCompanyCode | Workday Get CompanyCode |
| HRWorkdayHCMEmployeeGetCostCenter | Workday Get CostCenter |
| HRWorkdayHCMEmployeeGetServiceAnniversary | Workday Get ServiceAnniversary |
| HRWorkdayHCMEmployeeGetContext | Workday System Get UserContext |
| HRWorkdayHCMEmployeeGetEmploymentInfo  <br>HRWorkdayHCMEmployeeGetReferenceData | Employee Get EmploymentInformation |
| HRWorkdayHCMEmployeeGetEmergencyContactInfo  <br>HRWorkdayHCMEmployeeGetReferenceData | Workday Get EmergencyContact |
| HRWorkdayHCMEmployeeGetNationalIds  <br>HRWorkdayHCMEmployeeGetReferenceData | Workday Get NationalIDs |
| HRWorkdayHCMEmployeeGetPassports  <br>HRWorkdayHCMEmployeeGetReferenceData | Workday Get Passports |
| HRWorkdayHCMEmployeeGetVisas  <br>HRWorkdayHCMEmployeeGetReferenceData | Workday Get Visas |
| HRWorkdayHCMEmployeeGetLanguageInformation  <br>HRWorkdayHCMEmployeeGetReferenceData | Workday Get LanguageInformation |
| HRWorkdayHCMEmployeeGetCertifications  <br>HRWorkdayHCMEmployeeGetReferenceData | Workday Get Certifications |
| HRWorkdayHCMEmployeeGetPersonalEmail  <br>HRWorkdayHCMEmployeeAddPersonalEmail  <br>HRWorkdayHCMEmployeeUpdatePrimaryAndSecondaryEmail | Workday Update Email |
| HRWorkdayHCMEmployeeGetPhoneNumber  <br>HRWorkdayHCMEmployeeAddPhoneNumber  <br>HRWorkdayHCMEmployeeUpdatePhoneNumber  <br>HRWorkdayHCMEmployeeUpdatePrimaryAndSecondaryPhoneNumber  <br>HRWorkdayHCMEmployeeGetReferenceData | Workday Update PhoneNumber |

### Template structure overview

The templates are split into two key components: `scenario` and `requestTemplates`.

```xml
<WorkdayEntityConfigurationTemplate>
    <Scenario name="GetJobTaxonomy">
        <apiRequests>
            <apiRequest>
                <authType>User</authType>
                <endpoint>...
                </endpoint>
                <requestParameters>...
                </requestParameters>
                <responseProperties>...
                </responseProperties>
            </apiRequest>
        </apiRequests>
    </Scenario>
    <RequestTemplates>
        <RequestTemplate name="Template_GetWorkerRequest">...
        </RequestTemplate>
    </RequestTemplates>
</WorkdayEntityConfigurationTemplate>
```

#### Scenario

The `scenario` object is an XML object used to drive specific customer scenarios in the Employee Self-Service agent flows. The `scenario` XML node contains a `name` attribute that describes the scenario from a high-level perspective. Inside the `scenario` object, there are `apiRequests` and labels.

#### apiRequest

The `apiRequest` nodes contain information that conveys to the Workday API flow how to request data.

```xml
<apiRequest>
    <authType>User</authType>
    <endpoint>
        <request>msdyn_HRWorkdayHCMManagerJobTaxonomy_GetWorkerRequest</request>
        <serviceName>Human_Resources</serviceName>
        <version>v41.0</version>
    </endpoint>
    <requestParameters>
        <parameter>
            <name>Include_Roles</name>
            <value>true</value>
        </parameter>
    </requestParameters>
    <responseProperties>
        <property>
            <extractPath>//*[local-name()='Role_Assigner_Reference']/*[local-name()='ID' and @*[local-name()='type']='Organization_Reference_ID']/text()</extractPath>
            <key>OrganizationReferenceID</key>
        </property>
    </responseProperties>
</apiRequest>
```

#### requestTemplates

Request templates are XML objects that define the request body that gets sent to Copilot. These templates often contain replaceable values that are filled as part of the flow. Replaceable values appear in curly brackets `{example_replaceable_value}`.

```xml
<requestTemplates>
    <requestTemplate name="msdyn_HRWorkdayHCMManagerJobTaxonomy_GetWorkerRequest">
        <bsvc:Get_Workers_Request xmlns:bsvc="urn:com.workday/bsvc" bsvc:version="v41.0">
            <bsvc:Request_References bsvc:Skip_Non_Existing_Instances="false" bsvc:Ignore_Invalid_References="true">
                <bsvc:Worker_Reference bsvc:Descriptor="Employee_ID">
                    <bsvc:ID bsvc:type="Employee_ID">{Employee_ID}</bsvc:ID>
                </bsvc:Worker_Reference>
            </bsvc:Request_References>
            <bsvc:Response_Filter>
                <bsvc:As_Of_Effective_Date>{As_Of_Effective_Date}</bsvc:As_Of_Effective_Date>
            </bsvc:Response_Filter>
            <bsvc:Response_Group>
                <bsvc:Include_Roles>true</bsvc:Include_Roles>
            </bsvc:Response_Group>
        </bsvc:Get_Workers_Request>
    </requestTemplate>
</requestTemplates>
```

The following example is a full sample template:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<workdayEntityConfigurationTemplate>
    <scenario name="GetJobTaxonomy">
        <apiRequests>
            <apiRequest>
                <authType>User</authType>
                    <endpoint>
                        <request>Template_GetWorkerRequest</request>
                        <serviceName>Human_Resources</serviceName>
                        <version>v42.0</version>
                    </endpoint>
                    <responseProperties>
                        <property>
                            <extractPath>//*[local-name()="Position_Title"]/text()</extractPath>
                            <key>JobTitle</key>
                        </property>
                        <property>
                            <extractPath>//*[local-name()="Business_Title"]/text()</extractPath>
                            <key>BusinessTitle</key>
                        </property>
                        <property>
                            <extractPath>//*[local-name()="Job_Profile_Name"]/text()</extractPath>
                            <key>JobProfile</key>
                        </property>
                        <property>
                            <extractPath>//*[local-name()='Job_Profile_Summary_Data']/*[local-name()='Job_Family_Reference']/*[local-name()='ID' and @*[local-name()='type']='Job_Family_ID']/text()</extractPath>
                            <key>JobFamilyId</key>
                        </property>
                    </responseProperties>
            </apiRequest>
        </apiRequests>
    </scenario>
<requestTemplates>
    <requestTemplate name="Template_GetWorkerRequest">
        <bsvc:Get_Workers_Request xmlns:bsvc="urn:com.workday/bsvc" bsvc:version="v41.0">
            <bsvc:Request_References bsvc:Skip_Non_Existing_Instances="false" bsvc:Ignore_Invalid_References="true">
                <bsvc:Worker_Reference bsvc:Descriptor="Employee_ID">
                    <bsvc:ID bsvc:type="Employee_ID">{Employee_ID}</bsvc:ID>
                </bsvc:Worker_Reference>
            </bsvc:Request_References>
            <bsvc:Response_Filter>
                <bsvc:As_Of_Effective_Date>{As_Of_Effective_Date}</bsvc:As_Of_Effective_Date>
            </bsvc:Response_Filter>
            <bsvc:Response_Group>
                <bsvc:Include_Employment_Information>true</bsvc:Include_Employment_Information>
            </bsvc:Response_Group>
        </bsvc:Get_Workers_Request>
    </requestTemplate>
</requestTemplates>
</workdayEntityConfigurationTemplate>
```

## Customize Workday reference data

The Workday solution ships with 17 reference data sets, each stored as a template configuration record in Dataverse. These records are seeded from a canonical Workday tenant. If your Workday tenant customized any of these catalogs, bring the matching template configuration in line with your tenant.

Note

Reference data is embedded in the Workday solution as template configurations so that affected topics no longer depend on Workday's admin-only `Get_References` SOAP operation at runtime. If you're taking this release as an upgrade, complete it in the correct order. See [Upgrade the Workday solution for Employee Self-Service](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/workday-upgrade-solution).

### When to customize reference data

Customize reference data when one of the following happens:

- A topic that returns a list \(for example, "show me my passports", "show me my visas", or "show me my education"\) returns an empty result, or returns labels that look wrong for your tenant.
- A Workday write operation returns an `Invalid_Reference_ID` error. This error means the agent sent a Reference ID that your Workday tenant doesn't recognize.
- Your Workday HRIS team confirmed that the tenant uses customized Reference IDs for one or more of the types listed in the following table.

If you see no errors and all values look right, you don't need to customize reference data.

### The 17 reference data records

Each reference data set is stored in the Employee Self-Service Template Configuration table \(`msdyn_employeeselfservicetemplateconfig`\). The following table lists the records, along with the agent topics that consume them.

| Reference data | Unique name in Dataverse | Used by these topics |
| --- | --- | --- |
| Phone Device Type | `msdyn_HRWorkdayHCMReferenceData_PhoneDeviceType` | Update Phone Number |
| Country Phone Code | `msdyn_HRWorkdayHCMReferenceData_CountryPhoneCode` | Update Phone Number |
| ISO Country | `msdyn_HRWorkdayHCMReferenceData_ISO3166Country` | Update Phone Number, Update Address |
| Passport ID Type | `msdyn_HRWorkdayHCMReferenceData_PassportIdType` | Get Passports |
| National ID Type | `msdyn_HRWorkdayHCMReferenceData_NationalIdType` | Get National IDs |
| Government ID Type | `msdyn_HRWorkdayHCMReferenceData_GovernmentIdType` | Get Government IDs |
| Visa ID Type | `msdyn_HRWorkdayHCMReferenceData_VisaIdType` | Get Visas |
| Degree | `msdyn_HRWorkdayHCMReferenceData_Degree` | Get Education, Get Certifications |
| Field of Study | `msdyn_HRWorkdayHCMReferenceData_FieldOfStudy` | Get Education |
| Language | `msdyn_HRWorkdayHCMReferenceData_Language` | Get Language Information |
| Language Ability Type | `msdyn_HRWorkdayHCMReferenceData_LanguageAbilityType` | Get Language Information |
| Language Proficiency | `msdyn_HRWorkdayHCMReferenceData_LanguageProficiency` | Get Language Information |
| Employee Type | `msdyn_HRWorkdayHCMReferenceData_EmployeeType` | Worker profile lookups |
| Position Time Type | `msdyn_HRWorkdayHCMReferenceData_PositionTimeType` | Worker profile lookups |
| Job Family | `msdyn_HRWorkdayHCMReferenceData_JobFamily` | Worker profile lookups |
| Management Level | `msdyn_HRWorkdayHCMReferenceData_ManagementLevel` | Worker profile lookups |
| Related Person Relationship | `msdyn_HRWorkdayHCMReferenceData_RelatedPersonRelationship` | Get Dependents, Get Emergency Contacts |

### Find the right values in Workday

The authoritative list for each reference type lives in Workday, behind the **Maintain Reference IDs** task. To export the canonical list:

1. Sign in to Workday as a user with Integration Configuration access. This user is typically a Workday admin or someone on your HRIS team.
2. In the Workday search bar, enter **Maintain Reference IDs** and run the task.
3. In the prompt that appears, select the **Reference ID Type** that you want to validate. The Reference ID Type names in Workday map directly to the records in the previous table. For example:

   - Passport ID Type maps to `msdyn_HRWorkdayHCMReferenceData_PassportIdType`.
   - National ID Type maps to `msdyn_HRWorkdayHCMReferenceData_NationalIdType`.
   - Visa ID Type maps to `msdyn_HRWorkdayHCMReferenceData_VisaIdType`.
   - Degree maps to `msdyn_HRWorkdayHCMReferenceData_Degree`.
   - Language maps to `msdyn_HRWorkdayHCMReferenceData_Language`.

[![Screenshot of the Workday View Reference IDs dialog with Passport ID Type selected as the business object.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/ess/workday-reference-data-1-view-reference-ids.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/ess/workday-reference-data-1-view-reference-ids.png#lightbox)

Workday returns the list of Reference IDs that are configured in the tenant. The **Reference ID** column is the value that you use as the key. The **Name** or **Description** column is the value that you use as the display label.

[![Screenshot of the Workday View Reference IDs results table that lists Passport ID Type reference IDs and values.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/ess/workday-reference-data-2-reference-id-list.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/ess/workday-reference-data-2-reference-id-list.png#lightbox)

Alternate Workday tasks return the same data and might be quicker to access, depending on your security profile:

- **View Reference IDs**: A read-only view of the same lists, with broader access than Maintain Reference IDs.
- **Maintain Languages**, **Maintain Language Abilities**, and **Maintain Language Proficiencies**: Each task exposes the same Reference IDs scoped to the relevant language reference type.

If your Workday tenant heavily customized these catalogs or uses a third-party identity setup, ask your Workday HRIS team to export the lists for you.

### Edit a reference data record

After you have the authoritative list from Workday, edit the matching record in Dataverse. You need the **Environment Maker** security role in the Power Platform environment to view and edit these records.

1. In the Power Apps maker portal, open **Tables** and select **Employee Self-Service Template Configuration**.
2. Filter the records by the **Unique name** column. Enter `msdyn_HRWorkdayHCMReferenceData_` to see all 17 records.
3. Open the record that corresponds to the reference type that you want to update.
4. Open the **Value** column. You see XML that looks like this example:

   ```xml
   <workdayEntityConfigurationTemplate>
     <scenario name="HRWorkdayHCMReferenceData_PassportIdType">
       <seedData type="Passport_ID_Type_ID" count="42">
         <i k="Passport_ID_Type_USA" v="United States Passport"/>
         <i k="Passport_ID_Type_GBR" v="United Kingdom Passport"/>
       </seedData>
     </scenario>
   </workdayEntityConfigurationTemplate>
   ```


   The `k` attribute on each `<i>` element is the Workday Reference ID that the agent sends back to Workday on write operations. The `v` attribute is the display label that the agent shows to the end user. Both need to match what Workday accepts.

[![Screenshot of the Employee Self-Service Template Configuration record in Power Apps showing the Value column with reference data XML.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/ess/workday-reference-data-3-edit-template-config.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/ess/workday-reference-data-3-edit-template-config.png#lightbox)

For each item in the list, compare against the Workday export:

- If a `k` value doesn't appear in your Workday list, the agent fails to write that value with an `Invalid_Reference_ID` error. Update the `k` attribute to a value that exists in your Workday tenant, or remove the entry if it doesn't apply.
- If a Workday Reference ID is missing from the template configuration, end users don't see it in the agent picker. Add a new entry in the form `<i k="YourReferenceId" v="Display label"/>` inside the `<seedData>` block.
- If a `v` label is stale or doesn't match your local language conventions, update the `v` attribute. The label is display-only and isn't sent back to Workday.

Save the record. The change takes effect on the next agent invocation. You don't need to restart a flow or republish a solution.

### Backup your customizations

Customizations to template configuration records are reset when the Workday solution is upgraded, because these records ship as part of the managed package. Before any future upgrade:

1. Open each customized record under `msdyn_HRWorkdayHCMReferenceData_*`.
2. Copy the full content of the **Value** column \(the entire XML block\) into a safe location. A SharePoint document in your tenant, a versioned file in your runbook repository, or a secure team mailbox are all reasonable choices.
3. After the upgrade completes, paste the saved XML back into the **Value** column of the corresponding record.

Until a customization-preservation approach is available, this backup and restore step is the supported pattern.

Note

The next Workday release replaces the embedded reference data approach for 12 of the 17 reference types. Instead of reading template configurations, the affected topics call Workday live, under the signed-in employee's OAuth context. No customization is needed for those 12 types, because the values come directly from your Workday tenant at runtime. The remaining five reference types continue to use the embedded template configuration approach, because Workday doesn't expose them through APIs that are accessible to a signed-in employee:

- Visa ID Type
- Degree
- Language
- Language Ability Type
- Language Proficiency

For these five types, the customization steps in this section continue to apply. Check the release notes for confirmed dates, version numbers, and the latest behavior before you plan a future upgrade.

## Related articles

- [Upgrade the Workday solution for Employee Self-Service](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/workday-upgrade-solution)
- [Upgrade an existing Workday integration to the simplified setup](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/workday-upgrade-to-simplified)
- [Creating reports for your Workday integration](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/workday-reports)
- [An introduction to Employee Self-Service](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/overview)
- [Integrate ServiceNow with your Employee Self-Service deployment](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/servicenow)
- [Integrate Workday with your Employee Self-Service deployment \(legacy ISU + RaaS reference\)](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/workday)
