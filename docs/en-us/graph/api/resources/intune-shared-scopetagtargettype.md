<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-scopetagtargettype?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# scopeTagTargetType enum type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Specifies which type of Entra object to target in the Group for a given ScopeTag.

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| none | 0 | Unused value. Do not use. |
| user | 1 | Indicates the ScopeTag assignment will Target Users in the Group Ids provided. |
| device | 2 | Indicates the ScopeTag assignment will Target Devices in the Group Ids provided. |
| unknownFutureValue | 4 | Evolvable enumeration sentinel value. Do not use. |
