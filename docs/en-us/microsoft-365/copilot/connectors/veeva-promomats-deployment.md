<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/veeva-promomats-deployment -->
<!-- Sitemap-Last-Modified: 2026-06-23 -->

# Deploy the Veeva PromoMats connector

The Veeva PromoMats Microsoft 365 Copilot connector allows organizations to index promotional marketing materials from Veeva PromoMats into Microsoft Graph, making them accessible across Microsoft 365 experiences, including Microsoft 365 Copilot and Microsoft Search. The connector integrates the Vault PromoMats built-in permission model to ensure that users only access authorized content, and supports faster content generation and review through content analysis and preparation. It helps maintain brand consistency by improving efficiency throughout the content lifecycle. This functionality is beneficial for marketing, medical affairs, and regulatory teams, enabling informed decision-making and reducing the time-to-market for promotional materials.

This article describes the steps to deploy and customize the Veeva PromoMats connector. For general information about Copilot connector deployment, see [Set up Copilot connectors in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/deployment-overview).

## Prerequisites

Before you deploy the connector, make sure that you meet the following prerequisites:

- You must be a Microsoft 365 admin.
- You must have access to a configured Veeva PromoMats environment.
- You must have the necessary permissions in both Microsoft Entra ID and Veeva PromoMats to register applications and configure OAuth/OpenID Connect.
- You must have the PromoMats instance URL and admin credentials.

### Register an application and configure OAuth

Use the following steps to configure Microsoft Entra ID OAuth 2.0/OpenID Connect for the Veeva PromoMats connector.

1. Register an application in Microsoft Entra ID.

   - Go to **Microsoft Entra admin center** > **App registrations** > **New registration**.
   - Name the application and select **Accounts in this organizational directory only**.
   - Add the redirect URI:

     - For Microsoft 365 Enterprise: `https://gcs.office.com/v1.0/admin/oauth/callback`
     - For Microsoft 365 Government: `https://gcsgcc.office.com/v1.0/admin/oauth/callback`

   - Generate a client secret under **Certificates & Secrets** and store it securely.
   - Configure API permissions for the application. Go to **API permissions** > **Add a permission** > **Microsoft Graph** > **Delegated permissions**, and add the following scopes:

     - `offline_access` – Required to obtain refresh tokens for persistent access.
     - `{client_id}/.default` – Required to link the Microsoft Entra user with the Veeva user. Replace `{client_id}` with the application \(client\) ID of your registered Entra application.

   - Select **Grant admin consent** to consent on behalf of your organization.

2. Configure OAuth in Veeva PromoMats.

   - Go to **Admin > Settings > OAuth 2.0/OpenID Connect Profiles**.
   - Create a new profile, set the **Status** to active, and select **Azure AD** as the provider.
   - Choose **Upload AS metadata** > **Provide Authorization Server Metadata URL**, and paste the following link. Replace {tenant-id} with your tenant ID. `https://login.microsoftonline.com/{tenant-id}/v2.0/.well-known/openid-configuration`
   - Set **Identity is in another claim** to `upn`, and in **User ID Type**, select **Federated ID**. The UPN should be the same as the federated ID.
   - Choose **Client Applications** > **Add**, and use the client ID from your Microsoft Entra ID application for both **Application Client ID** and **Authorization Server Client ID**. Add an **Application Label**.


   Note


   To enable **Perform strict Audience Restriction validation**, add the client ID to the **Audience** field.

