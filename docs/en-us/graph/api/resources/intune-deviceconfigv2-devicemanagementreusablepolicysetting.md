<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementreusablepolicysetting?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementReusablePolicySetting resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Graph model for a reusable setting

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementReusablePolicySettings](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementreusablepolicysetting-list?view=graph-rest-beta) | [deviceManagementReusablePolicySetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementreusablepolicysetting?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementReusablePolicySetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementreusablepolicysetting?view=graph-rest-beta) objects. |
| [Get deviceManagementReusablePolicySetting](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementreusablepolicysetting-get?view=graph-rest-beta) | [deviceManagementReusablePolicySetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementreusablepolicysetting?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementReusablePolicySetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementreusablepolicysetting?view=graph-rest-beta) object. |
| [Create deviceManagementReusablePolicySetting](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementreusablepolicysetting-create?view=graph-rest-beta) | [deviceManagementReusablePolicySetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementreusablepolicysetting?view=graph-rest-beta) | Create a new [deviceManagementReusablePolicySetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementreusablepolicysetting?view=graph-rest-beta) object. |
| [Delete deviceManagementReusablePolicySetting](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementreusablepolicysetting-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementReusablePolicySetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementreusablepolicysetting?view=graph-rest-beta). |
| [Update deviceManagementReusablePolicySetting](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementreusablepolicysetting-update?view=graph-rest-beta) | [deviceManagementReusablePolicySetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementreusablepolicysetting?view=graph-rest-beta) | Update the properties of a [deviceManagementReusablePolicySetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementreusablepolicysetting?view=graph-rest-beta) object. |
| [clone action](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementreusablepolicysetting-clone?view=graph-rest-beta) | [deviceManagementReusablePolicySetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementreusablepolicysetting?view=graph-rest-beta) |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | system generated reusable setting id. |
| displayName | String | reusable setting display name supplied by user. |
| description | String | reusable setting description supplied by user. |
| settingDefinitionId | String | setting definition id associated with this reusable setting. |
| settingInstance | [deviceManagementConfigurationSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettinginstance?view=graph-rest-beta) | reusable setting configuration instance |
| createdDateTime | DateTimeOffset | reusable setting creation date and time. This property is read-only. |
| lastModifiedDateTime | DateTimeOffset | date and time when reusable setting was last modified. This property is read-only. |
| version | Int32 | version number for reusable setting. Valid values 0 to 2147483647. This property is read-only. |
| referencingConfigurationPolicyCount | Int32 | count of configuration policies referencing the current reusable setting. Valid values 0 to 2147483647. This property is read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| referencingConfigurationPolicies | [deviceManagementConfigurationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicy?view=graph-rest-beta) collection | configuration policies referencing the current reusable setting. This property is read-only. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementReusablePolicySetting",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "settingDefinitionId": "String",
  "settingInstance": {
    "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
    "settingDefinitionId": "String",
    "settingInstanceTemplateReference": {
      "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
      "settingInstanceTemplateId": "String"
    },
    "auditRuleInformation": {
      "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
      "auditType": "String",
      "auditRuleMetadata": {
        "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
        "metadataType": "String",
        "ruleId": "String",
        "ruleName": "String",
        "ruleDescription": "String",
        "ruleVersion": "String",
        "ruleSeverity": "String"
      }
    },
    "choiceSettingValue": {
      "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
      "settingValueTemplateReference": {
        "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
        "settingValueTemplateId": "String",
        "useTemplateDefault": true
      },
      "value": "String",
      "children": [
        {
          "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
          "settingDefinitionId": "String",
          "settingInstanceTemplateReference": {
            "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
            "settingInstanceTemplateId": "String"
          },
          "auditRuleInformation": {
            "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
            "auditType": "String",
            "auditRuleMetadata": {
              "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
              "metadataType": "String",
              "ruleId": "String",
              "ruleName": "String",
              "ruleDescription": "String",
              "ruleVersion": "String",
              "ruleSeverity": "String"
            }
          },
          "choiceSettingValue": {
            "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
            "settingValueTemplateReference": {
              "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
              "settingValueTemplateId": "String",
              "useTemplateDefault": true
            },
            "value": "String",
            "children": [
              {
                "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                "settingDefinitionId": "String",
                "settingInstanceTemplateReference": {
                  "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                  "settingInstanceTemplateId": "String"
                },
                "auditRuleInformation": {
                  "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                  "auditType": "String",
                  "auditRuleMetadata": {
                    "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                    "metadataType": "String",
                    "ruleId": "String",
                    "ruleName": "String",
                    "ruleDescription": "String",
                    "ruleVersion": "String",
                    "ruleSeverity": "String"
                  }
                },
                "choiceSettingValue": {
                  "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                  "settingValueTemplateReference": {
                    "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                    "settingValueTemplateId": "String",
                    "useTemplateDefault": true
                  },
                  "value": "String",
                  "children": [
                    {
                      "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                      "settingDefinitionId": "String",
                      "settingInstanceTemplateReference": {
                        "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                        "settingInstanceTemplateId": "String"
                      },
                      "auditRuleInformation": {
                        "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                        "auditType": "String",
                        "auditRuleMetadata": {
                          "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                          "metadataType": "String",
                          "ruleId": "String",
                          "ruleName": "String",
                          "ruleDescription": "String",
                          "ruleVersion": "String",
                          "ruleSeverity": "String"
                        }
                      },
                      "choiceSettingValue": {
                        "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                        "settingValueTemplateReference": {
                          "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                          "settingValueTemplateId": "String",
                          "useTemplateDefault": true
                        },
                        "value": "String",
                        "children": [
                          {
                            "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                            "settingDefinitionId": "String",
                            "settingInstanceTemplateReference": {
                              "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                              "settingInstanceTemplateId": "String"
                            },
                            "auditRuleInformation": {
                              "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                              "auditType": "String",
                              "auditRuleMetadata": {
                                "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                                "metadataType": "String",
                                "ruleId": "String",
                                "ruleName": "String",
                                "ruleDescription": "String",
                                "ruleVersion": "String",
                                "ruleSeverity": "String"
                              }
                            },
                            "choiceSettingValue": {
                              "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                              "settingValueTemplateReference": {
                                "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                                "settingValueTemplateId": "String",
                                "useTemplateDefault": true
                              },
                              "value": "String",
                              "children": [
                                {
                                  "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                                  "settingDefinitionId": "String",
                                  "settingInstanceTemplateReference": {
                                    "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                                    "settingInstanceTemplateId": "String"
                                  },
                                  "auditRuleInformation": {
                                    "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                                    "auditType": "String",
                                    "auditRuleMetadata": {
                                      "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                                      "metadataType": "String",
                                      "ruleId": "String",
                                      "ruleName": "String",
                                      "ruleDescription": "String",
                                      "ruleVersion": "String",
                                      "ruleSeverity": "String"
                                    }
                                  },
                                  "choiceSettingValue": {
                                    "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                                    "settingValueTemplateReference": {
                                      "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                                      "settingValueTemplateId": "String",
                                      "useTemplateDefault": true
                                    },
                                    "value": "String",
                                    "children": [
                                      {
                                        "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                                        "settingDefinitionId": "String",
                                        "settingInstanceTemplateReference": {
                                          "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                                          "settingInstanceTemplateId": "String"
                                        },
                                        "auditRuleInformation": {
                                          "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                                          "auditType": "String",
                                          "auditRuleMetadata": {
                                            "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                                            "metadataType": "String",
                                            "ruleId": "String",
                                            "ruleName": "String",
                                            "ruleDescription": "String",
                                            "ruleVersion": "String",
                                            "ruleSeverity": "String"
                                          }
                                        },
                                        "choiceSettingValue": {
                                          "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                                          "settingValueTemplateReference": {
                                            "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                                            "settingValueTemplateId": "String",
                                            "useTemplateDefault": true
                                          },
                                          "value": "String",
                                          "children": [
                                            {
                                              "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                                              "settingDefinitionId": "String",
                                              "settingInstanceTemplateReference": {
                                                "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                                                "settingInstanceTemplateId": "String"
                                              },
                                              "auditRuleInformation": {
                                                "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                                                "auditType": "String",
                                                "auditRuleMetadata": {
                                                  "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                                                  "metadataType": "String",
                                                  "ruleId": "String",
                                                  "ruleName": "String",
                                                  "ruleDescription": "String",
                                                  "ruleVersion": "String",
                                                  "ruleSeverity": "String"
                                                }
                                              },
                                              "choiceSettingValue": {
                                                "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                                                "settingValueTemplateReference": {
                                                  "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                                                  "settingValueTemplateId": "String",
                                                  "useTemplateDefault": true
                                                },
                                                "value": "String",
                                                "children": [
                                                  {
                                                    "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                                                    "settingDefinitionId": "String",
                                                    "settingInstanceTemplateReference": {
                                                      "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                                                      "settingInstanceTemplateId": "String"
                                                    },
                                                    "auditRuleInformation": {
                                                      "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                                                      "auditType": "String",
                                                      "auditRuleMetadata": {
                                                        "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                                                        "metadataType": "String",
                                                        "ruleId": "String",
                                                        "ruleName": "String",
                                                        "ruleDescription": "String",
                                                        "ruleVersion": "String",
                                                        "ruleSeverity": "String"
                                                      }
                                                    },
                                                    "choiceSettingValue": {
                                                      "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                                                      "settingValueTemplateReference": {
                                                        "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                                                        "settingValueTemplateId": "String",
                                                        "useTemplateDefault": true
                                                      },
                                                      "value": "String",
                                                      "children": [
                                                        {
                                                          "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                                                          "settingDefinitionId": "String",
                                                          "settingInstanceTemplateReference": {
                                                            "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                                                            "settingInstanceTemplateId": "String"
                                                          },
                                                          "auditRuleInformation": {
                                                            "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                                                            "auditType": "String",
                                                            "auditRuleMetadata": {
                                                              "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                                                              "metadataType": "String",
                                                              "ruleId": "String",
                                                              "ruleName": "String",
                                                              "ruleDescription": "String",
                                                              "ruleVersion": "String",
                                                              "ruleSeverity": "String"
                                                            }
                                                          },
                                                          "choiceSettingValue": {
                                                            "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                                                            "settingValueTemplateReference": {
                                                              "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                                                              "settingValueTemplateId": "String",
                                                              "useTemplateDefault": true
                                                            },
                                                            "value": "String",
                                                            "children": [
                                                              {
                                                                "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                                                                "settingDefinitionId": "String",
                                                                "settingInstanceTemplateReference": {
                                                                  "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                                                                  "settingInstanceTemplateId": "String"
                                                                },
                                                                "auditRuleInformation": {
                                                                  "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                                                                  "auditType": "String",
                                                                  "auditRuleMetadata": {
                                                                    "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                                                                    "metadataType": "String",
                                                                    "ruleId": "String",
                                                                    "ruleName": "String",
                                                                    "ruleDescription": "String",
                                                                    "ruleVersion": "String",
                                                                    "ruleSeverity": "String"
                                                                  }
                                                                },
                                                                "choiceSettingValue": {
                                                                  "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                                                                  "settingValueTemplateReference": {
                                                                    "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                                                                    "settingValueTemplateId": "String",
                                                                    "useTemplateDefault": true
                                                                  },
                                                                  "value": "String",
                                                                  "children": [
                                                                    {
                                                                      "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                                                                      "settingDefinitionId": null,
                                                                      "settingInstanceTemplateReference": null,
                                                                      "auditRuleInformation": null,
                                                                      "choiceSettingValue": null
                                                                    }
                                                                  ]
                                                                }
                                                              }
                                                            ]
                                                          }
                                                        }
                                                      ]
                                                    }
                                                  }
                                                ]
                                              }
                                            }
                                          ]
                                        }
                                      }
                                    ]
                                  }
                                }
                              ]
                            }
                          }
                        ]
                      }
                    }
                  ]
                }
              }
            ]
          }
        }
      ]
    }
  },
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "version": 1024,
  "referencingConfigurationPolicyCount": 1024
}
```
