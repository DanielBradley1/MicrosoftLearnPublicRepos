<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/planneruserids?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-01 -->

# plannerUserIds resource type

Namespace: microsoft.graph

The **plannerUserIds** resource represents the list of users IDs that a [plan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-1.0) is shared with, and is an Open Type. If you're using Microsoft 365 groups, use the Groups API to manage group membership to share the [group's](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) plan. You can also add existing members of the group to this collection though it isn't required for them to access the plan owned by the group.

## Properties

The client defines the properties of an Open Type, and the client should provide user IDs as properties with their values being the `true` Boolean. When user IDs are no longer shared with, properties are automatically removed by setting their values to the `false` Boolean.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "String-value": true
}
```

### Example

```json
{
  "400723e1-102b-43aa-aba9-f35524827084": true, // property name is user id
  "f117339e-c914-4a9c-9b66-1c062b027556": true,
  "e886d105-23b9-47e2-bde1-757e75ee4a28": true
}
```
