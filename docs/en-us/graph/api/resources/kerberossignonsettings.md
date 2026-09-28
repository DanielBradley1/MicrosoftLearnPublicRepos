<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/kerberossignonsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# kerberosSignOnSettings resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the Kerberos Constrained Delegation \(KCD\) settings \(**kerberosSignOnSettings** property\) for the [onPremisesPublishingSingleSignOn](https://learn.microsoft.com/en-us/graph/api/resources/onpremisespublishingsinglesignon?view=graph-rest-beta) resource when publishing an on-premises application via Microsoft Entra application proxy. Application Proxy uses Kerberos Constrained Delegation \(KCD\) to support single-sign on to Integrated Windows Authentication applications. For more information, see [Kerberos Constrained Delegation for single-sign on to your apps with Application Proxy](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/application-proxy-configure-single-sign-on-with-kcd).

Note

Do not use this property for configuring SAML or password-based single-sign on. If you are configuring SAML single-sign-on this must be set on the [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-beta). If you are configuring password-based single-sign this must be set using [createPasswordSingleSignOnCredentials](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-createpasswordsinglesignoncredentials?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| kerberosServicePrincipalName | String | The Internal Application SPN of the application server. This SPN needs to be in the list of services to which the connector can present delegated credentials. |
| kerberosSignOnMappingAttributeType | kerberosSignOnMappingAttributeType | The Delegated Login Identity for the connector to use on behalf of your users. For more information, see [Working with different on-premises and cloud identities](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/application-proxy-configure-single-sign-on-with-kcd#working-with-different-on-premises-and-cloud-identities). The possible values are: `userPrincipalName`, `onPremisesUserPrincipalName`, `userPrincipalUsername`, `onPremisesUserPrincipalUsername`, `onPremisesSAMAccountName`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "kerberosServicePrincipalName": "String",
  "kerberosSignOnMappingAttributeType": "String"
}
```
