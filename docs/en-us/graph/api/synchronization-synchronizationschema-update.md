<!-- Source: https://learn.microsoft.com/en-us/graph/api/synchronization-synchronizationschema-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# Update synchronizationSchema

Namespace: microsoft.graph

Update the [synchronizationSchema](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationschema?view=graph-rest-1.0) for a given job or template. This method fully replaces the current schema with the one provided in the request. To update the schema of a template, make the call on the application object. You must be the owner of the application.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Synchronization.ReadWrite.All | CustomSecAttributeProvisioning.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Application.ReadWrite.OwnedBy | CustomSecAttributeProvisioning.ReadWrite.All, Synchronization.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be an owner or member of the group or be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Application Administrator
- Cloud Application Administrator
- Hybrid Identity Administrator - to configure Microsoft Entra Cloud Sync

## HTTP Request

```http
PUT /servicePrincipals/{id}/synchronization/jobs/{jobId}/schema
PUT /applications/{id}/synchronization/templates/{templateId}/schema
```

## Request headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | string | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, supply the [synchronizationSchema](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationschema?view=graph-rest-1.0) object to replace the existing schema with.

## Response

If successful, returns a `204 No Content` response code. It doesn't return anything in the response body.

## Examples

### Example 1: Update schema

#### Request

The following example shows a request.

> **Note:** The request object shown here is shortened for readability. Supply all the properties in an actual call.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PUT https://graph.microsoft.com/v1.0/servicePrincipals/{id}/synchronization/jobs/{jobId}/schema
Content-type: application/json

{
    "directories": [
        {
            "name": "Azure Active Directory",
            "objects": [
                {
                    "name": "User",
                    "attributes": [
                        {
                            "name": "userPrincipalName",
                            "type": "string"
                        }
                    ]
                },
            ]
        },
        {
            "name": "Salesforce",
        }
    ],
    "synchronizationRules":[
        {
            "name": "USER_TO_USER",
            "sourceDirectoryName": "Azure Active Directory",
            "targetDirectoryName": "Salesforce",
            "objectMappings": [
                {
                    "sourceObjectName": "User",
                    "targetObjectName": "User",
                    "attributeMappings": [
                        {
                            "source": {},
                            "targetAttributeName": "userName"
                        },
                    ]
                },
            ]
        },
    ]
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const synchronizationSchema = {
    directories: [
        {
            name: 'Azure Active Directory',
            objects: [
                {
                    name: 'User',
                    attributes: [
                        {
                            name: 'userPrincipalName',
                            type: 'string'
                        }
                    ]
                },
            ]
        },
        {
            name: 'Salesforce',
        }
    ],
    synchronizationRules: [
        {
            name: 'USER_TO_USER',
            sourceDirectoryName: 'Azure Active Directory',
            targetDirectoryName: 'Salesforce',
            objectMappings: [
                {
                    sourceObjectName: 'User',
                    targetObjectName: 'User',
                    attributeMappings: [
                        {
                            source: {},
                            targetAttributeName: 'userName'
                        },
                    ]
                },
            ]
        },
    ]
};

await client.api('/servicePrincipals/{id}/synchronization/jobs/{jobId}/schema')
	.put(synchronizationSchema);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 2: Add attribute "CustomAttribute" to the target system schema

#### Request

The following example shows a request. It assumes that the attribute "CustomAttribute" doesn't exist in the target directory schema. If it does exist, the attribute is updated.

> **Note:** The request object shown here is shortened for readability. Supply all the properties in an actual call.

- [HTTP](#tabpanel_2_http)
- [JavaScript](#tabpanel_2_javascript)

```http
PUT https://graph.microsoft.com/v1.0/servicePrincipals/{id}/synchronization/jobs/{jobId}/schema
Content-type: application/json

{
   "directories":[
      {
         "id":"09760868-cafb-47ac-9031-0a3262300427",
         "name":"customappsso",
         "objects":[
            {
               "name":"User",
               "attributes":[
                  {
                     "anchor":false,
                     "caseExact":false,
                     "defaultValue":null,
                     "flowNullValues":false,
                     "multivalued":false,
                     "mutability":"ReadWrite",
                     "name":"urn:ietf:params:scim:schemas:extension:CustomExtensionName:2.0:User:CustomAttribute",
                     "required":false,
                     "type":"String",
                     "apiExpressions":[],
                     "metadata":[],
                     "referencedObjects":[]
                  }
               ]
            }
         ]
      }
   ]
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const synchronizationSchema = {
   directories: [
      {
         id: '09760868-cafb-47ac-9031-0a3262300427',
         name: 'customappsso',
         objects: [
            {
               name: 'User',
               attributes: [
                  {
                     anchor: false,
                     caseExact: false,
                     defaultValue: null,
                     flowNullValues: false,
                     multivalued: false,
                     mutability: 'ReadWrite',
                     name: 'urn:ietf:params:scim:schemas:extension:CustomExtensionName:2.0:User:CustomAttribute',
                     required: false,
                     type: 'String',
                     apiExpressions: [],
                     metadata: [],
                     referencedObjects: []
                  }
               ]
            }
         ]
      }
   ]
};

await client.api('/servicePrincipals/{id}/synchronization/jobs/{jobId}/schema')
	.put(synchronizationSchema);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 3: Add a new attribute mapping to the synchronization rules

#### Request

The following example shows a request. The synchronizationSchema has a one-to-many relationship between **targetAttributeName** and **source** attributes. If your schema doesn't have "timezone" as a target attribute, the service adds a new mapping for extensionAttribute11 --> timezone. If your application has timezone as a target attribute in the schema, the service throws an error because an attribute can only be mapped as a target once. In addition, the attribute must exist in the schema before it can be added to the mappings.

> **Note:** The request object shown here is shortened for readability. Supply all the properties in an actual call.

- [HTTP](#tabpanel_3_http)
- [JavaScript](#tabpanel_3_javascript)

```http
PUT https://graph.microsoft.com/v1.0/servicePrincipals/{id}/synchronization/jobs/{jobId}/schema
Content-type: application/json

{
   "@odata.type":"#microsoft.graph.synchronizationSchema",
   "synchronizationRules":[
      {
         "defaultValue":"",
         "exportMissingReferences":false,
         "flowBehavior":"FlowWhenChanged",
         "flowType":"Always",
         "matchingPriority":0,
         "source":{
            "expression":"[extensionAttribute11]",
            "name":"extensionAttribute11",
            "parameters":[],
            "type":"Attribute"
         },
         "targetAttributeName":"timezone"
      }
   ]
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const synchronizationSchema = {
   '@odata.type':'#microsoft.graph.synchronizationSchema',
   synchronizationRules: [
      {
         defaultValue: '',
         exportMissingReferences: false,
         flowBehavior: 'FlowWhenChanged',
         flowType: 'Always',
         matchingPriority: 0,
         source: {
            expression: '[extensionAttribute11]',
            name: 'extensionAttribute11',
            parameters: [],
            type: 'Attribute'
         },
         targetAttributeName: 'timezone'
      }
   ]
};

await client.api('/servicePrincipals/{id}/synchronization/jobs/{jobId}/schema')
	.put(synchronizationSchema);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
