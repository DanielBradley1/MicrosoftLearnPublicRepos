<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/unrestrictedaudience?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-29 -->

# unrestrictedAudience resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The **unrestrictedAudience** type is used as the **signInAudienceRestrictions** value for an [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-beta) resource to indicate that there are no restrictions on what is allowed by the application's **signInAudience** value.

Inherits from [signInAudienceRestrictionsBase](https://learn.microsoft.com/en-us/graph/api/resources/signinaudiencerestrictionsbase?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| kind | kind | If provided, must be `unrestricted`. Optional. Inherited from [signInAudienceRestrictionsBase](https://learn.microsoft.com/en-us/graph/api/resources/signinaudiencerestrictionsbase?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.unrestrictedAudience",
  "kind": "String"
}
```
