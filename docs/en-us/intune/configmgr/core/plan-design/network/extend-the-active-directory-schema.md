<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/network/extend-the-active-directory-schema -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Prepare Active Directory for site publishing

*Applies to: Configuration Manager \(current branch\)*

When you extend the Active Directory schema for Configuration Manager, you introduce new structures to Active Directory. Configuration Manager sites use these new structures to publish key information in a secure location where clients can easily access it.

When you manage on-premises clients, you should extend the Active Directory schema for Configuration Manager. An extended schema can simplify the process of deploying and setting up clients. An extended schema also lets clients efficiently locate resources like content servers. Extending the schema is a one-time action for any forest.

If you're not familiar with the benefits of an extended schema for Configuration Manager, see [Schema extensions for Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/network/schema-extensions).

When you don't use an extended schema, you can set up other methods like DNS to locate services and site system servers. These methods of service location require other configurations and aren't the preferred method for service location by clients. For more information, see [Understand how clients find site resources and services for Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services).

If your Active Directory schema was extended for Configuration Manager 2007 or System Center 2012 Configuration Manager, then you don't need to do more. The schema extensions are unchanged and are already in place.

## Step 1: Extend the schema

To extend the schema for Configuration Manager:

- Use an account that's a member of the **Schema Admins** security group.
- Sign in with that account to the schema master domain controller.

Then use one of the following options to add the new classes and attributes to the Active Directory schema.

### Option A: Use the extadsch.exe tool

This tool is in the **SMSSETUP\\BIN\\X64** folder on the Configuration Manager installation media.

1. Open a command line, and run **extadsch.exe**.

   Tip

   Run this tool from a command line to view feedback while it runs.
2. To verify that the schema extension was successful, review **extadsch.log** in the root of the system drive.

### Option B: Use the LDIF file

This file is in the **SMSSETUP\\BIN\\X64** folder on the Configuration Manager installation media.

1. Make a copy of the **ConfigMgr\_ad\_schema.ldf** file. Edit it in Notepad, and define the Active Directory root domain that you want to extend. Replace all instances of the text `DC=x` in the file with the full name of the domain to extend. For example, if the full name of the domain to extend is named **widgets.contoso.com**, change all instances of `DC=x` in the file to `DC=widgets, DC=contoso, DC=com`.
2. Use the **LDIFDE** command-line utility to import the contents of the **ConfigMgr\_ad\_schema.ldf** file to Active Directory Domain Services. For example, the following command-line imports the schema extensions, turns on verbose logging, and creates a log file in the temp directory:

   `ldifde -i -f ConfigMgr_ad_schema.ldf -v -j "%temp%"`

   For more information, see [Command-line reference: Ldifde](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/cc731033\(v=ws.11\)).
3. To verify that the schema extension was successful, review the ldifde log file.

## Step 2: The System Management container

After you extend the schema, create a container named **System Management** in Active Directory Domain Services. Create this container once in each domain that has a Configuration site that will publish data to Active Directory. For each container, you need to grant permissions to the computer account of each site server that will publish data to that domain.

1. Use an account that has the **Create All Child Objects** permission on the **System** container in Active Directory Domain Services.
2. Run **ADSI Edit** \(adsiedit.msc\), and connect to the site server's domain.
3. Create the container:

   1. Expand the fully qualified domain name, and expand the distinguished name. Right-click **CN=System**, choose **New**, and then select **Object**.
   2. In the **Create Object** window, select **Container**, and then select **Next**.
   3. In the **Value** box, enter `System Management`, and then select **Next**.

4. Assign permissions:

   Note

   If you prefer, you can use other tools like the Active Directory Users and Computers administrative tool \(dsa.msc\) to add permissions to the container.

   1. Right-click **CN=System Management**, and select **Properties**.
   2. Switch to the **Security** tab. Select **Add**, and then add the site server's computer account with the **Full Control** permission.

      Add the computer account for each Configuration Manager site server in this domain. If you use [site server high availability](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/site-server-high-availability), make sure to include the computer account of the site server in passive mode.
   3. Select **Advanced**, select the site server's computer account, and then select **Edit**.
   4. In the **Apply onto** list, select **This object and all descendant objects**.
   5. Select **OK** to save the configuration.

## Next steps

After you create the container and grant permissions, configure the Configuration Manager site to publish data to Active Directory.

[Publish site data for Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/publish-site-data)