3. Create security policies and link users.

   - Go to **Admin > Settings > Security Policies** > **Create** > **Single sign-on**. Provide a name and description, and set the status to **active**.
   - For the authentication type, choose **Single Sign-on**, and choose a profile. For more information, see [Configuring Single Sign-on](https://platform.veevavault.help/en/gr/13977/).
   - In **eSignature Profile**, select **None**, and in **OAuth 2.0 / OpenID Connect Profile**, select the OAuth 2.0 profile that you created. Keep the default values for the remaining settings.
   - Go to **Admin** > **Users & Groups**, select the vault owner, and choose **Edit**.
   - In **Details** > **Security Policy**, change the values to the new policy, and in **Federated ID**, change the value to the UPN of the connector admin account.

## Deploy the connector

To add the Veeva PromoMats connector for your organization:

1. In the Microsoft 365 admin center, in the left pane, choose **Copilot** > **Connectors**.
2. Choose the **Gallery** tab.
3. From the list of available connectors, choose **Veeva PromoMats**.

### Set display name

The display name is used to identify references in Copilot responses to help users recognize the associated file or item. The display name also signifies trusted content and is used as a content source filter.

You can accept the default **Veeva PromoMats** display name, or customize the value to use a display name that users in your organization recognize.

For more information about connector display names and descriptions, see [Enhance Copilot discovery of connector content](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/enhance-copilot-discovery).

### Set instance URL

Enter the URL of your Veeva PromoMats instance. For example: `https://<your-vault-domain>.veevavault.com`

### Choose authentication type

To authenticate the Veeva PromoMats connector, select **Microsoft Entra ID OIDC** for the **Authentication type**. Enter the following information:

- **Vault session ID URL**: In Veeva PromoMats, go to **Admin panel** > **Settings** > **OAuth 2.0/ OpenID Connect Profiles**, and select the profile you created for this connection. Copy the Vault Session ID URL.
- **Client ID**: The application ID for the Microsoft Entra application you registered for Veeva PromoMats.
- **Client secret**: The client secret associated with the Entra application.

Select **Authorize** to sign in with your Microsoft Entra ID account. Select **Consent on behalf of your organization**, and on the permission request screen, choose **Accept**.

Important

To enable Microsoft Entra ID authentication, configure both Microsoft Entra ID and Veeva PromoMats admin settings. Ensure the API permissions \(`offline_access` and `{client_id}/.default`\) are granted admin consent before authorizing the connector.

### Roll out

To roll out to a limited audience, choose the toggle next to **Rollout to limited audience** and specify the users and groups to roll the connector out to. For more information, see [Staged rollout for Copilot connectors](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/staged-rollout).

Choose **Create** to deploy the connection. The Veeva PromoMats Copilot connector starts indexing content right away.

The following table lists the default values that are set.

| Category | Default value |
| --- | --- |
| Users | Respects Veeva Vault permissions; only viewable documents are accessible. |
| Content | Indexes key metadata, such as document name, owner, and lifecycle stage. Enables metadata like title, created by, and last modified by. |
| Sync | Full crawl – daily. |

To customize these values, choose **Custom setup**. For more information, see [Customize settings](#customize-settings-optional).

After you create your connection, you can review the status in the **Connectors** section of the [Microsoft 365 admin center](https://admin.microsoft.com/).

## Customize settings \(optional\)

You can customize the default values for the Veeva PromoMats connector settings. To customize settings, on the connector page in the admin center, choose **Custom setup**.

### Customize user settings

#### Access permissions

The connector adheres to the access control lists \(ACLs\) defined in Veeva PromoMats. Only users with view permissions in Veeva PromoMats can see the indexed content in Microsoft 365. Admins can optionally allow all users access to all indexed content, although this isn't recommended.

#### Mapping identities

The connector requires that PromoMats user identities map to the organization's Microsoft Entra ID identities. If the identities don't automatically match, admins can configure custom user mappings so that access rights are enforced. For example, you can map identities based on email addresses or other unique identifiers.

To enforce the security settings of your Veeva PromoMats instance, select **Non-ME-ID** as the identity type for your content source.

Enter the required information for identity mapping. For example, if you want to map identities based on email addresses:

1. For the **Microsoft Entra user property**, select **Mail**.
2. Under **non-Microsoft Entra user property**, select **Add identity property**, and choose **Email**. Use an expression such as `([^@]+)` to capture a sequence of one or more characters that are not the `@` symbol. Create a formula to complete the mapping, such as `{0}@<your-domain>`.

### Customize content settings

#### Query string

Admins can use query string conditions to precisely control the synchronization of articles to ensure efficient indexing. For example, you can filter by metadata, document state, or time to include only relevant content.

#### Manage properties

You can view and manage properties crawled from your Veeva PromoMats instance. The following table lists the properties that the connector indexes by default.

| Property | Veeva field | Semantic label | Description | Schema attributes |
| --- | --- | --- | --- | --- |
| Id | document\_number\_\_v |  | Unique identifier of the document | Query, Retrieve |
| DocId | id |  | Internal document identifier \(primary key\) in the Veeva system | Query, Retrieve |
| GlobalId | global\_id\_\_sys |  | System-generated globally unique identifier across Vaults | Query, Retrieve |
| DocumentNumber | document\_number\_\_v |  | System-assigned document number in the Veeva system | Query, Retrieve |
| FileName | filename\_\_v | fileName | Name of the uploaded source file | Query, Retrieve |
| Title | title\_\_v | title | Document title | Retrieve, Search |
| Description | description\_\_v |  | Free-text description of the document | Retrieve, Search |
| Extension | file extension of filename\_\_v | fileExtension | File type extension \(for example, PDF, DOCX, PPTX\) | Query, Retrieve, Search |
| Url | https://{vaultDns}/ui/#doc\_info/{id} | url | Direct URL to access or preview the document in Veeva Vault | Query, Retrieve |
| Status | status\_\_v |  | Document status \(for example, Active, Archived\) | Query, Retrieve |
| VersionId | version\_id |  | Unique identifier for a specific document version | Query, Retrieve |
| MajorVersion | major\_version\_number\_\_v |  | Major version number of the document | Query, Retrieve |
| MinorVersion | minor\_version\_number\_\_v |  | Minor version or revision number | Query, Retrieve |
| Type | type\_\_v | containerName | Top-level document type classification | Query, Retrieve |
| Subtype | subtype\_\_v |  | Second-level document classification under type | Query, Retrieve |
| Product | product\_\_v.name\_\_v |  | Product associated with the document content | Query, Retrieve |
| Brand | branding\_\_v |  | Brand associated with the promotional material | Query, Retrieve, Search, Refine |
| SecondaryBrand | secondary\_brands\_\_v |  | Secondary brands associated with the promotional material | Query, Retrieve, Search, Refine |
| KeyMessages | key\_message\_\_v |  | Key messages associated with the promotional material | Retrieve, Search |
| Tags | tags\_\_v | tags | Tags or keywords associated with the document | Query, Retrieve, Refine |
| Country | country\_\_v.name\_\_v |  | Country or region related to the document | Query, Retrieve |
| Format | format\_\_v |  | File format of the source document | Query, Retrieve |
| ItemType | format\_\_v | itemType | Item type derived from the document format | Query, Retrieve, Refine |
| ItemPath | {type\_\_v}/{subtype\_\_v} | itemPath | Hierarchical path combining the document type and subtype | Query, Retrieve |
| Authors | file\_meta\_author\_\_v | authors | Author metadata from the source file | Query, Retrieve, Refine |
| DocumentCreationDate | document\_creation\_date\_\_v | createdDateTime | Date and time the document was created in Vault | Query, Retrieve |
| VersionModifiedDate | version\_modified\_date\_\_v | lastModifiedDateTime | Date and time when this version was last modified | Query, Retrieve |
| CreatedBy | created\_by\_\_v \(name, email\) | createdBy | User who initially created the document | Query, Retrieve, Search |
| CreatedByUserId | created\_by\_\_v |  | Internal user identifier for document creator | Query, Retrieve |
| LastModifiedByUserId | last\_modified\_by\_\_v |  | Internal user identifier for last modifier | Query, Retrieve |
| LastModifiedBy | last\_modified\_by\_\_v \(name, email\) | lastModifiedBy | User who last modified the document | Query, Retrieve, Search |
| Lifecycle | lifecycle\_\_v |  | Lifecycle assigned to the document | Query, Retrieve |
| Size | size\_\_v |  | File size of the document |  |
| Content | document content |  | Main text or body content extracted from the document | Search |

#### Add custom properties

In addition to the default properties, the connector automatically discovers custom and other document properties from your Veeva PromoMats instance. During setup, the connector retrieves all available document fields that are queryable, not disabled, and not hidden, and presents them as additional properties under **Manage properties**.

You can select and add these custom properties one by one to the connector schema. Each added custom property has the following default schema attributes:

- **Query** and **Retrieve** are enabled by default.
- **Search** and **Refine** aren't enabled by default but can be turned on under **Manage properties**.

For properties that reference Veeva Vault objects \(ObjectReference type\), the connector also fetches the referenced object's metadata and exposes its fields as nested properties. For example, if a custom property references a VObject of type `campaign__v`, the connector generates properties like `campaign__v.name__v`, `campaign__v.status__v`, and so on.

After adding custom properties, you can customize the schema attributes for any property—both default and custom—under **Manage properties**. You can enable or disable **Query**, **Retrieve**, **Search**, and **Refine** for each property based on your organization's requirements.

### Customize sync intervals

You can change how often the connector does a full crawl to fit your organization's needs. By default, the connector does a full crawl every day.

For more information, see [Guidelines for crawl settings](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/deployment-overview#guidelines-for-crawl-settings).

## Related content

- [Veeva PromoMats connector overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/veeva-promomats-overview)
- [Troubleshoot issues with the Veeva PromoMats connector](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/veeva-promomats-troubleshooting)
- [Set up Copilot connectors in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/deployment-overview)
