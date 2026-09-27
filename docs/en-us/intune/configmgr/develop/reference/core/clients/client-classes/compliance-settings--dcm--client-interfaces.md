<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/compliance-settings--dcm--client-interfaces -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Compliance Settings \(DCM\) Client Interfaces

In Configuration Manager, the desired configuration management COM automation classes and related types are used by client applications to manage configuration items on the client computer. They concern client-side behavior only and are called externally by the Desired Configuration Management Agent, which is enabled by default on the client computer. For more information about the agent, see [Enable or disable the compliance settings agent](https://learn.microsoft.com/en-us/intune/configmgr/develop/compliance/how-to-enable-or-disable-the-compliance-settings--dcm--agent).

Before the Desired Configuration Management Client Agent can call the desired configuration management client COM automation objects in your application, Configuration Manager must send a policy to the client computers for the site. The policy requests desired configuration management components to be enabled. The Desired Configuration Management Client Agent properties are site-wide client settings.

When the policy is received, the Desired Configuration Management Agent can call the COM automation objects in the client application to handle configuration items as needed. For example, the agent calls an [IDCMSDK Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmsdk-interface) object to access and query baseline configuration items.

For more information about developing applications by using the desired configuration management client COM automation classes, see [Configuration Manager Development Environment](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/about-configuration-manager-sdk-requirements).

| Term | Definition |
| --- | --- |
| [ICIINFO Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo-interface) | Represents the properties of a baseline configuration item in a Desired Configuration Management Agent job in the client data store. |
| [IDCMAgentCallback Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmagentcallback-interface) | Represents the callback for the Desired Configuration Management Agent. |
| [IDCMSDK Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmsdk-interface) | Represents the Desired Configuration Management SDK and defines methods that are used to handle baseline configuration items. |
| [CIDetectInfo Structure](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/cidetectinfo-structure) | Contains information for baseline configuration item detection. |
| [CIPackageInfo Structure](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/cipackageinfo-structure) | Contains package information for a configuration item. |
| [CIEvalState Enumeration](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/cievalstate-enumeration) | Defines configuration item evaluation states. |
| [CIJobState Enumeration](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/cijobstate-enumeration) | Defines configuration item agent job states. |
| [CIPresence Enumeration](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/cipresence-enumeration) | Defines configuration item presence types used in the discovery process. |
