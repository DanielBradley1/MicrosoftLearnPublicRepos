<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationjobrestartcriteria?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# synchronizationJobRestartCriteria resource type

Namespace: microsoft.graph

Defines the scope of the [synchronizationJob: restart](https://learn.microsoft.com/en-us/graph/api/synchronization-synchronizationjob-restart?view=graph-rest-1.0) action.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| resetScope | synchronizationJobRestartScope | Comma-separated combination of the following values: `None`, `ConnectorDataStore`, `Escrows`, `Watermark`, `QuarantineState`, `Full`, `ForceDeletes`. The property can also be empty.  <br><br><br>1. `None`: Starts a paused or quarantined provisioning job. **DO NOT USE.** Use the [Start synchronizationJob](https://learn.microsoft.com/en-us/graph/api/synchronization-synchronizationjob-start?view=graph-rest-1.0) API instead.<br>2. `ConnectorDataStore` - Clears the underlying cache for all users. **DO NOT USE. Contact Microsoft Support for guidance.**<br>3. `Escrows` - Provisioning failures are marked as escrows and retried. Clearing escrows will stop the service from retrying failures.<br>4. `Watermark` - Removing the watermark causes the service to reevaluate all the users again, rather than just processing changes.<br>5. `QuarantineState` - Temporarily lifts the quarantine.<br>6. Use `Full` if you want all of the options.<br>7. `ForceDeletes` - Forces the system to delete the pending deleted users when using the accidental deletions prevention feature and the deletion threshold is exceeded.<br><br>Leaving this property empty emulates the **Restart provisioning** option in the Microsoft Entra admin center. It is similar to setting the **resetScope** to include `QuarantineState`, `Watermark`, and `Escrows`. This option meets most customer needs. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "resetScope": "String"
}
```
