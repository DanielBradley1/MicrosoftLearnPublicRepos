<!-- Source: https://learn.microsoft.com/en-us/graph/api/authenticationlistener-put?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-06 -->

# Put authenticationListener

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Replace an [authenticationListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationlistener?view=graph-rest-beta) defined for the onSignupStart event in the authentication pipeline.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Policy.ReadWrite.ApplicationConfiguration | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Policy.ReadWrite.ApplicationConfiguration | Not available. |

## HTTP request

```http
PUT /identity/events/onSignupStart/{id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [authenticationListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationlistener?view=graph-rest-beta) object.

The following table lists the properties that are required when you create the [invokeUserFlowListener](https://learn.microsoft.com/en-us/graph/api/resources/invokeuserflowlistener?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| priority | Int32 | The priority of the listener. Determines the order of evaluation when an event has multiple listeners. The priority is evaluated from low to high. |
| sourceFilter | [authenticationSourceFilter](https://learn.microsoft.com/en-us/graph/api/resources/authenticationsourcefilter?view=graph-rest-beta) | Filter based on the source of the authentication that is used to determine whether the listener is evaluated. This is currently limited to evaluations based on application the user is authenticating to. |
| userFlow | [b2xIdentityUserFlow](https://learn.microsoft.com/en-us/graph/api/resources/b2xidentityuserflow?view=graph-rest-beta) | The reference to the user flow object that is invoked in this action. |

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request.

```http
PUT https://graph.microsoft.com/beta/identity/events/onSignupStart/{id}
Content-Type: application/json

{
    "@odata.type": "#Microsoft.Graph.InvokeUserFlowListener",
    "priority": 101,
    "sourceFilter": {
        "includeApplications": [
            "1fc41a76-3050-4529-8095-9af8897cf63d"
        ]
    },
    "userFlow": {
        "id": "B2X_1_Partner"
    }
}
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
