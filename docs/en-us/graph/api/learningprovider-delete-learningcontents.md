<!-- Source: https://learn.microsoft.com/en-us/graph/api/learningprovider-delete-learningcontents?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# Delete learningContent

Namespace: microsoft.graph

Delete the specified [learningContent](https://learn.microsoft.com/en-us/graph/api/resources/learningcontent?view=graph-rest-1.0) resource that represents the metadata of the specified provider's ingested content.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | LearningContent.ReadWrite.All | Not available. |

## HTTP request

For a specific learning content based on its ID \(primary key\):

```http
DELETE /employeeExperience/learningProviders/{learningProviderId}/learningContents/{learningContentId}/$ref
```

For a specific learning content based on its external ID \(secondary key\):

```http
DELETE /employeeExperience/learningProviders/{learningProviderId}/learningContents(externalId='{externalId}')/$ref
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Example 1: Delete a learning content resource based on its ID

The following example shows a request that deletes a learning content resource based on its ID \(primary key\).

#### Request

The following example shows the request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
DELETE https://graph.microsoft.com/v1.0/employeeExperience/learningProviders/13727311-e7bb-470d-8b20-6a23d9030d70/learningContents/77029588-a660-46b6-ba58-3ce4d21d5678/$ref
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/employeeExperience/learningProviders/13727311-e7bb-470d-8b20-6a23d9030d70/learningContents/77029588-a660-46b6-ba58-3ce4d21d5678/$ref')
	.delete();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 2: Delete a learning content resource based on its external ID

The following example shows a request that deletes a learning content resource based on its external ID \(secondary key\).

#### Request

The following example shows the request.

```http
DELETE https://graph.microsoft.com/v1.0/employeeExperience/learningProviders/13727311-e7bb-470d-8b20-6a23d9030d70/learningContents(externalId='27rg2ifb28gf28')/$ref
```

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
