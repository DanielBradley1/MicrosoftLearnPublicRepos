<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/resource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# oneNoteResource resource type

Namespace: microsoft.graph

An image or other file resource on a OneNote page.

You can get the binary data of a resource, but getting a JSON representation of a resource object or a resource collection is not supported.

```json
{
  "content": { "@odata.type": "Edm.Stream" },
  "contentUrl": "string (url)"
}
```

Get the binary data of a specific resource by sending a GET request to the resource's `content` endpoint:

```
GET ../onenote/resources/{id}/content
```

The file's resource URI is returned when you get a page's HTML content using the following request:

```
GET ../onenote/pages/{id}/content
```

In the page HTML, an `img` tag includes endpoints for the original image resource in the `data-fullres-src` attribute and the optimized image in the `src` attribute:

```
<img
    src="image-resource-url"
    data-src-type="media-type"
    data-fullres-src="image-resource-url"
    data-fullres-src-type="media-type" ... />
```

An `object` tag \(which represents files such as PDF, DOCX, and PNG\) includes the endpoint for the file resource in the `data` attribute:

```
<object
    data="file-resource-url"
    data-attachment="file-name.file-type"
    type="media-type" ... />
```

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| content | Stream | The content stream |
| contentUrl | String \(url\) | The URL for downloading the content |

## Relationships

None.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get resource](https://learn.microsoft.com/en-us/graph/api/resource-get?view=graph-rest-1.0) | Stream | Retrieve the binary data of a file or image resource. |
