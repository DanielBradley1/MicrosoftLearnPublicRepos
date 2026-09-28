<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/reportsuspiciousactivitysettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-03 -->

# reportSuspiciousActivitySettings resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Defines the report suspicious activity settings for the tenant, whether it's enabled and which group of users is enabled for use. Report suspicious activity enables users to report a suspicious voice or phone app notification multifactor authentication prompt as suspicious. These users have their user risk set to `high`, and a [risk detection](https://learn.microsoft.com/en-us/graph/api/resources/riskdetection?view=graph-rest-beta) **riskEventType** of `userReportedSuspiciousActivity` is emitted.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| includeTarget | [includeTarget](https://learn.microsoft.com/en-us/graph/api/resources/includetarget?view=graph-rest-beta) | Group IDs in scope for report suspicious activity. |
| state | advancedConfigState | Specifies the state of the reportSuspiciousActivitySettings object. The possible values are: `default`, `enabled`, `disabled`, `unknownFutureValue`. Setting to `default` results in a disabled state. |
| voiceReportingCode | Int32 | Specifies the number the user enters on their phone to report the MFA prompt as suspicious. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.reportSuspiciousActivitySettings",
  "includeTarget": {
    "@odata.type": "microsoft.graph.includeTarget"
  },
  "voiceReportingCode": "Integer",
  "state": "String"
}
```
