<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionpolicysettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-09 -->

# tlsInspectionPolicySettings resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Defines the default behavior and configuration settings for a TLS inspection policy in Global Secure Access. These settings determine how traffic should be handled when no specific rules in the policy match the traffic pattern.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| defaultAction | microsoft.graph.networkaccess.tlsInspectionAction | The default action to take when no rules in the policy match the traffic. The possible values are: `bypass`, `inspect`, `unknownFutureValue`. Supports `$filter` \(`eq`, `ne`\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.tlsInspectionPolicySettings",
  "defaultAction": "String"
}
```
