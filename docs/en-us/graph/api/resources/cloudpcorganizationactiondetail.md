<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcorganizationactiondetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-17 -->

# cloudPcOrganizationActionDetail resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the result of a Cloud PC organization action used to activate or deactivate an organization for Windows 365 for Agents.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionType | [cloudPcOrganizationActionType](#cloudpcorganizationactiontype-values) | The Cloud PC organization action type. Possible values: `activate`, `deactivate`, and `unknownFutureValue`. |
| errorDescription | String | More user-friendly error details. For example, `Activation failed due to invalid billing plan`. |
| status | [cloudPcOrganizationActionStatus](#cloudpcorganizationactionstatus-values) | The Cloud PC organization action status. Possible values: `inProgress`, `succeeded`, `failed`, and `unknownFutureValue`. Default is `inProgress`. |

### cloudPcOrganizationActionType values

| Member | Description |
| :--- | :--- |
| activate | To activate the organization for Windows 365 for Agents. |
| deactivate | To deactivate the organization for Windows 365 for Agents. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

### cloudPcOrganizationActionStatus values

| Member | Description |
| :--- | :--- |
| inProgress | The Cloud PC organization action is in progress. |
| succeeded | The Cloud PC organization action succeeded. |
| failed | The Cloud PC organization action failed. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcOrganizationActionDetail",
  "actionType": "String",
  "errorDescription": "String",
  "status": "String"
}
```
