<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-field-length-restrictions -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS Provider Field Length Restrictions

The SMS Provider places restrictions on the width of character fields for schema classes. If you write a program that writes to these classes, you should take these field widths into account. Where they are used in the user interface, the SMS online Help provides the maximum character widths. You can also determine the width by dividing the corresponding schema class table column width by two to give the field width in characters.

You can determine the schema class table column width from the corresponding SQL Server views. For information about mapping schema classes to SQL Server views, see SMS Schema View Mapping. The steps for obtaining the table column width from the SQL Server view in SQL Server are:

- Open the SQL Server view's properties to see which table and table columns it uses.
- Open the corresponding table in the database Tables view to discover the column width.

  Classes that are commonly affected by this restriction are:
- SMS\_Package
- SMS\_Advertisement
- SMS\_Program
- SMS\_DistributionPoint
- SMS\_PDF\_Package
- SMS\_PDF\_Program
- SMS\_Query
- SMS\_Report
- SMS\_ReportDashboard
- SMS\_ReportViewSchema
- SMS\_CollectionRuleQuery
- SMS\_Collection
- SMS\_UserInstancePermissions
- SMS\_UserClassPermissions
- SMS\_UserInstancePermissionNames
- SMS\_UserClassPermissionNames
