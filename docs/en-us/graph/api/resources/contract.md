<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/contract?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-08 -->

# Contract resource type

Namespace: microsoft.graph Represents an existing partnership that the partner tenant has with a customer tenant.

> **Important:** Exists in partner tenants only. Partner tenants are Microsoft Entra tenants that belong to Microsoft partners who are either part of [Microsoft Cloud Solution Provider](https://partnercenter.microsoft.com/en-us/partner/programs), Office 365 Syndication, or Microsoft Advisor partner programs.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/contract-get?view=graph-rest-1.0) | Contract | Read properties of a specific contract object. |
| [List](https://learn.microsoft.com/en-us/graph/api/contract-list?view=graph-rest-1.0) | Contract collection | List of contracts in the partner tenant. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contractType | String | Type of contract. The possible values are: `SyndicationPartner`, `BreadthPartner`, `ResellerPartner`. See more in the [table below](#contracttype-values). |
| customerId | Guid | The unique identifier for the customer tenant referenced by this partnership. Corresponds to the id property of the customer tenant's organization resource. |
| defaultDomainName | String | A copy of the customer tenant's default domain name. The copy is made when the partnership with the customer is established. It isn't automatically updated if the customer tenant's default domain name changes. |
| displayName | String | A copy of the customer tenant's display name. The copy is made when the partnership with the customer is established. It is not automatically updated if the customer tenant's display name changes. |
| id | String | The unique identifier for the partnership. Key, read-only |

### contractType values

| Member | Description |
| :--- | :--- |
| SyndicationPartner | Partner that *exclusively* resells and manages O365 and Intune for this customer. They resell and support their customers. |
| BreadthPartner | Partner has the ability to provide administrative support for this customer. However, the partner isn't allowed to resell to the customer. |
| ResellerPartner | Partner that is similar to a syndication partner, except that the partner doesn't have exclusive access to a tenant. In the syndication case, the customer can't buy additional direct subscriptions from Microsoft or from other partners. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "contractType": "String",
  "customerId": "Guid",
  "defaultDomainName": "String",
  "displayName": "String",
  "id": "String (identifier)"
}
```
