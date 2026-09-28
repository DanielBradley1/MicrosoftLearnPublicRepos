<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernanceusersettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-14 -->

# identityGovernanceUserSettings resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents identity governance settings for a user, including the approver delegate configuration. This resource is accessed via the `identityGovernance` property on the [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-beta) resource.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| approverDelegate | [approverDelegate](https://learn.microsoft.com/en-us/graph/api/resources/approverdelegate?view=graph-rest-beta) | The approver delegate configuration for the user, including the delegate identity and delegation schedule. Nullable. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernanceUserSettings",
  "approverDelegate": {
    "@odata.type": "microsoft.graph.approverDelegate"
  }
}
```
