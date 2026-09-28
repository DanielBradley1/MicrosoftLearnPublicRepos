<!-- Source: https://learn.microsoft.com/en-us/entra/identity/app-provisioning/expression-builder -->
<!-- Sitemap-Last-Modified: 2026-08-06 -->

# Understand how expression builder in Application Provisioning works

You can use [expressions](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/functions-for-customizing-application-data) to [map attributes](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes). Previously, you had to create these expressions manually and enter them into the expression box. Expression builder is a tool you can use to help you create expressions.

[![The default expression builder page before selecting a function.](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/media/expression-builder/expression-builder.png)](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/media/expression-builder/expression-builder.png#lightbox)

For reference on building expressions, see [Reference for writing expressions for attribute mappings](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/functions-for-customizing-application-data).

## Finding the expression builder

In application provisioning, you use expressions for attribute mappings. You access Expression Builder on the attribute mapping page by selecting the **Expression builder** from the left navigation menu.

## Using expression builder

To use expression builder, select a function and attribute and then enter a suffix if needed. Then select **Add expression** to add the expression to the code box. To learn more about the functions available and how to use them, see [Reference for writing expressions for attribute mappings](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/functions-for-customizing-application-data).

Test the expression by providing values and selecting **Test expression**. For example, from the dropdown list, select the **mail** attribute. Fill in the value with the email domain that starts with the @ sign; for example, `@fabrikam.com`. Then select **Test expression** and the output of the expression test appears in the **View expression output** box.

When you're satisfied with the expression, move it to an attribute mapping. Copy and paste it into the expression box for the attribute mapping you're working on.

## Known limitations

- Extension attributes aren't available for selection in the expression builder. However, extension attributes can be used in the attribute mapping expression.
- The maximum supported length for a single attribute mapping expression is **10,000 characters**.

## Next steps

[Reference for writing expressions for attribute mappings](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/functions-for-customizing-application-data)
