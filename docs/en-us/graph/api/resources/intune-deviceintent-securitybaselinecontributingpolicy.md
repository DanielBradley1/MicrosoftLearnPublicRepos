<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinecontributingpolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# securityBaselineContributingPolicy resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The security baseline compliance state of a setting for a device

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| sourceId | String | Unique identifier of the policy |
| displayName | String | Name of the policy |
| sourceType | [securityBaselinePolicySourceType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinepolicysourcetype?view=graph-rest-beta) | Authoring source of the policy. Possible values are: `deviceConfiguration`, `deviceIntent`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.securityBaselineContributingPolicy",
  "sourceId": "String",
  "displayName": "String",
  "sourceType": "String"
}
```
