<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/idlesessionsignout?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# idleSessionSignOut resource type

Namespace: microsoft.graph

Represents the idle session sign-out policy settings for SharePoint.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isEnabled | Boolean | Indicates whether the idle session sign-out policy is enabled. |
| signOutAfterInSeconds | Int64 | Number of seconds of inactivity after which a user is signed out. |
| warnAfterInSeconds | Int64 | Number of seconds of inactivity after which a user is notified that they'll be signed out. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "isEnabled": "Boolean",
    "signOutAfterInSeconds": "Int64",
    "warnAfterInSeconds": "Int64"
}
```
