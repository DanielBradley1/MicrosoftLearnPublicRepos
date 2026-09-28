<!-- Source: https://learn.microsoft.com/en-us/graph/api/sitepage-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-11 -->

# Update sitePage

Namespace: microsoft.graph

Update the properties of a [sitePage](https://learn.microsoft.com/en-us/graph/api/resources/sitepage?view=graph-rest-1.0) object.

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
PATCH /sites/{site-id}/pages/{page-id}/microsoft.graph.sitePage
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

These fields and be used in update requests.

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Description of the site page. Optional. |
| thumbnailWebUrl | String | Url of the site page's thumbnail image. Optional. |
| title | String | Title of the site page. Optional. |
| showComments | Boolean | Boolean to determine whether or not to show comments at the bottom of the page. Optional. |
| showRecommendedPages | Boolean | Boolean to determine whether or not to show recommended pages at the bottom of the page. Optional. |
| promotionKind | [PagePromotionType](https://learn.microsoft.com/en-us/graph/api/resources/sitepage?view=graph-rest-1.0#pagepromotiontype-values) | Promotion kind of the SharePoint page. Optional. Only support promote a page \(e.g from `page` to `newsPost`\). Demote is not supported. |
| titleArea | [titleArea](https://learn.microsoft.com/en-us/graph/api/resources/titlearea?view=graph-rest-1.0) | Title area on the site page. Optional. |
| canvasLayout | [canvasLayout](https://learn.microsoft.com/en-us/graph/api/resources/canvaslayout?view=graph-rest-1.0) | The layout of the content in a page, including horizontal sections and vertical section. A content of the entire page layout needs to be provided, the update function doesn't support partial updates. Optional. |

> **Notes:** :
> 
> 1. To ensure successful parsing of the request body, the `@odata.type=#microsoft.graph.sitePage` must be included in the request body.
> 2. If you're using the response from the [Get sitepage](https://learn.microsoft.com/en-us/graph/api/sitepage-get?view=graph-rest-1.0) operation to update a **sitePage**, we recommend that you add the HTTP header `Accept: application/json;odata.metadata=none`. This will remove all OData metadata from the response. You can also manually remove all OData metadata.
> 3. Only the web part listed in the [Supported web parts](#supported-web-parts) section are supported when updating a [sitePage](https://learn.microsoft.com/en-us/graph/api/resources/sitepage?view=graph-rest-1.0) using the Microsoft Graph API. Attempting to add unsupported web parts will result in a failure or exception.

### Supported web parts

There are two kinds of web parts that can be added to a [sitePage](https://learn.microsoft.com/en-us/graph/api/resources/sitepage?view=graph-rest-1.0): [standardWebParts](https://learn.microsoft.com/en-us/graph/api/resources/standardwebpart?view=graph-rest-1.0) and [textWebPart](https://learn.microsoft.com/en-us/graph/api/resources/textwebpart?view=graph-rest-1.0). The following table lists the supported web parts for standard web parts.

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

If successful, this method returns a `200 OK` response code and an updated [sitePage](https://learn.microsoft.com/en-us/graph/api/resources/sitepage?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following is an example of a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PATCH https://graph.microsoft.com/v1.0/sites/7f50f45e-714a-4264-9c59-3bf43ea4db8f/pages/df69e386-6c58-4df2-afc0-ab6327d5b202/microsoft.graph.sitePage
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.sitePage",
  "title": "sample",
  "showComments": true,
  "showRecommendedPages": false
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const sitePage = {
  '@odata.type': '#microsoft.graph.sitePage',
  title: 'sample',
  showComments: true,
  showRecommendedPages: false
};

await client.api('/sites/7f50f45e-714a-4264-9c59-3bf43ea4db8f/pages/df69e386-6c58-4df2-afc0-ab6327d5b202/microsoft.graph.sitePage')
	.update(sitePage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.sitePage",
  "id": "0dd6ddd6-45bd-4acd-b683-de0e6e7231b7",
  "name": "sample.aspx",
  "webUrl": "https://contoso.sharepoint.com/SitePages/sample.aspx",
  "title": "sample",
  "pageLayout": "article",
  "showComments": true,
  "showRecommendedPages": false,
  "createdBy": {
    "user": {
      "displayName": "Rahul Mittal",
      "email": "rahmit@contoso.com"
    }
  },
  "lastModifiedBy": {
    "user": {
      "displayName": "Rahul Mittal",
      "email": "rahmit@contoso.com"
    }
  },
  "publishingState": {
    "level": "draft",
    "versionId": "0.1"
  },
  "titleArea": {
    "enableGradientEffect": true,
    "imageWebUrl": "https://cdn.hubblecontent.osi.office.net/m365content/publish/005292d6-9dcc-4fc5-b50b-b2d0383a411b/image.jpg",
    "layout": "colorBlock",
    "showAuthor": true,
    "showPublishedDate": false,
    "showTextBlockAboveTitle": false,
    "textAboveTitle": "TEXT ABOVE TITLE",
    "textAlignment": "left",
    "title": "sample",
    "imageSourceType": 2
  }
}
```
