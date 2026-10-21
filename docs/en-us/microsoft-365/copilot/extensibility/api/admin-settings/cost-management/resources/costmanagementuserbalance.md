<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserbalance -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# costManagementUserBalance resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

A user's computed per-service consumption balance. Addressed by the user's identifier; one balance resource exists per user. A user who never consumed anything still returns an empty `serviceBalances` collection rather than a `404` response.

Note

The parent collection `GET /copilot/costManagement/userBalances` is declared but isn't listable and returns a `404` response. Read a balance by the user's identifier instead.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementuserbalance-get) | [costManagementUserBalance](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserbalance) | Retrieve the properties and relationships of a costManagementUserBalance object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `id` | String | The user's identifier \(computed key\). Read-only. |
| `selectionDataStatus` | [selectionDataStatus](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/selectiondatastatus) | When the balance was evaluated and the as-of times of each contributing source. Reported once for the user. Read-only. |
| `unevaluatedServices` | [costManagementUnevaluatedService](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementunevaluatedservice) collection | Services whose balance couldn't be evaluated. A non-empty collection means a partial result; when no service can be evaluated, the request fails with a `503 sourceUnavailable` response. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| `serviceBalances` | [costManagementUserServiceBalance](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserservicebalance) collection | Per-service balance rows. Services listed in `unevaluatedServices` are omitted. Expand to inline the rows. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.costManagementUserBalance",
  "id": "String",
  "selectionDataStatus": {
    "@odata.type": "microsoft.graph.selectionDataStatus"
  },
  "unevaluatedServices": [
    {
      "@odata.type": "microsoft.graph.costManagementUnevaluatedService"
    }
  ]
}
```
