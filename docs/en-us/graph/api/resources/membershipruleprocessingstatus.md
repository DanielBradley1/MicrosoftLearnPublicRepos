<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/membershipruleprocessingstatus?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# membershipRuleProcessingStatus resource type

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the current status of dynamic group processing.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| errorMessage | String | Detailed error message if dynamic group processing ran into an error.  <br>  <br>Optional. Read-only. |
| lastMembershipUpdated | edm.DateTime | Most recent date and time when membership of a dynamic group was updated.  <br>  <br>Optional. Read-only. |
| status | [membershipRuleProcessingStatusDetails](#membershipruleprocessingstatusdetails-values) | Current status of a dynamic group processing. The possible values are: `NotStarted`, `Running`, `Succeeded`, `Failed`, and `UnknownFutureValue`.  <br>  <br>Required. Read-only. |

### membershipRuleProcessingStatusDetails values

| Member | Description |
| :--- | :--- |
| NotStarted | Group has been created or updated, and awaiting processing. |
| Running | Processing has started. |
| Succeeded | Processing has completed. Incremental object changes are processed perpetually. |
| Failed | Processing ran into an error. See **errorMessage** for details. |
| UnknownFutureValue | Supports future values. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "status": "string",
  "lastMembershipUpdated": "DateTime",
  "errorMessage": "string"
}
```
