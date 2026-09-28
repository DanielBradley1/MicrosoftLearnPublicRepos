<!-- Source: https://learn.microsoft.com/en-us/graph/api/termstore-relation-post?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# Create relation

Namespace: microsoft.graph.termStore

Create a new [relation](https://learn.microsoft.com/en-us/graph/api/resources/termstore-relation?view=graph-rest-1.0) object. These are used to create pinned and reused relations between terms or between a term and set. If you create a pinned/reused term between term and set, then **fromTerm** must be set to *null* in the post body.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TermStore.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /sites/{site-id}/termStore/sets/{set-id}/terms/{term-id}/relations
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [relation](https://learn.microsoft.com/en-us/graph/api/resources/termstore-relation?view=graph-rest-1.0) object.

The following table lists the properties that are required when you create the [relation](https://learn.microsoft.com/en-us/graph/api/resources/termstore-relation?view=graph-rest-1.0) object.

| Property | Type | Description |
| :--- | :--- | :--- |
| relationship | microsoft.graph.termStore.relationType | Type of relation to be created. The possible values are: `pin`, `reuse`. |
| set | [microsoft.graph.termStore.set](https://learn.microsoft.com/en-us/graph/api/resources/termstore-set?view=graph-rest-1.0) | The set where the relationship needs to be created. |
| fromTerm | [microsoft.graph.termStore.term](https://learn.microsoft.com/en-us/graph/api/resources/termstore-term?view=graph-rest-1.0) | The term with which the relationship needs to be created. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.termStore.relation](https://learn.microsoft.com/en-us/graph/api/resources/termstore-relation?view=graph-rest-1.0) object in the response body.

## Examples

### Request

```http
POST https://graph.microsoft.com/v1.0/sites/microsoft.sharepoint.com,b9b0bc03-cbc4-40d2-aba9-2c9dd9821ddf,6a742cee-9216-4db5-8046-13a595684e74/termStores/27fd2d26-60d3-485c-9420-0c71f74a0cfd/terms/8861b57a-c777-49e7-826f-47d6afecf80d/relations
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.termStore.relation",
  "relationship": "pin",
  "fromTerm" : {
    "id" : "b49f64b3-4722-4336-9a5c-56c326b344d4"
  },
  "set" : {
    "id": "95e553ae-a91a-4670-a139-67a6cea285b3"
  }
}
```

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.termStore.relation",
  "id": "052c749c-749c-052c-9c74-2c059c742c05",
  "relationship": "pin",
  "fromTerm" : {
      "id" : "b49f64b3-4722-4336-9a5c-56c326b344d4"
  },
  "toTerm" : {
      "id" : "226e8ee3-f4b6-49d7-92d5-ec9d5475eec5"
  },
  "set" : {
      "id" : "95e553ae-a91a-4670-a139-67a6cea285b3"
  }
}
```
