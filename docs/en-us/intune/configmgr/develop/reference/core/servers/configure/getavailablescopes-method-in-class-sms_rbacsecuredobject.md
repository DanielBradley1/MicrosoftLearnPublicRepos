<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/getavailablescopes-method-in-class-sms_rbacsecuredobject -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetAvailableScopes Method in Class SMS\_RbacSecuredObject

The `GetAvailableScopes` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, returns the secured scopes, which current user has the permission to grant to other accounts.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
UInt32 GetAvailableScopes(
     String RoleIDs[],
     UInt32 ScopeTypeID,
     String ScopeIDs[],
     String ScopeNames[]
);
```

#### Parameters

`RoleIDs` Data type: `String` Array

Qualifiers: \[in\]

The role ID list which user uses to grant permissions to other accounts.

`ScopeTypeID` Data type: `UInt32`

Qualifiers: \[in, optional\]

Type of scope, could be RBA security category \(29\) or collection\(1\). The default value is 29.

| Value | Scope type |
| --- | --- |
| 1 | Collection |
| 29 | Secured scope. |

`ScopeIDs` Data type: `String` Array

Qualifiers: \[out\]

IDs of collections for which the user has the specified permissions.

`ScopeNames` Data type: `String` Array

Qualifiers: \[out\]

The name of the scopes.

## Return Values

A `UInt32` data type that is 0 to indicate success or non-zero to indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
