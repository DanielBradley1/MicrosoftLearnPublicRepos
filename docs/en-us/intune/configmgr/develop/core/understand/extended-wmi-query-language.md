<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/extended-wmi-query-language -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# Configuration Manager Extended WMI Query Language

Configuration Manager supports a superset of the Windows Management Instrumentation \(WMI\) Query Language \(WQL\) known as Extended WQL. Both WQL and Extended WQL are retrieval-only languages that are used to create queries. Neither language can be used to create, modify, or delete classes or instances.

WQL and Extended WQL are based on the American National Standards Institute \(ANSI\) Structured Query Language \(SQL\) standard. However, they differ from standard SQL in that they retrieve from classes rather than tables and return instances rather than rows.

Extended WQL supports elements from two versions of ANSI SQL:

ANSI-92, which is the recommended version for most operations.

ANSI-89, which is primarily used only for `JOIN` operations by Open Database Connectivity \(ODBC\) applications requiring the services of the WMI ODBC Adapter.

Extended WQL includes a much broader range of operations than WQL. The following list shows the `SELECT` clauses that Extended WQL supports:

`DISTINCT`

`COUNT`

`JOIN`

`WHERE`

`SUBSTRING`

`ORDER BY`

`UPPER, LOWER`, and `DATEPART` functions

Because Extended WQL is fully case-insensitive, the UPPER and LOWER functions are not useful. Extended WQL supports the standard comparison operators \(including LIKE and IN\) and sub queries.

The SMS Provider does not support querying on system properties. System properties are those preceded by a double underscore prefix, for example `__path`.

Association queries are limited to the WQL syntax.

The use of `COUNT` and `DISTINCT` keywords together in a statement is not supported.

in Configuration Manager the `WHERE` clause supports `GetDate()`, `DateDiff()`, `and DateAdd()`.

The `ORDER BY` clause does not work with the collection-limiting context qualifier.

## See Also

[Configuration Manager Association Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/association-classes) [Configuration Manager Bit Field Properties](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-bit-field-properties) [Configuration Manager Date and Time Formats](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/date-and-time-formats) [Configuration Manager Embedded Objects](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/embedded-objects) [Objects overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-objects-overview) [Configuration Manager Lazy Properties](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-lazy-properties) [About errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors) [Configuration Manager Object Security](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-object-security) [Configuration Manager Special Queries](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/special-queries)
