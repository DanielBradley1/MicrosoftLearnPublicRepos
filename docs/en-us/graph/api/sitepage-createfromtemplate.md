<!-- Source: https://learn.microsoft.com/en-us/graph/api/sitepage-createfromtemplate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-05 -->

# sitePage: createFromTemplate

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [sitePage](https://learn.microsoft.com/en-us/graph/api/resources/sitepage?view=graph-rest-beta) from a [pageTemplate](https://learn.microsoft.com/en-us/graph/api/resources/pagetemplate?view=graph-rest-beta) in a [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-beta).

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Sites.ReadWrite.All | Sites.FullControl.All, Sites.Manage.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Sites.ReadWrite.All | Sites.FullControl.All, Sites.Manage.All |

## HTTP request

```http
POST /sites/{site-id}/pages/createFromTemplate
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [crateFromPageTemplateRequest](https://learn.microsoft.com/en-us/graph/api/resources/createfromtemplate?view=graph-rest-beta) to use in the request payload.

## Response

If successful, this method returns a `201 Created` and the created [sitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta) object.

## Example

The following example shows how to create a new page from the page template.

### Request

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/beta/sites/dd00d52e-0db7-4d5f-8269-90060ac688d1/pages/sitePage/createFromTemplate
Content-Type: application/json

{
    "title": "Sample",
    "name": "Sample.aspx",
    "templateId": "f6ed8c43-9923-4c6c-ba09-9c32b8f10aeb"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const createFromTemplate = {
    title: 'Sample',
    name: 'Sample.aspx',
    templateId: 'f6ed8c43-9923-4c6c-ba09-9c32b8f10aeb'
};

await client.api('/sites/dd00d52e-0db7-4d5f-8269-90060ac688d1/pages/sitePage/createFromTemplate')
	.version('beta')
	.post(createFromTemplate);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.type": "microsoft.graph.sitePage",
    "id": "0dd6ddd6-45bd-4acd-b683-de0e6e7231b7",
    "name": "Sample.aspx",
    "webUrl": "https://contoso.sharepoint.com/SitePages/Sample.aspx",
    "title": "Sample",
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
        "imageSourceType": 2
    }
}
```
