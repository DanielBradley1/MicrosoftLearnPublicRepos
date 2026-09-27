<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-and-write-to-the-site-control-file-by-using-managed-code -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# How to Read and Write to the Configuration Manager Site Control File by Using Managed Code

To write to the Configuration Manager site control file by using the managed SMS Provider, you get the site definition file by querying for the required resource or component. You then update the embedded property, embedded property list, or multi-string list as required.

Note

You can also use connection manager [GetInstance](https://learn.microsoft.com/en-us/previous-versions/system-center/developer/cc146190\(v=msdn.10\)) to get the required resource or component.

The managed Configuration Manager manages the connection session to the site control file automatically for you. Therefore you treat the [IResultObject](https://learn.microsoft.com/en-us/previous-versions/system-center/developer/cc147376\(v=msdn.10\)) objects returned from the query in the same way as you treat [IResultObject](https://learn.microsoft.com/en-us/previous-versions/system-center/developer/cc147376\(v=msdn.10\)) objects retrieved from the SMS Provider.

### To read and write to the site control file

1. Set up a connection to the SMS Provider. For more information, see [How to Connect to an SMS Provider in Configuration Manager by Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-by-using-managed-code).
2. Use the Connection Manager **QueryProcessor** object *ExecQuery* or *GetInstance* method to get the required site control file resource or component [IResultObject](https://learn.microsoft.com/en-us/previous-versions/system-center/developer/cc147376\(v=msdn.10\)) object.
3. Using the [IResultObject](https://learn.microsoft.com/en-us/previous-versions/system-center/developer/cc147376\(v=msdn.10\)) update the site control file.
4. Use the [IResultObject](https://learn.microsoft.com/en-us/previous-versions/system-center/developer/cc147376\(v=msdn.10\)) object [Put](https://learn.microsoft.com/en-us/previous-versions/system-center/developer/cc146500\(v=msdn.10\)) method to commit the changes.

## Example

The following C# example accesses the client agent component of the site control file and creates a dummy property, property list and multi-string list. It then removes the updates that were made. The example demonstrates how to query the site control file, make updates, and commit changes to the site control file.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```
public void ReadWriteSCF(WqlConnectionManager connection,string siteCode)
{
    try
    {

    // Query for the site's site control file client agent settings.
    IResultObject resources =
    connection.QueryProcessor.ExecuteQuery
    ("SELECT * FROM SMS_SCI_ClientComp WHERE ClientComponentName = 'Client Agent' AND SiteCode = '" +
    siteCode + "'");

    foreach (IResultObject resource in resources)
    {
            // Embedded Properties

            Console.WriteLine("Embedded property");
            Console.WriteLine("-----------------");

            int value = 0;
            string value1 = "";
            string value2 = "";

            // Write a dummy embedded property.
            this.WriteScfEmbeddedProperty(resource, "Test", 10, "Hello", "World");

            // Get the embedded property back and display the values.
            if (this.GetScfEmbeddedProperty(resource, "Test", ref value, ref value1, ref value2))
            {
                Console.WriteLine("Value: " + value);
                Console.WriteLine("Value1: " + value1);
                Console.WriteLine("Value2: " + value2);

                // Remove the dummy embedded property.
                Dictionary<string, IResultObject> EmbeddedProperties = resource.EmbeddedProperties;
                EmbeddedProperties.Remove("Test");
                resource.EmbeddedProperties = EmbeddedProperties;
                resource.Put();

                // See if the dummy embedded property is still there.
                if (this.GetScfEmbeddedProperty(resource, "Test", ref value, ref value1, ref value2))
                {
                    Console.WriteLine("Test exists");
                }
                else
                {
                    Console.WriteLine("Test does not exist");
                }
            }
            else
            {
                Console.WriteLine("Property not found");
            }

            Console.WriteLine();

            // Embedded property list.

            Console.WriteLine("Embedded property list");
            Console.WriteLine("----------------------");

            // values contains the embedded property list.
            ArrayList values = new ArrayList();

            values.Add("Elephant");
            values.Add("Giraffe");

            // Write to the resource.
            this.WriteScfEmbeddedPropertyList(resource, "Animals", values);

            ArrayList retrievedValues;

            // Get the embedded property list and display.
            if (this.GetScfEmbeddedPropertyList(resource, "Animals", out retrievedValues))
            {
                foreach (string retrievedValue in retrievedValues)
                {
                    Console.WriteLine(retrievedValue);
                }

                // Remove one of the entries.
                retrievedValues.Remove("Elephant");
                Console.WriteLine();

                // Update the list.
                this.WriteScfEmbeddedPropertyList(resource, "Animals", retrievedValues);

                // Display the list again.
                this.GetScfEmbeddedPropertyList(resource, "Animals", out retrievedValues);
                foreach (string retrievedValue in retrievedValues)
                {
                    Console.WriteLine(retrievedValue);
                }

            }
            else
            {
                Console.WriteLine("None");
            }

            Console.WriteLine();

            // RegMultiStringList.

            Console.WriteLine("RegMultiStringList");
            Console.WriteLine("------------------");

            // valuesStrings is the RegMultiString List.
            ArrayList valueStrings = new ArrayList();

            valueStrings.Add("Tom");
            valueStrings.Add("Harry");

            this.WriteScfRegMultiStringList(resource, "Names", valueStrings);

            ArrayList retrievedValuesStrings;

            if (this.GetScfRegMultiStringList(resource, "Names", out retrievedValuesStrings))
            {
                foreach (string retrievedValue in retrievedValuesStrings)
                {
                    Console.WriteLine(retrievedValue);
                }

                // Remove one of the entries.
                retrievedValuesStrings.Remove("Tom");
                Console.WriteLine();

                // Update the list.
                this.WriteScfRegMultiStringList(resource, "Names", retrievedValuesStrings);

                // Display the list again.
                this.GetScfRegMultiStringList(resource, "Names", out retrievedValuesStrings);
                foreach (string retrievedValue in retrievedValuesStrings)
                {
                    Console.WriteLine(retrievedValue);
                }
            }
            else
            {
                Console.WriteLine("None");
            }
        }
    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed: " + e.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - `WqlConnectionManager` | A valid connection to the SMS Provider. |
| `siteCode` | - `String` | The site code for the Configuration Manager site. |

## Compiling the Code

### Namespaces

System

System.Collections.Generic

System.Collections

System.ComponentModel

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

microsoft.configurationmanagement.managementprovider

adminui.wqlqueryengine

## Robust Programming

The Configuration Manager exceptions that can be raised are [SmsConnectionException](https://learn.microsoft.com/en-us/previous-versions/system-center/developer/cc147431\(v=msdn.10\)) and [SmsQueryException](https://learn.microsoft.com/en-us/previous-versions/system-center/developer/cc147436\(v=msdn.10\)). These can be caught together with [SmsException](https://learn.microsoft.com/en-us/previous-versions/system-center/developer/cc147433\(v=msdn.10\)).

## See Also

[SMS Provider fundamentals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-fundamentals) [About the Configuration Manager Site Control File](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-the-configuration-manager-site-control-file) [How to Connect to a Configuration Manager Provider using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-by-using-managed-code) [How to Read a Configuration Manager Site Control File Embedded Property List](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-a-configuration-manager-site-control-file-embedded-property-list) [Objects overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-objects-overview)
