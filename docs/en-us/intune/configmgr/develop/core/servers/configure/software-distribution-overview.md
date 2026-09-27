<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/software-distribution-overview -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Software Distribution Overview

With this release, Configuration Manager expands the abilities of system administrators to centrally manage computers effectively. Building on the capabilities provided by Configuration Manager 2007, Configuration Manager provides a refined tool set for software distribution.

## Distributing Software

The software distribution process advertises packages, which contain programs, to members of a collection. The client then installs the software from specified distribution points. The order in which you create the components that make up the software distribution process is important.

1. Create an instance of `SMS_Package`.
2. Create an instance of `SMS_Program`.
3. If an existing collection does not identify the users to whom you want to distribute the software, create a new collection by creating an instance of `SMS_Collection`.
4. If the package contains source files, define a distribution point for the package by creating an instance of `SMS_DistributionPoint`.
5. Create an instance of `SMS_Advertisement`.

   The following topics show how to create the software distribution components:

   [How to Create a Package](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-create-a-package)

   [How to Create a Program](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-create-a-program)

   [How to Assign a Package to a Distribution Point](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-assign-a-package-to-a-distribution-point)

   [How to Create an Advertisement](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-create-an-advertisement)

## See Also

[Software distribution overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/software-distribution-overview)
