<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-bit-field-properties -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# Configuration Manager Bit Field Properties

Some Configuration Manager object properties are implemented as bit fields, where individual binary bits of an integer \(usually a `uint32` data type\) are used as `Boolean` flags to store information. These properties can be difficult to interpret at the user interface because the bit field is often displayed as a decimal number.

For example, the Security User Class Permissions object \(`SMS_UserClassPermissions`\) contains an integer property called `ClassPermissions`, which is defined as an `int32` data type with the following bit flags:

| Bit | Value |
| --- | --- |
| 0 | READ |
| 1 | MODIFY |
| 2 | DELETE |
| 3 | DISTRIBUTE |
| 4 | CREATE\_CHILD |
| 5 | REMOTE\_CONTROL |
| 6 | ADVERTISE |
| 7 | MODIFY\_RESOURCE |
| 8 | ADMINISTER |
| 9 | DELETE\_RESOURCE |
| 10 | CREATE |
| 11 | VIEW\_COLL\_FILE |
| 12 | READ\_RESOURCE |
| 13 | DELEGATE |
| 14 | METER |
| 15 | MANAGESQLCOMMAND |
| 16 | MANAGESTATUSFILTER |

A typical value of this bit field might be 10100000111. Bit 0 is the least significant bit \(on the right\) and the other bits are counted right to left. Therefore, in this example, the available class permissions include READ, MODIFY, DELETE, ADMINISTER, and CREATE, corresponding to bit fields 0, 1, 2, 8, and 10, respectively.

The difficulty arises when the binary number 10100000111 appears as the decimal number 1287 in a Configuration Manager console display and in how you interpret the bits. The solution is to open the Windows Calculator application \(Calc.exe, in the Accessories group\). Use the Scientific view, set the calculator for decimal mode, and enter 1287. Use the radio buttons of the calculator to convert to a binary display. The binary bit field 10100000111 appears. You can read the selected bit flags from this display.

Note

In a typical bit field property, many of the bits are unused and have no defined meaning.

## See Also

[Configuration Manager Association Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/association-classes) [Configuration Manager Date and Time Formats](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/date-and-time-formats) [Configuration Manager Embedded Objects](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/embedded-objects) [Configuration Manager Extended WMI Query Language](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/extended-wmi-query-language) [Objects overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-objects-overview) [Configuration Manager Lazy Properties](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-lazy-properties) [About errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors) [Configuration Manager Object Security](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-object-security) [Configuration Manager Special Queries](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/special-queries)
