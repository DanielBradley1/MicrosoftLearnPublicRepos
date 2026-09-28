<!-- Source: https://learn.microsoft.com/en-us/graph/api/educationassignmentsettings-put-defaultgradingscheme?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-05 -->

# Add defaultGradingScheme

Namespace: microsoft.graph

Add the default [educationGradingScheme](https://learn.microsoft.com/en-us/graph/api/resources/educationgradingscheme?view=graph-rest-1.0) to an [educationAssignmentSettings](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentsettings?view=graph-rest-1.0) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EduAssignments.ReadWriteBasic | EduAssignments.ReadWrite |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
PUT /education/classes/{educationClassId}/assignmentSettings/defaultGradingScheme/$ref
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of a structure with the OData ID of the existing [educationGradingScheme](https://learn.microsoft.com/en-us/graph/api/resources/educationgradingscheme?view=graph-rest-1.0) to add to this assignment.

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PUT https://graph.microsoft.com/v1.0/education/classes/37d99af7-cfc5-4e3b-8566-f7d40e4a2070/assignmentSettings/defaultGradingScheme/$ref
Content-Type: application/json

{
    "@odata.id": "https://graph.microsoft.com/v1.0/education/classes/37d99af7-cfc5-4e3b-8566-f7d40e4a2070/assignmentSettings/gradingSchemes/69911dea-bc5c-406a-8743-81d06225a3a1"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const educationGradingScheme = {
    '@odata.id': 'https://graph.microsoft.com/v1.0/education/classes/37d99af7-cfc5-4e3b-8566-f7d40e4a2070/assignmentSettings/gradingSchemes/69911dea-bc5c-406a-8743-81d06225a3a1'
};

await client.api('/education/classes/37d99af7-cfc5-4e3b-8566-f7d40e4a2070/assignmentSettings/defaultGradingScheme/$ref')
	.put(educationGradingScheme);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
