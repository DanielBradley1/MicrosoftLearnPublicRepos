<!-- Source: https://learn.microsoft.com/en-us/graph/api/sitepage-create-webpart?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# Create webPart

Namespace: microsoft.graph

Create a new [webPart](https://learn.microsoft.com/en-us/graph/api/resources/webpart?view=graph-rest-1.0) at a specified position in the [sitePage](https://learn.microsoft.com/en-us/graph/api/resources/sitepage?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Sites.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Sites.ReadWrite.All | Not available. |

## HTTP request

```http
POST /sites/{site-id}/pages/{page-id}/microsoft.graph.sitePage/canvasLayout/verticalSection/webparts
POST /sites/{site-id}/pages/{page-id}/microsoft.graph.sitePage/canvasLayout/horizontalSections/{horizontal-section-id}/columns/{horizontal-section-column-id}/webparts
```

## Optional query parameters

| Name | Description |
| :--- | :--- |
| index | The position at which the web part should be inserted in the collection of web parts |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [textWebPart](https://learn.microsoft.com/en-us/graph/api/resources/textwebpart?view=graph-rest-1.0) or [standardWebPart](https://learn.microsoft.com/en-us/graph/api/resources/standardwebpart?view=graph-rest-1.0).

To ensure successful parsing of the request body, the `@odata.type=#microsoft.graph.textwebpart` or `@odata.type=#microsoft.graph.standardwebpart` must be included in the request body.

### Supported web parts

There are two kinds of web parts that can be added to a [sitePage](https://learn.microsoft.com/en-us/graph/api/resources/sitepage?view=graph-rest-1.0): [standardWebPart](https://learn.microsoft.com/en-us/graph/api/resources/standardwebpart?view=graph-rest-1.0) and [textWebPart](https://learn.microsoft.com/en-us/graph/api/resources/textwebpart?view=graph-rest-1.0).

For [standardWebPart](https://learn.microsoft.com/en-us/graph/api/resources/standardwebpart?view=graph-rest-1.0), only the following are supported when updating using the Microsoft Graph API. Attempting to add unsupported web parts will result in a failure or exception.

| # | Web Part | Type |
| --- | --- | --- |
| 1 | Bing Maps | `e377ea37-9047-43b9-8cdb-a761be2f8e09` |
| 2 | Button | `0f087d7f-520e-42b7-89c0-496aaf979d58` |
| 3 | Call To Action | `df8e44e7-edd5-46d5-90da-aca1539313b8` |
| 4 | Divider | `2161a1c6-db61-4731-b97c-3cdb303f7cbb` |
| 5 | Document Embed | `b7dd04e1-19ce-4b24-9132-b60a1c2b910d` |
| 6 | Image | `d1d91016-032f-456d-98a4-721247c305e8` |
| 7 | Image Gallery | `af8be689-990e-492a-81f7-ba3e4cd3ed9c` |
| 8 | Link Preview | `6410b3b6-d440-4663-8744-378976dc041e` |
| 9 | Org Chart | `e84a8ca2-f63c-4fb9-bc0b-d8eef5ccb22b` |
| 10 | People | `7f718435-ee4d-431c-bdbf-9c4ff326f46e` |
| 11 | Quick Links | `c70391ea-0b10-4ee9-b2b4-006d3fcad0cd` |
| 12 | Spacer | `8654b779-4886-46d4-8ffb-b5ed960ee986` |
| 13 | Youtube Embed | `544dd15b-cf3c-441b-96da-004d5a8cea1d` |
| 14 | Title Area | `cbe7b0a9-3504-44dd-a3a3-0e5cacd07788` |

## Response

If successful, this method returns a `201` and the created [webPart](https://learn.microsoft.com/en-us/graph/api/resources/webpart?view=graph-rest-1.0) object in the response body.

## Example

### Request

The following example shows how to create a new webpart.

```http
POST /sites/7f50f45e-714a-4264-9c59-3bf43ea4db8f/pages/df69e386-6c58-4df2-afc0-ab6327d5b202//microsoft.graph.sitePage/canvasLayout/verticalSection/webparts
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.textWebPart",
  "innerHtml": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus blandit pellentesque ipsum tempor porta. Phasellus tincidunt et ipsum nec iaculis. Sed eu arcu tristique, congue erat a, consequat lorem. Suspendisse ac ullamcorper elit. Sed ultricies, risus sed hendrerit dictum, nunc massa ornare velit, a pharetra dolor urna quis lorem. Maecenas eget pellentesque purus, nec ultricies risus. Donec rhoncus lorem at euismod varius. Donec auctor sed mi vitae pharetra. Aenean id tempor mauris. Donec dui nulla, semper ut elit id, mattis commodo arcu. Aliquam erat volutpat."
}
```

---

### Response

If successful, this method returns a [webPart](https://learn.microsoft.com/en-us/graph/api/resources/webpart?view=graph-rest-1.0) in the response body for the created webPart.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "@odata.type": "#microsoft.graph.textWebPart",
  "id": "51053496-e6f3-4161-94ac-07bdf4d92226",
  "innerHtml": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus blandit pellentesque ipsum tempor porta. Phasellus tincidunt et ipsum nec iaculis. Sed eu arcu tristique, congue erat a, consequat lorem. Suspendisse ac ullamcorper elit. Sed ultricies, risus sed hendrerit dictum, nunc massa ornare velit, a pharetra dolor urna quis lorem. Maecenas eget pellentesque purus, nec ultricies risus. Donec rhoncus lorem at euismod varius. Donec auctor sed mi vitae pharetra. Aenean id tempor mauris. Donec dui nulla, semper ut elit id, mattis commodo arcu. Aliquam erat volutpat."
}
```
