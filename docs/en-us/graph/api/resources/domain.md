<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/domain?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-11-01 -->

# domain resource type

Namespace: microsoft.graph

Represents a domain associated with the tenant.

Use domain operations to associate domains to a tenant, verify domain ownership, and configure supported services. Verifying a domain through Microsoft Graph doesn't configure the domain for use with Office 365 services like Exchange. Fully configuring the domain to work with Microsoft 365 products might require extra steps. For more information, see [Microsoft 365 admin setup](https://learn.microsoft.com/en-us/microsoft-365/admin/setup/add-domain).

To associate a domain with a tenant:

1. [Associate](https://learn.microsoft.com/en-us/graph/api/domain-post-domains?view=graph-rest-1.0) a domain with a tenant.
2. [Retrieve](https://learn.microsoft.com/en-us/graph/api/domain-list-verificationdnsrecords?view=graph-rest-1.0) the domain verification records. Add the verification record details to the domain's zone file using the domain registrar or DNS server configuration.
3. [Verify](https://learn.microsoft.com/en-us/graph/api/domain-verify?view=graph-rest-1.0) the ownership of the domain, including executing external admin takeover. This operation sets the **isVerified** property to `true`.
4. [Indicate](https://learn.microsoft.com/en-us/graph/api/domain-update?view=graph-rest-1.0) the supported services you plan to use with the domain.
5. [Configure](https://learn.microsoft.com/en-us/graph/api/domain-list-serviceconfigurationrecords?view=graph-rest-1.0) supported services by retrieving a list of records needed to enable services for the domain. Add the configuration record details to the domain's zone file using the domain registrar or DNS server configuration.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/domain-list?view=graph-rest-1.0) | [domain](https://learn.microsoft.com/en-us/graph/api/resources/domain?view=graph-rest-1.0) | Retrieve all domains linked to the tenant. |
| [Create](https://learn.microsoft.com/en-us/graph/api/domain-post-domains?view=graph-rest-1.0) | [domain](https://learn.microsoft.com/en-us/graph/api/resources/domain?view=graph-rest-1.0) | Adds a domain to the tenant. |
| [Get](https://learn.microsoft.com/en-us/graph/api/domain-get?view=graph-rest-1.0) | [domain](https://learn.microsoft.com/en-us/graph/api/resources/domain?view=graph-rest-1.0) | Read properties and relationships of a domain object. |
| [Get root domain](https://learn.microsoft.com/en-us/graph/api/domain-get-rootdomain?view=graph-rest-1.0) | [domain](https://learn.microsoft.com/en-us/graph/api/resources/domain?view=graph-rest-1.0) | Get the root domain of a subdomain. |
| [Update](https://learn.microsoft.com/en-us/graph/api/domain-update?view=graph-rest-1.0) | [domain](https://learn.microsoft.com/en-us/graph/api/resources/domain?view=graph-rest-1.0) | Updates a domain. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/domain-delete?view=graph-rest-1.0) | None | Deletes a domain. |
| [Force delete](https://learn.microsoft.com/en-us/graph/api/domain-forcedelete?view=graph-rest-1.0) | None | Deletes a domain using an asynchronous operation. |
| [Verify](https://learn.microsoft.com/en-us/graph/api/domain-verify?view=graph-rest-1.0) | [domain](https://learn.microsoft.com/en-us/graph/api/resources/domain?view=graph-rest-1.0) | Validates the ownership of the domain. |
| [Promote](https://learn.microsoft.com/en-us/graph/api/domain-promote?view=graph-rest-1.0) | Boolean | Promote a verified subdomain to the root domain. |
| [List domain name references](https://learn.microsoft.com/en-us/graph/api/domain-list-domainnamereferences?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Retrieve a list of directory objects with a reference to the domain. |
| [List service configuration records](https://learn.microsoft.com/en-us/graph/api/domain-list-serviceconfigurationrecords?view=graph-rest-1.0) | [domainDnsRecord](https://learn.microsoft.com/en-us/graph/api/resources/domaindnsrecord?view=graph-rest-1.0) collection | Retrieve a list of domain DNS records for domain configuration. |
| [List verification DNS records](https://learn.microsoft.com/en-us/graph/api/domain-list-verificationdnsrecords?view=graph-rest-1.0) | [domainDnsRecord](https://learn.microsoft.com/en-us/graph/api/resources/domaindnsrecord?view=graph-rest-1.0) collection | Retrieve a list of domain DNS records for domain verification. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationType | String | Indicates the configured authentication type for the domain. The value is either `Managed` or `Federated`. `Managed` indicates a cloud managed domain where Microsoft Entra ID performs user authentication. `Federated` indicates authentication is federated with an identity provider such as the tenant's on-premises Active Directory via Active Directory Federation Services. Not nullable.  <br>  <br>To update this property in delegated scenarios, the calling app must be assigned the *Domain-InternalFederation.ReadWrite.All* permission. |
| availabilityStatus | String | This property is always `null` except when the [verify](https://learn.microsoft.com/en-us/graph/api/domain-verify?view=graph-rest-1.0) action is used. When the [verify](https://learn.microsoft.com/en-us/graph/api/domain-verify?view=graph-rest-1.0) action is used, a **domain** entity is returned in the response. The **availabilityStatus** property of the **domain** entity in the response is either `AvailableImmediately` or `EmailVerifiedDomainTakeoverScheduled`. |
| id | String | The fully qualified name of the domain. Key, immutable, not nullable, unique. |
| isAdminManaged | Boolean | The value of the property is `false` if the DNS record management of the domain is delegated to Microsoft 365. Otherwise, the value is `true`. Not nullable |
| isDefault | Boolean | `true` if this is the default domain that is used for user creation. There's only one default domain per company. Not nullable. |
| isInitial | Boolean | `true` if this is the initial domain created by Microsoft Online Services \(contoso.com\). There's only one initial domain per company. Not nullable |
| isRoot | Boolean | `true` if the domain is a verified root domain. Otherwise, `false` if the domain is a subdomain or unverified. Not nullable. |
| isVerified | Boolean | `true` if the domain completed domain ownership verification. Not nullable. |
| passwordNotificationWindowInDays | Int32 | Specifies the number of days before a user receives notification that their password expires. If the property isn't set, a default value of 14 days is used. |
| passwordValidityPeriodInDays | Int32 | Specifies the length of time that a password is valid before it must be changed. If the property isn't set, a default value of 90 days is used. |
| state | [domainState](https://learn.microsoft.com/en-us/graph/api/resources/domainstate?view=graph-rest-1.0) | Status of asynchronous operations scheduled for the domain. |
| supportedServices | String collection | The capabilities assigned to the domain. Can include `0`, `1` or more of following values: `Email`, `Sharepoint`, `EmailInternalRelayOnly`, `OfficeCommunicationsOnline`, `SharePointDefaultDomain`, `FullRedelegation`, `SharePointPublic`, `OrgIdAuthentication`, `Yammer`, `Intune`. The values that you can add or remove using the API include: `Email`, `OfficeCommunicationsOnline`, `Yammer`. Not nullable. |

## Relationships

Relationships between a domain and other objects in the directory such as its verification records and service configuration records are exposed through navigation properties. You can read these relationships by targeting these navigation properties in your requests.

| Relationship | Type | Description |
| :--- | :--- | :--- |
| domainNameReferences | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | The objects such as users and groups that reference the domain ID. Read-only, Nullable. Doesn't support `$expand`. Supports `$filter` by the OData type of objects returned. For example, `/domains/{domainId}/domainNameReferences/microsoft.graph.user` and `/domains/{domainId}/domainNameReferences/microsoft.graph.group`. |
| federationConfiguration | [internalDomainFederation](https://learn.microsoft.com/en-us/graph/api/resources/internaldomainfederation?view=graph-rest-1.0) | Domain settings configured by a customer when federated with Microsoft Entra ID. Doesn't support `$expand`. |
| rootDomain | [domain](https://learn.microsoft.com/en-us/graph/api/resources/domain?view=graph-rest-1.0) | Root domain of a subdomain. Read-only, Nullable. Supports `$expand`. |
| serviceConfigurationRecords | [domainDnsRecord](https://learn.microsoft.com/en-us/graph/api/resources/domaindnsrecord?view=graph-rest-1.0) collection | DNS records the customer adds to the DNS zone file of the domain before the domain can be used by Microsoft Online services. Read-only, Nullable. Doesn't support `$expand`. |
| verificationDnsRecords | [domainDnsRecord](https://learn.microsoft.com/en-us/graph/api/resources/domaindnsrecord?view=graph-rest-1.0) collection | DNS records that the customer adds to the DNS zone file of the domain before the customer can complete domain ownership verification with Microsoft Entra ID. Read-only, Nullable. Doesn't support `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "authenticationType": "String",
  "availabilityStatus": "String",
  "id": "String (identifier)",
  "isAdminManaged": true,
  "isDefault": true,
  "isInitial": true,
  "isRoot": true,
  "isVerified": true,
  "passwordNotificationWindowInDays": 14,
  "passwordValidityPeriodInDays": 90,
  "state": {"@odata.type": "microsoft.graph.domainState"},
  "supportedServices": ["String"]
}
```
