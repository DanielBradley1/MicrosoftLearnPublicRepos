<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/organization?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-23 -->

# organization resource type

Namespace: microsoft.graph

Represents the Microsoft Entra tenant that the user or application is authenticated to. Only the read and update operations are supported on this resource. Inherits from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0).

This resource lets you add your own data to custom properties using [extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/organization-list?view=graph-rest-1.0) | [organization](https://learn.microsoft.com/en-us/graph/api/resources/organization?view=graph-rest-1.0) collection | Read properties and relationships of the organization object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/organization-get?view=graph-rest-1.0) | [organization](https://learn.microsoft.com/en-us/graph/api/resources/organization?view=graph-rest-1.0) collection | Read properties and relationships of organization object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/organization-update?view=graph-rest-1.0) | None | Update an organization object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignedPlans | [assignedPlan](https://learn.microsoft.com/en-us/graph/api/resources/assignedplan?view=graph-rest-1.0) collection | The collection of service plans associated with the tenant. Not nullable. |
| businessPhones | String collection | Telephone number for the organization. Although this property is a string collection, only one number can be set. |
| city | String | City name of the address for the organization. |
| country | String | Country or region name of the address for the organization. |
| countryLetterCode | String | Country or region abbreviation for the organization in ISO 3166-2 format. |
| createdDateTime | DateTimeOffset | Timestamp of when the organization was created. The value can't be modified and is automatically populated when the organization is created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| defaultUsageLocation | String | Two-letter ISO 3166 country code indicating the default service usage location of an organization. |
| deletedDateTime | DateTimeOffset | Represents date and time of when the Microsoft Entra tenant was deleted using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| displayName | String | The display name for the tenant. |
| id | String | The tenant ID, a unique identifier representing the organization \(or tenant\). Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0). Key. Not nullable. Read-only. |
| isMultipleDataLocationsForServicesEnabled | Boolean | `true` if organization is Multi-Geo enabled; **false** if the organization isn't Multi-Geo enabled; **null** \(default\). Read-only. For more information, see [OneDrive Online Multi-Geo](https://learn.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-introduction). |
| marketingNotificationEmails | String collection | Not nullable. |
| onPremisesLastSyncDateTime | DateTimeOffset | The time and date at which the tenant was last synced with the on-premises directory. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| onPremisesSyncEnabled | Boolean | `true` if this object is synced from an on-premises directory; `false` if this object was originally synced from an on-premises directory but is no longer synced. Nullable. `null` if this object isn't synced from on-premises active directory \(default\). |
| partnerTenantType | partnerTenantType | The type of partnership this tenant has with Microsoft. The possible values are: `microsoftSupport`, `syndicatePartner`, `breadthPartner`, `breadthPartnerDelegatedAdmin`, `resellerPartnerDelegatedAdmin`, `valueAddedResellerPartnerDelegatedAdmin`, `unknownFutureValue`. Nullable. For more information about the possible types, see [partnerTenantType values](#partnertenanttype-values). |
| postalCode | String | Postal code of the address for the organization. |
| preferredLanguage | String | The preferred language for the organization. Should follow ISO 639-1 Code; for example, `en`. |
| privacyProfile | [privacyProfile](https://learn.microsoft.com/en-us/graph/api/resources/privacyprofile?view=graph-rest-1.0) | The privacy profile of an organization. |
| provisionedPlans | [ProvisionedPlan](https://learn.microsoft.com/en-us/graph/api/resources/provisionedplan?view=graph-rest-1.0) collection | Not nullable. |
| securityComplianceNotificationMails | String collection | Not nullable. |
| securityComplianceNotificationPhones | String collection | Not nullable. |
| state | String | State name of the address for the organization. |
| street | String | Street name of the address for organization. |
| technicalNotificationMails | String collection | Not nullable. |
| tenantType | String | Not nullable. Can be one of the following types:<br><br><li> <code>AAD</code> - An enterprise identity access management (IAM) service that serves business-to-employee and business-to-business (B2B) scenarios. </li><br><br><li> <code>AAD B2C</code> An identity access management (IAM) service that serves business-to-consumer (B2C) scenarios.  </li><br><br><li> <code>CIAM</code> - A customer identity &amp; access management (CIAM) solution that provides an integrated platform to serve consumers, partners, and citizen scenarios.</li> |
| verifiedDomains | [VerifiedDomain](https://learn.microsoft.com/en-us/graph/api/resources/verifieddomain?view=graph-rest-1.0) collection | The collection of domains associated with this tenant. Not nullable. |

### partnerTenantType values

| Member | Description |
| --- | --- |
| microsoftSupport | Legacy support tenant of Microsoft that was used to provide administrative support to all customer tenants. |
| breadthPartner | The partner can provide administrative support for their customers. However, the partner isn't allowed to resell to or request delegated admin permissions from customers. |
| breadthPartnerDelegatedAdmin | Similar to Breadth Partner except they can request for delegated admin permissions \(DAP\) from customer tenants. |
| syndicatePartner | The partner exclusively resells and manages Microsoft 365 and Intune for their customers. The customer can't buy more subscriptions directly or through other Microsoft partners. |
| resellerPartnerDelegatedAdmin | The partner that can resell and manage Microsoft 365 and Intune for their customers. There's no exclusivity clause like for syndication partners. The customer can buy more subscriptions directly from Microsoft or through other Microsoft partners. |
| valueAddedResellerPartnerDelegatedAdmin | They're Tier 2 partners. They're Microsoft partners that have a relationship with another Microsoft partner such as a reseller. |
| unknownFutureValue | Evolvable enumeration sentinel value. Do not use. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| certificateBasedAuthConfiguration | [certificateBasedAuthConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedauthconfiguration?view=graph-rest-1.0) collection | Navigation property to manage certificate-based authentication configuration. Only a single instance of certificateBasedAuthConfiguration can be created in the collection. |
| extensions | [extension](https://learn.microsoft.com/en-us/graph/api/resources/extension?view=graph-rest-1.0) collection | The collection of open extensions defined for the organization. Read-only. Nullable. |
| branding | [organizationalBranding](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbranding?view=graph-rest-1.0) | Branding for the organization. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "assignedPlans": [{"@odata.type": "microsoft.graph.assignedPlan"}],
  "businessPhones": ["string"],
  "city": "string",
  "country": "string",
  "countryLetterCode": "string",
  "createdDateTime": "String (timestamp)",
  "defaultUsageLocation": "String",
  "deletedDateTime": "String (timestamp)",
  "displayName": "string",
  "id": "string (identifier)",
  "isMultipleDataLocationsForServicesEnabled": "boolean",
  "marketingNotificationEmails": ["string"],
  "onPremisesLastSyncDateTime": "String (timestamp)",
  "onPremisesSyncEnabled": true,
  "partnerTenantType": "String",
  "postalCode": "string",
  "preferredLanguage": "string",
  "privacyProfile": {"@odata.type": "microsoft.graph.privacyProfile"},
  "provisionedPlans": [{"@odata.type": "microsoft.graph.provisionedPlan"}],
  "securityComplianceNotificationMails": ["string"],
  "securityComplianceNotificationPhones": ["string"],
  "state": "string",
  "street": "string",
  "technicalNotificationMails": ["string"],
  "tenantType": "string",
  "verifiedDomains": [{"@odata.type": "microsoft.graph.verifiedDomain"}]
}
```

## Related content

- [Add custom data to resources using extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview)
- [Add custom data to users using open extensions](https://learn.microsoft.com/en-us/graph/extensibility-open-users)
- [Add custom data to groups using schema extensions](https://learn.microsoft.com/en-us/graph/extensibility-schema-groups)
