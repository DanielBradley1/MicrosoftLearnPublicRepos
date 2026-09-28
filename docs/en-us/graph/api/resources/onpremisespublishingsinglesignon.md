<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onpremisespublishingsinglesignon?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# onPremisesPublishingSingleSignOn resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the single sign-on settings \(**singleSignOnSettings** property\) for the [onPremisesPublishing](https://learn.microsoft.com/en-us/graph/api/resources/onpremisespublishing?view=graph-rest-beta) resource when publishing an on-premises application with Microsoft Entra application proxy. This resource is used for setting Integrated Windows Authentication and header-based authentication as the single-sign on mode. For more information, see [Kerberos Constrained Delegation for single-sign on to your apps with Application Proxy](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/application-proxy-configure-single-sign-on-with-kcd).

Note

Do not use this property for configuring SAML or password-based single-sign on. If you are configuring SAML single-sign-on this must be set on the [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-beta). If you are configuring password-based single-sign this must be set using [createPasswordSingleSignOnCredentials](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-createpasswordsinglesignoncredentials?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| kerberosSignOnSettings | [kerberosSignOnSettings](https://learn.microsoft.com/en-us/graph/api/resources/kerberossignonsettings?view=graph-rest-beta) | The Kerberos Constrained Delegation settings for applications that use Integrated Window Authentication. |
| singleSignOnMode | singleSignOnMode | The preferred single-sign on mode for the application. The possible values are: `none`, `onPremisesKerberos`, `aadHeaderBased`,`pingHeaderBased`, `oAuthToken`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "kerberosSignOnSettings": {"@odata.type": "microsoft.graph.kerberosSignOnSettings"},
  "singleSignOnMode": "String"
}
```
