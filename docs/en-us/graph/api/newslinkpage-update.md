<!-- Source: https://learn.microsoft.com/en-us/graph/api/newslinkpage-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-04 -->

# Update newsLinkPage

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a [newsLinkPage](https://learn.microsoft.com/en-us/graph/api/resources/newslinkpage?view=graph-rest-beta) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Sites.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Sites.ReadWrite.All | Not available. |

## HTTP request

```http
PATCH /sites/{site-id}/pages/{pageId}/microsoft.graph.newsLinkPage
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json for JSON content, including the required **title** property in multipart requests. Multipart requests use the multipart/form-data; boundary=your-boundary content type. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | The descriptive text for the item. The maximum length limit is 250 characters. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta). |
| newsWebUrl | String | The URL of the news article referenced by the **newsLinkPage**. It can be an external link. |
| title | String | Title of the **newsLinkPage**. The maximum length limit is 110 characters. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta). |

> **Notes:** You can update the **bannerImage** property by uploading the image bytes of the new banner image you want to set. The banner image is autosaved in the site assets library, and the banner image URL is then generated based on the persisted file. Make a multipart request and set the `@microsoft.graph.bannerImageWebUrlContent` annotation to send the image content, as shown in the example.

## Response

If successful, this method returns a `200 OK` response code and an updated [newsLinkPage](https://learn.microsoft.com/en-us/graph/api/resources/newslinkpage?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/beta/sites/c1370818-f5e0-4a40-a99b-be4520640642/pages/637c601e-0d0e-43c0-b50f-b18513bb9de2/microsoft.graph.newsLinkPage
Content-type: multipart/form-data; boundary=MyPartBoundary198374

--MyPartBoundary198374
Content-Disposition:form-data; name="metadata"
Content-Type: application/json

{
  "title": "External News | Microsoft Build brings AI tools to the forefront for developers",
  "@microsoft.graph.bannerImageWebUrlContent" : "name:content"
}

--MyPartBoundary198374
Content-Disposition:form-data; name="content"
Content-Type: image/jpeg

... binary file data ...

--MyPartBoundary198374--
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.newsLinkPage",
  "createdDateTime": "2024-06-11T17:31:20Z",
  "description": " You only need two simple letters to accurately convey the major shift in the technology space this year: A and I. Beyond those letters, however, is a complex, evolving and exciting way in which we work, communicate and collaborate.",
  "eTag": "\"{179210C2-637E-4C61-8491-331D0D4A0C05},2\"",
  "id": "179210c2-637e-4c61-8491-331d0d4a0c05",
  "lastModifiedDateTime": "2024-06-11T17:31:21Z",
  "name": "microsoft-build-ai-tools-developers.aspx",
  "webUrl": "https://contoso.sharepoint.com/SitePages/Microsoft-Build-brings-AI-tools-to-the-forefront-for-developers.aspx",
  "title": "External News | Microsoft Build brings AI tools to the forefront for developers",
  "pageLayout": "newsLink",
  "bannerImageWebUrl": "https://contoso.sharepoint.com/_layouts/15/getpreview.ashx?path=/SiteAssets/SitePages/microsoft-build-ai-tools-developers/BannerImage.png",
  "newsWebUrl": "https://someexternalnewssite.com/2024/05/23/microsoft-build-ai-tools-developers",
  "createdBy": {
    "user": {
      "displayName": "John Doe",
      "email": "jdoe@contoso.com"
    }
  },
  "lastModifiedBy": {
    "user": {
      "displayName": "John Doe",
      "email": "jdoe@contoso.com"
    }
  },
  "publishingState": {
    "level": "checkout",
    "versionId": "0.1",
    "checkedOutBy": {
      "user": {
        "displayName": "John Doe",
        "email": "jdoe@contoso.com"
      }
    }
  }
}
```
