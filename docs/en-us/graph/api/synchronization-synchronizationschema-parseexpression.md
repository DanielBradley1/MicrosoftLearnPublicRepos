<!-- Source: https://learn.microsoft.com/en-us/graph/api/synchronization-synchronizationschema-parseexpression?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# synchronizationSchema: parseExpression

Namespace: microsoft.graph

Parse a given string expression into an [attributeMappingSource](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-attributemappingsource?view=graph-rest-1.0) object for a [synchronizationSchema](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationschema?view=graph-rest-1.0).

For more information about expressions, see [Writing Expressions for Attribute Mappings in Microsoft Entra ID](https://learn.microsoft.com/en-us/azure/active-directory/active-directory-saas-writing-expressions-for-attribute-mappings).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Synchronization.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Application.ReadWrite.OwnedBy | Synchronization.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be an owner or member of the group or be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Application Administrator
- Cloud Application Administrator
- Hybrid Identity Administrator - to configure Microsoft Entra Cloud Sync

## HTTP request

```http
POST /servicePrincipals/{id}/synchronization/jobs/{id}/schema/parseExpression
POST /servicePrincipals/{id}/synchronization/templates/{id}/schema/parseExpression
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| expression | String | Expression to parse. |
| testInputObject | [expressionInputObject](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-expressioninputobject?view=graph-rest-1.0) | Test data object to evaluate expression against. Optional. |
| targetAttributeDefinition | [attributeDefinition](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-attributedefinition?view=graph-rest-1.0) | Definition of the attribute that will be mapped to this expression. Optional. |

## Response

If successful, this method returns a `200 OK` response code and a [parseExpressionResponse](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-parseexpressionresponse?view=graph-rest-1.0) object in the response body.

## Example

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/v1.0/servicePrincipals/{id}/synchronization/jobs/{id}/schema/parseExpression
Content-type: application/json

{
    "expression":"Replace([preferredLanguage], \"-\", , , \"_\", ,  )",
    "targetAttributeDefinition":null,
    "testInputObject": {
        definition: null,
        properties:[
            { key: "objectId", value : "66E4A8CC-1B7B-435E-95F8-F06CEA133828" },
            { key: "IsSoftDeleted", value: "false"},
            { key: "accountEnabled", value: "true"},
            { key: "streetAddress", value: "1 Redmond Way"},
            { key: "city", value: "Redmond"},
            { key: "state", value: "WA"},
            { key: "postalCode", value: "98052"},
            { key: "country", value: "USA"},
            { key: "department", value: "Sales"},
            { key: "displayName", value: "John Smith"},
            { key: "extensionAttribute1", value: "Sample 1"},
            { key: "extensionAttribute2", value: "Sample 2"},
            { key: "extensionAttribute3", value: "Sample 3"},
            { key: "extensionAttribute4", value: "Sample 4"},
            { key: "extensionAttribute5", value: "Sample 5"},
            { key: "extensionAttribute6", value: "Sample 6"},
            { key: "extensionAttribute7", value: "Sample 1"},
            { key: "extensionAttribute8", value: "Sample 1"},
            { key: "extensionAttribute9", value: "Sample 1"},
            { key: "extensionAttribute10", value: "Sample 1"},
            { key: "extensionAttribute11", value: "Sample 1"},
            { key: "extensionAttribute12", value: "Sample 1"},
            { key: "extensionAttribute13", value: "Sample 1"},
            { key: "extensionAttribute14", value: "Sample 1"},
            { key: "extensionAttribute15", value: "Sample 1"},
            { key: "givenName", value: "John"},
            { key: "jobTitle", value: "Finance manager"},
            { key: "mail", value: "johns@contoso.com"},
            { key: "mailNickname", value: "johns"},
            { key: "manager", value: "maxs@contoso.com"},
            { key: "mobile", value: "425-555-0010"},
            { key: "onPremisesSecurityIdentifier", value: "66E4A8CC-1B7B-435E-95F8-F06CEA133828"},
            { key: "passwordProfile.password", value: ""},
            { key: "physicalDeliveryOfficeName", value: "Main Office"},
            { key: "preferredLanguage", value: "EN-US"},
            { key: "proxyAddresses", value: ""},
            { key: "surname", value: "Smith"},
            { key: "telephoneNumber", value: "425-555-0011"},
            { key: "userPrincipalName", value: "johns@contoso.com"},
            { key: "appRoleAssignments", "value@odata.type":"#Collection(String)", value: ["Default Assignment"] }
        ]
    }
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const parseExpressionResponse = {
    expression: 'Replace([preferredLanguage], \"-\", , , \"_\", ,  )',
    targetAttributeDefinition: null,
    testInputObject: {
        definition: null,
        properties:[
            { key: 'objectId', value : '66E4A8CC-1B7B-435E-95F8-F06CEA133828' },
            { key: 'IsSoftDeleted', value: 'false'},
            { key: 'accountEnabled', value: 'true'},
            { key: 'streetAddress', value: '1 Redmond Way'},
            { key: 'city', value: 'Redmond'},
            { key: 'state', value: 'WA'},
            { key: 'postalCode', value: '98052'},
            { key: 'country', value: 'USA'},
            { key: 'department', value: 'Sales'},
            { key: 'displayName', value: 'John Smith'},
            { key: 'extensionAttribute1', value: 'Sample 1'},
            { key: 'extensionAttribute2', value: 'Sample 2'},
            { key: 'extensionAttribute3', value: 'Sample 3'},
            { key: 'extensionAttribute4', value: 'Sample 4'},
            { key: 'extensionAttribute5', value: 'Sample 5'},
            { key: 'extensionAttribute6', value: 'Sample 6'},
            { key: 'extensionAttribute7', value: 'Sample 1'},
            { key: 'extensionAttribute8', value: 'Sample 1'},
            { key: 'extensionAttribute9', value: 'Sample 1'},
            { key: 'extensionAttribute10', value: 'Sample 1'},
            { key: 'extensionAttribute11', value: 'Sample 1'},
            { key: 'extensionAttribute12', value: 'Sample 1'},
            { key: 'extensionAttribute13', value: 'Sample 1'},
            { key: 'extensionAttribute14', value: 'Sample 1'},
            { key: 'extensionAttribute15', value: 'Sample 1'},
            { key: 'givenName', value: 'John'},
            { key: 'jobTitle', value: 'Finance manager'},
            { key: 'mail', value: 'johns@contoso.com'},
            { key: 'mailNickname', value: 'johns'},
            { key: 'manager', value: 'maxs@contoso.com'},
            { key: 'mobile', value: '425-555-0010'},
            { key: 'onPremisesSecurityIdentifier', value: '66E4A8CC-1B7B-435E-95F8-F06CEA133828'},
            { key: 'passwordProfile.password', value: ''},
            { key: 'physicalDeliveryOfficeName', value: 'Main Office'},
            { key: 'preferredLanguage', value: 'EN-US'},
            { key: 'proxyAddresses', value: ''},
            { key: 'surname', value: 'Smith'},
            { key: 'telephoneNumber', value: '425-555-0011'},
            { key: 'userPrincipalName', value: 'johns@contoso.com'},
            { key: 'appRoleAssignments', 'value@odata.type':'#Collection(String)', value: ['Default Assignment'] }
        ]
    }
};

await client.api('/servicePrincipals/{id}/synchronization/jobs/{id}/schema/parseExpression')
	.post(parseExpressionResponse);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "error": null,
    "evaluationSucceeded": true,
    "evaluationResult": [
        "EN_US"
    ],
    "parsedExpression": {
        "expression": "Replace([preferredLanguage], \"-\", , , \"_\", , )",
        "name": "Replace",
        "parameters": [
            {
                "key": "source",
                "value": {
                    "expression": "[preferredLanguage]",
                    "name": "preferredLanguage",
                    "parameters": [],
                    "type": "Attribute"
                }
            },
            {
                "key": "Find",
                "value": {
                    "expression": "\"-\"",
                    "name": "-",
                    "parameters": [],
                    "type": "Constant"
                }
            },
            {
                "key": "Replacement",
                "value": {
                    "expression": "\"_\"",
                    "name": "_",
                    "parameters": [],
                    "type": "Constant"
                }
            }
        ],
        "type": "Function"
    },
    "parsingSucceeded": true
}
```
