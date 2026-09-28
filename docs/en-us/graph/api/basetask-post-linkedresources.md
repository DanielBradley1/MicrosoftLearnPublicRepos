<!-- Source: https://learn.microsoft.com/en-us/graph/api/basetask-post-linkedresources?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# Create linkedResource\_v2 \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The to-do API set built on [baseTask](https://learn.microsoft.com/en-us/graph/api/resources/basetask?view=graph-rest-beta&preserve-view=true) was deprecated on May 31, 2022, and stopped returning data on August 31, 2022. Use the [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-beta&preserve-view=true) API instead.

Create a new [linkedResource\_v2](https://learn.microsoft.com/en-us/graph/api/resources/linkedresource_v2?view=graph-rest-beta) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Tasks.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Tasks.ReadWrite | Not available. |
| Application | Tasks.ReadWrite | Not available. |

## HTTP request

```http
POST /me/tasks/lists/{baseTaskListId}/tasks/{baseTaskId}/linkedResources
POST /users/{id | userPrincipalName}/tasks/lists/{baseTaskListId}/tasks/{baseTaskId}/linkedResources
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [linkedResource\_v2](https://learn.microsoft.com/en-us/graph/api/resources/linkedresource_v2?view=graph-rest-beta) object.

You can specify the following properties when creating a **linkedResource\_v2**.

| Property | Type | Description |
| :--- | :--- | :--- |
| applicationName | String | Field indicating the app name of the source that is sending the **linkedResource**. |
| displayName | String | Field indicating the title of the **linkedResource**. |
| externalId | String | Id of the object that is associated with this task on the third-party/partner system. |
| webUrl | String | Deep link to the **linkedResource**. |

## Response

If successful, this method returns a `201 Created` response code and a [linkedResource\_v2](https://learn.microsoft.com/en-us/graph/api/resources/linkedresource_v2?view=graph-rest-beta) object in the response body.

## Examples

### Request

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/beta/me/tasks/lists/AAMkADliMmU5YjJlLTVmMmQtNGQzNS1iYjA0LTdmZTA2NTI0MTE5YwAuAAAAAADdOMUbUmCfTKa7OC-fqjkdAQBnu3olF7NfToRyJ2f__TNcAAAAAAESAAA=/tasks/AAkALgAAAAAAHYQDEapmEc2byACqAC-EWg0AZ7t6JRezX06Ecidn-vkzXAABPDii4gAA/linkedResources
Content-Type: application/json

{
    "webUrl": "https://microsoft.com",
    "applicationName": "Microsoft",
    "displayName": "Microsoft",
    "externalId": "dk9cddce2-dce2-f9dd-e2dc-cdf9e2dccdf9"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const linkedResources = {
    webUrl: 'https://microsoft.com',
    applicationName: 'Microsoft',
    displayName: 'Microsoft',
    externalId: 'dk9cddce2-dce2-f9dd-e2dc-cdf9e2dccdf9'
};

await client.api('/me/tasks/lists/AAMkADliMmU5YjJlLTVmMmQtNGQzNS1iYjA0LTdmZTA2NTI0MTE5YwAuAAAAAADdOMUbUmCfTKa7OC-fqjkdAQBnu3olF7NfToRyJ2f__TNcAAAAAAESAAA=/tasks/AAkALgAAAAAAHYQDEapmEc2byACqAC-EWg0AZ7t6JRezX06Ecidn-vkzXAABPDii4gAA/linkedResources')
	.version('beta')
	.post(linkedResources);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#users('6f9a2a92-8527-4d64-937e-b5312852f35d')/tasks/lists('AAMkADliMmU5YjJlLTVmMmQtNGQzNS1iYjA0LTdmZTA2NTI0MTE5YwAuAAAAAADdOMUbUmCfTKa7OC-fqjkdAQBnu3olF7NfToRyJ2f__TNcAAAAAAESAAA%3D')/tasks('AAkALgAAAAAAHYQDEapmEc2byACqAC-EWg0AZ7t6JRezX06Ecidn-vkzXAABPDii4gAA')/linkedResources/$entity",
    "webUrl": "https://microsoft.com",
    "applicationName": "Microsoft",
    "displayName": "Microsoft",
    "externalId": "dk9cddce2-dce2-f9dd-e2dc-cdf9e2dccdf9",
    "id": "e2c5ed75-7aa4-4f8e-84ab-98b5e0b56ee8"
}
```
