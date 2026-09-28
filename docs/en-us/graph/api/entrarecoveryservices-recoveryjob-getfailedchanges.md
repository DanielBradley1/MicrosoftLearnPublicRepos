<!-- Source: https://learn.microsoft.com/en-us/graph/api/entrarecoveryservices-recoveryjob-getfailedchanges?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-19 -->

# recoveryJob: getFailedChanges

Namespace: microsoft.graph.entraRecoveryServices

Get a paginated collection of [recoveryChangeObjectBase](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoverychangeobjectbase?view=graph-rest-1.0) objects that failed to apply during the recovery operation.

This method can only be called on a recovery job that has completed and has a **totalFailedChanges** value greater than 0. Each failed change includes a **failureMessage** property describing why the change could not be applied.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EntraBackup.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | EntraBackup.Read.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Entra Backup Reader
- Entra Backup Administrator

## HTTP request

```http
GET /directory/recovery/snapshots/{snapshot-id}/recoveryJobs/{job-id}/microsoft.graph.entraRecoveryServices.getFailedChanges
```

## Function parameters

Don't supply a function parameter for this method.

## Optional query parameters

This method supports the `$top`, `$skip`, and `$select` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters). The default and maximum page sizes are 100 and 999 failed change objects respectively.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a collection of [microsoft.graph.entraRecoveryServices.recoveryChangeObjectBase](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoverychangeobjectbase?view=graph-rest-1.0) objects in the response body. Each object includes a **failureMessage** property describing the error.

## Examples

### Example 1: Get failed changes from a completed recovery job

The following example shows a request to retrieve changes that failed to apply during recovery.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
GET https://graph.microsoft.com/v1.0/directory/recovery/snapshots/MjAyNC0wOC0yNlQwMjozMDowMFo=/recoveryJobs/3f4a6b60-7c1e-4e7c-9c7b-13f8d44b20c4/microsoft.graph.entraRecoveryServices.getFailedChanges
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let getFailedChanges = await client.api('/directory/recovery/snapshots/MjAyNC0wOC0yNlQwMjozMDowMFo=/recoveryJobs/3f4a6b60-7c1e-4e7c-9c7b-13f8d44b20c4/microsoft.graph.entraRecoveryServices.getFailedChanges')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#directory/recovery/snapshots/MjAyNC0wOC0yNlQwMjozMDowMFo=/recoveryJobs/d3f8e7e8-7e87-4a7f-9d2c-c1c2d7e8e1f1/microsoft.graph.entraRecoveryServices.getFailedChanges",
    "@odata.nextLink": "https://graph.microsoft.com/v1.0/directory/recovery/snapshots/MjAyNC0wOC0yNlQwMjozMDowMFo=/recoveryJobs/d3f8e7e8-7e87-4a7f-9d2c-c1c2d7e8e1f1/microsoft.graph.entraRecoveryServices.getFailedChanges?$skiptoken=RFNwdAIAAQAAACA6X1NNVFBfYnJhemlsc291dGhAbWl",
    "value":
      [
        {
            "entityTypeName": "user",
            "id": "36e07e06-72c1-4b2c-b547-c5084413b88b",
            "displayName": "JD",
            "recoveryAction": "update",
            "deltaFromCurrent":
            {
                "@odata.type": "#microsoft.graph.user",
                "displayName": "John Doe",
                "userPrincipalName": "johndoe@example.com",
                "mail": "johndoe@example.com",
                "jobTitle": "Software Engineer",
                "department": "Engineering",
                "officeLocation": "Redmond",
                "mobilePhone": "+1 555-555-5555",
                "businessPhones": [
                "+1 555-555-5555"
                ],
                "preferredLanguage": "en-US",
                "accountEnabled": true,
                "passwordProfile": {
                "forceChangePasswordNextSignIn": false
                }
            },
            "currentState":
            {
                "@odata.type": "#microsoft.graph.user",
                "displayName": "JD",
                "userPrincipalName": "johndoe@example2.com",
                "mail": "jdoe@example.com",
                "jobTitle": "Product Manager",
                "department": "Management",
                "officeLocation": "San Fransisco",
                "mobilePhone": "+1 999-999-9999",
                "businessPhones": [
                "+1 555-888-5555"
                ],
                "preferredLanguage": "en-SP",
                "accountEnabled": false,
                "passwordProfile": {
                "forceChangePasswordNextSignIn": true
                }
            }
        }
      ]
}
```

### Example 2: Get failed changes with top parameter

The following example shows a request using the `$top` query parameter to limit results.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [JavaScript](#tabpanel_2_javascript)

```http
GET https://graph.microsoft.com/v1.0/directory/recovery/snapshots/MjAyNC0wOC0yNlQwMjozMDowMFo=/recoveryJobs/3f4a6b60-7c1e-4e7c-9c7b-13f8d44b20c4/microsoft.graph.entraRecoveryServices.getFailedChanges?$top=1
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let getFailedChanges = await client.api('/directory/recovery/snapshots/MjAyNC0wOC0yNlQwMjozMDowMFo=/recoveryJobs/3f4a6b60-7c1e-4e7c-9c7b-13f8d44b20c4/microsoft.graph.entraRecoveryServices.getFailedChanges')
	.top(1)
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(microsoft.graph.entraRecoveryServices.recoveryChangeObjectBase)",
  "@odata.count": 5,
  "value": [
    {
      "@odata.type": "#microsoft.graph.entraRecoveryServices.recoveryChangeObjectBase",
      "id": "9c4f2e1d-7a3b-4f8e-9c2d-3e4f5a6b7c8d",
      "entityTypeName": "servicePrincipal",
      "recoveryAction": "update",
      "deltaFromCurrent": {
        "appRoleAssignmentRequired": false
      },
      "currentState": {
        "appRoleAssignmentRequired": true
      },
      "failureMessage": "Update failed: Service principal is managed by another service."
    }
  ],
  "@odata.nextLink": "https://graph.microsoft.com/v1.0/directory/recovery/snapshots/MjAyNC0wOC0yNlQwMjozMDowMFo=/recoveryJobs/3f4a6b60-7c1e-4e7c-9c7b-13f8d44b20c4/microsoft.graph.entraRecoveryServices.getFailedChanges?$skip=1&$top=1"
}
```
