<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-lazy-properties -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# Configuration Manager Lazy Properties

Some Configuration Manager object properties are relatively inefficient to retrieve. If these properties were retrieved for many instances in a class \(as might be done in a query\), the response would be considerably delayed. Such properties are considered lazy properties and are not usually retrieved during query operations. However, if these properties are retrieved during a query, they have `null` or zero values, which might not be the actual value of the property for every instance. Therefore, if you want to get the correct value for lazy properties, you must get each instance individually.

## See Also

[How to Read Lazy Properties Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-lazy-properties-by-using-managed-code) [How to Read Lazy Properties Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-lazy-properties-by-using-wmi)
