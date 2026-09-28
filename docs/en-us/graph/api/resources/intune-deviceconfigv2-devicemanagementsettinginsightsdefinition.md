<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementsettinginsightsdefinition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementSettingInsightsDefinition resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Setting Insights

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| settingDefinitionId | String | Setting definition id that is being referred to a setting. |
| settingInsight | [deviceManagementConfigurationSettingValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingvalue?view=graph-rest-beta) | Data Insights Target Value |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementSettingInsightsDefinition",
  "settingDefinitionId": "String",
  "settingInsight": {
    "@odata.type": "microsoft.graph.deviceManagementConfigurationGroupSettingValue",
    "settingValueTemplateReference": {
      "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
      "settingValueTemplateId": "String",
      "useTemplateDefault": true
    },
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
                                                                      "settingValueTemplateReference": null,
                                                                      "value": "String",
                                                                      "children": null
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
      }
    ]
  }
}
```
