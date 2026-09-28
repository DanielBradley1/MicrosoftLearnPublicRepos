<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/aaduserconversationmemberresult?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# aadUserConversationMemberResult resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the individual response for each member specified in a bulk operation that includes [aadUserConversationMember](https://learn.microsoft.com/en-us/graph/api/resources/aaduserconversationmember?view=graph-rest-beta) objects in the request.

Inherits from [actionResultPart](https://learn.microsoft.com/en-us/graph/api/resources/actionresultpart?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| error | [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-beta) | The error that occurred, if any, during the course of the bulk operation. |
| userId | String | The user object ID of the Microsoft Entra user that was being added as part of the bulk operation. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "error": "microsoft.graph.publicError",
  "userId": "String"
}
```

## Related content

- [Add members in bulk to a team](https://learn.microsoft.com/en-us/graph/api/conversationmembers-add?view=graph-rest-beta)
- [Remove members in bulk from a team](https://learn.microsoft.com/en-us/graph/api/conversationmember-remove?view=graph-rest-beta)
