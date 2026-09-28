<!-- Source: https://learn.microsoft.com/en-us/graph/api/accessreviewinstance-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-16 -->

# Update accessReviewInstance

Namespace: microsoft.graph

Update the properties of an [accessReviewInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstance?view=graph-rest-1.0) object. Only the **reviewers** and **fallbackReviewers** properties can be updated but the **scope** property is also required in the request body. You can only add reviewers to the **fallbackReviewers** property but can't remove existing **fallbackReviewers**.

To update an **accessReviewInstance**, it's **status** must be `InProgress`.

Note

Updating an **accessReviewInstance** will update only that instance. The parent **accessReviewScheduleDefinition** and any future **accessReviewInstance** objects won't change. To make updates that apply to all future instances, update the parent [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AccessReview.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AccessReview.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- To write access reviews of a group or app: *User Administrator*, *Identity Governance Administrator*
- To write access reviews of a Microsoft Entra role: *Identity Governance Administrator*, *Privileged Role Administrator*

## HTTP request

```http
PUT /identityGovernance/accessReviews/definitions/{accessReviewScheduleDefinitionId}/instances/{accessReviewInstanceId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| fallbackReviewers | [accessReviewReviewerScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewreviewerscope?view=graph-rest-1.0) collection | This collection of reviewer scopes is used to define the list of fallback reviewers. These fallback reviewers will be notified to take action if no users are found from the list of reviewers specified. This could occur when either the group owner is specified as the reviewer but the group owner doesn't exist, or manager is specified as reviewer but a user's manager doesn't exist. Optional. Updatable. |
| reviewers | [accessReviewReviewerScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewreviewerscope?view=graph-rest-1.0) collection | This collection of access review scopes is used to define who the reviewers are. For examples of options for assigning reviewers, see [Assign reviewers to your access review definition using the Microsoft Graph API](https://learn.microsoft.com/en-us/graph/accessreviews-scope-concept). Optional. Updatable. |
| scope | [accessReviewScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscope?view=graph-rest-1.0) | Created based on **scope** and **instanceEnumerationScope** at the [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) level. Defines the scope of users reviewed in a group. Read-only. Required but not updated. |

## Response

If successful, this method returns a `200 OK` response code and an updated [accessReviewInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstance?view=graph-rest-1.0) object in the response body.

Attempting to remove existing **fallbackReviewers** returns a `409 Conflict` response code.

## Examples

### Request

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```msgraph
PUT https://graph.microsoft.com/v1.0/identityGovernance/accessReviews/definitions/5dcfcc88-da88-4252-8629-a0807b4b076d/instances/720b8ee0-cee4-42ac-b164-894c48703acc
Content-Type: application/json

{
    "scope": {
        "@odata.type": "#microsoft.graph.principalResourceMembershipsScope",
        "principalScopes": [
            {
                "@odata.type": "#microsoft.graph.accessReviewQueryScope",
                "query": "/v1.0/users",
                "queryType": "MicrosoftGraph"
            },
            {
                "@odata.type": "#microsoft.graph.accessReviewQueryScope",
                "query": "/v1.0/groups",
                "queryType": "MicrosoftGraph"
            }
        ],
        "resourceScopes": [
            {
                "@odata.type": "#microsoft.graph.accessReviewQueryScope",
                "query": "/v1.0/roleManagement/directory/roleDefinitions/9b895d92-2cd3-44c7-9d02-a6ac2d5ea5c3",
                "queryType": "MicrosoftGraph"
            }
        ]
    },
    "reviewers": [
        {
            "query": "/users/1ed8ac56-4827-4733-8f80-86adc2e67db5",
            "queryType": "MicrosoftGraph"
        }
    ],
    "fallbackReviewers": [
        {
            "query": "/users/4562bcc8-c436-4f95-b7c0-4f8ce89dca5e",
            "queryType": "MicrosoftGraph"
        },
        {
            "query": "/users/1ed8ac56-4827-4733-8f80-86adc2e67db5",
            "queryType": "MicrosoftGraph"
        }
    ]
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessReviewInstance = {
    scope: {
        '@odata.type': '#microsoft.graph.principalResourceMembershipsScope',
        principalScopes: [
            {
                '@odata.type': '#microsoft.graph.accessReviewQueryScope',
                query: '/v1.0/users',
                queryType: 'MicrosoftGraph'
            },
            {
                '@odata.type': '#microsoft.graph.accessReviewQueryScope',
                query: '/v1.0/groups',
                queryType: 'MicrosoftGraph'
            }
        ],
        resourceScopes: [
            {
                '@odata.type': '#microsoft.graph.accessReviewQueryScope',
                query: '/v1.0/roleManagement/directory/roleDefinitions/9b895d92-2cd3-44c7-9d02-a6ac2d5ea5c3',
                queryType: 'MicrosoftGraph'
            }
        ]
    },
    reviewers: [
        {
            query: '/users/1ed8ac56-4827-4733-8f80-86adc2e67db5',
            queryType: 'MicrosoftGraph'
        }
    ],
    fallbackReviewers: [
        {
            query: '/users/4562bcc8-c436-4f95-b7c0-4f8ce89dca5e',
            queryType: 'MicrosoftGraph'
        },
        {
            query: '/users/1ed8ac56-4827-4733-8f80-86adc2e67db5',
            queryType: 'MicrosoftGraph'
        }
    ]
};

await client.api('/identityGovernance/accessReviews/definitions/5dcfcc88-da88-4252-8629-a0807b4b076d/instances/720b8ee0-cee4-42ac-b164-894c48703acc')
	.put(accessReviewInstance);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/accessReviews/definitions('5dcfcc88-da88-4252-8629-a0807b4b076d')/instances/$entity",
    "id": "720b8ee0-cee4-42ac-b164-894c48703acc",
    "startDateTime": "2021-12-14T11:15:43.207Z",
    "endDateTime": "2021-12-15T11:15:43.207Z",
    "status": "InProgress",
    "scope": {
        "@odata.type": "#microsoft.graph.principalResourceMembershipsScope",
        "principalScopes": [
            {
                "@odata.type": "#microsoft.graph.accessReviewQueryScope",
                "query": "/v1.0/users",
                "queryType": "MicrosoftGraph",
                "queryRoot": null
            },
            {
                "@odata.type": "#microsoft.graph.accessReviewQueryScope",
                "query": "/v1.0/groups",
                "queryType": "MicrosoftGraph",
                "queryRoot": null
            }
        ],
        "resourceScopes": [
            {
                "@odata.type": "#microsoft.graph.accessReviewQueryScope",
                "query": "/v1.0/roleManagement/directory/roleDefinitions/9b895d92-2cd3-44c7-9d02-a6ac2d5ea5c3",
                "queryType": "MicrosoftGraph",
                "queryRoot": null
            }
        ]
    },
    "reviewers": [
        {
            "query": "/v1.0/users/4562bcc8-c436-4f95-b7c0-4f8ce89dca5e",
            "queryType": "MicrosoftGraph",
            "queryRoot": null
        }
    ],
    "fallbackReviewers": [
        {
            "query": "/v1.0/users/4562bcc8-c436-4f95-b7c0-4f8ce89dca5e",
            "queryType": "MicrosoftGraph",
            "queryRoot": null
        },
        {
            "query": "/v1.0/users/1ed8ac56-4827-4733-8f80-86adc2e67db5",
            "queryType": "MicrosoftGraph",
            "queryRoot": null
        }
    ]
}
```
