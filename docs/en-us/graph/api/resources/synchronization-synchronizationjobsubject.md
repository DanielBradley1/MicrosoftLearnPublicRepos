<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationjobsubject?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# synchronizationJobSubject resource type

Namespace: microsoft.graph

Represents the objects that will be provisioned during on-demand provisioning.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| links | [synchronizationLinkedObjects](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationlinkedobjects?view=graph-rest-1.0) | Principals that you would like to provision. |
| objectId | String | The identifier of an object to which a **synchronizationJob** is to be applied. Can be one of the following:<br><br><li>An <strong>onPremisesDistinguishedName</strong> for synchronization from Active Directory to Azure AD.</li><br><br><li>The user ID for synchronization from Microsoft Entra ID to a third-party.</li><br><br><li>The Worker ID of the Workday worker for synchronization from Workday to either Active Directory or Microsoft Entra ID.</li> |
| objectTypeName | String | The type of the object to which a **synchronizationJob** is to be applied. Can be one of the following:<br><br><li><code>user</code> for synchronizing between Active Directory and Azure AD.</li><br><br><li><code>User</code> for synchronizing a user between Microsoft Entra ID and a third-party application. </li><br><br><li><code>Worker</code> for synchronization a user between Workday and either Active Directory or Microsoft Entra ID.</li><br><br><li><code>Group</code> for synchronizing a group between Microsoft Entra ID and a third-party application. </li> |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.synchronizationJobSubject",
  "objectId": "String",
  "objectTypeName": "String",
  "links": {
    "@odata.type": "microsoft.graph.synchronizationLinkedObjects"
  }
}
```
