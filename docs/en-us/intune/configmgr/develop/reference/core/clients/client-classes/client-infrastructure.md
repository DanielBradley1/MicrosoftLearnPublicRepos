<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/client-infrastructure -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Configuration Manager Client Infrastructure

This section provides reference information for the Configuration Manager client infrastructure, including Control Panel, client framework and data transfer, and policy functionality.

## In This Section

Client Control Panel COM Automation

Important

The Client Control Panel COM Automation interface has been removed or deprecated in Configuration Manager SP1. Use the feature-related client WMI class instead.

[Client Framework and Data Transfer Client WMI Classes](#client-framework-and-data-transfer-client-wmi-classes) describes the Client Configuration Manager \(CCM\) framework and data transfer classes in Configuration Manager for the client.

[Policy Agent Client WMI Classes](#policy-agent-client-wmi-classes) describes the classes used to manage policy on client computers and devices.

## Client Framework and Data Transfer Client WMI Classes

The following framework and data transfer classes are used in Configuration Manager for the client.

[CCM\_Messaging\_Configuration Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_messaging_configuration-client-wmi-class) Supports messaging-related settings that are exposed to administrators.

[CCM\_Service\_BITSConfiguration Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_service_bitsconfiguration-client-wmi-class) Supports Background Intelligent Transfer Service \(BITS\)-related settings used by CCMEXEC for uploading and downloading message payloads.

[CCM\_Service\_EndpointConfiguration Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_service_endpointconfiguration-client-wmi-class) Supports endpoint configuration for the CCMEXEC service.

[CCM\_Service\_GlobalConfiguration Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_service_globalconfiguration-client-wmi-class) Supports global configuration for the CCMEXEC service.

[CCM\_Service\_HostedClass Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_service_hostedclass-client-wmi-class) Configures a COM class to be hosted in the CCMEXEC service.

[CCM\_Service\_IISConfiguration Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_service_iisconfiguration-client-wmi-class) Supports Internet Information Services \(IIS\)-related settings used by CCMEXEC for staging and receiving message payloads.

[CCM\_Service\_SystemTaskConfiguration Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_service_systemtaskconfiguration-client-wmi-class) Supports system task configuration for the CCMEXEC service.

[SMS\_Authority Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_authority-client-wmi-class) Represents the client authority that manages the client.

[SMS\_Client Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_client-client-wmi-class) Represents the client and facilitates manipulation and retrieval of client information.

[SMS\_LocalMP Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_localmp-client-wmi-class) Represents the local management point.

[SMS\_MPProxyInformation Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_mpproxyinformation-client-wmi-class) Represents information about a proxy management point.

[SMS\_PendingReRegistrationOnSiteReAssignment Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_pendingreregistrationonsitereassignment-client-wmi-class) Represents a pending re-registration at the time of site reassignment.

## Policy Agent Client WMI Classes

The following classes are used to manage policy on client computers and devices.

[CCM\_Policy Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy-client-wmi-class) Represents a client policy.

[CCM\_Policy\_Action Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_action-client-wmi-class) Represents settings for a policy action.

[CCM\_Policy\_ActionHandlerRegistration Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_actionhandlerregistration-client-wmi-class) Represents an action handler registration for a policy.

[CCM\_Policy\_Assignment Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_assignment-client-wmi-class) Represents a policy assignment.

[CCM\_Policy\_Assignment2 Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_assignment2-client-wmi-class) Represents a policy assignment.

[CCM\_Policy\_AuthorityData Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_authoritydata-client-wmi-class) Stores information about policy from a particular authority.

[CCM\_Policy\_Condition Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_condition-client-wmi-class) Represents a policy condition.

[CCM\_Policy\_Config Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_config-client-wmi-class) Represents a policy configuration used by the Policy Agent that needs to be replicated.

[CCM\_Policy\_EmbeddedObject Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_embeddedobject-client-wmi-class) Represents a policy setting embedded object.

[CCM\_Policy\_Expression Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_expression-client-wmi-class) Represents a policy expression that evaluates to either `true` or `false`.

[CCM\_Policy\_ExpressionHandlerRegistration Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_expressionhandlerregistration-client-wmi-class) Describes a registered expression handler for a policy.

[CCM\_Policy\_Operator Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_operator-client-wmi-class) Stores a compound expression that evaluates to either `true` or `false`.

[CCM\_Policy\_Policy Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_policy-client-wmi-class) Defines a policy object for a client policy.

[CCM\_Policy\_Rule Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_rule-client-wmi-class) Defines a policy object rule.

[CCM\_PolicyAgent\_Configuration Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policyagent_configuration-client-wmi-class) Represents the Policy Agent configuration for a given authority.

## See Also

[Configuration Manager Reference](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/configuration-manager-reference)
