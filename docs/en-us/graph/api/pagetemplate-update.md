<!-- Source: https://learn.microsoft.com/en-us/graph/api/pagetemplate-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-10-31 -->

# Update pageTemplate

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a [pageTemplate](https://learn.microsoft.com/en-us/graph/api/resources/pagetemplate?view=graph-rest-beta) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Sites.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Sites.ReadWrite.All | Not available. |

## HTTP request

```http
PATCH /sites/{site-id}/pageTemplates/{page-template-id}/microsoft.graph.pageTemplate
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

> **Note:**: You must include `@odata.type=#microsoft.graph.pageTemplate` in the request body. The `@odata.type=#microsoft.graph.pageTemplate` is a property in the HTTP request body for the Microsoft Graph API that specifies the page template type for SharePoint.

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | The description of the page template. Optional. |
| thumbnailWebUrl | String | The URL of the page template's thumbnail image. Optional. |
| title | String | The title of the page template. Optional. |
| titleArea | [titleArea](https://learn.microsoft.com/en-us/graph/api/resources/titlearea?view=graph-rest-beta) | The title area on the page template. Optional. |
| canvasLayout | [canvasLayout](https://learn.microsoft.com/en-us/graph/api/resources/canvaslayout?view=graph-rest-beta) | The layout of the content in a page template, including horizontal sections and vertical section. The content of the entire page layout must be provided, because the update function doesn't support partial updates. Optional. |

## Response

If successful, this method returns a `200 OK` response code and an updated [pageTemplate](https://learn.microsoft.com/en-us/graph/api/resources/pagetemplate?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PATCH https://graph.microsoft.com/beta/sites/dd00d52e-0db7-4d5f-8269-90060ac688d1/pageTemplates/8fbff3f5-0e5d-49e7-89c7-2b042b3bfaa6/microsoft.graph.pageTemplate
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.pageTemplate",
  "title": "sample",
  "showRecommendedPages": false
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const pageTemplate = {
  '@odata.type': '#microsoft.graph.pageTemplate',
  title: 'sample',
  showRecommendedPages: false
};

await client.api('/sites/dd00d52e-0db7-4d5f-8269-90060ac688d1/pageTemplates/8fbff3f5-0e5d-49e7-89c7-2b042b3bfaa6/microsoft.graph.pageTemplate')
	.version('beta')
	.update(pageTemplate);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.pageTemplate",
  "id": "0dd6ddd6-45bd-4acd-b683-de0e6e7231b7",
  "name": "sample.aspx",
  "webUrl": "https://contoso.sharepoint.com/SitePages/Templates/sample.aspx",
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
    "level": "checkout",
    "versionId": "0.1",
    "checkedOutBy": {
      "user": {
        "displayName": "Rahul Mittal",
        "email": "rahmit@contoso.com"
      }
    }
  },
  "titleArea": {
    "enableGradientEffect": true,
    "imageWebUrl": "https://cdn.contoso.osi.office.net/m365content/publish/005292d6-9dcc-4fc5-b50b-b2d0383a411b/image.jpg",
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
