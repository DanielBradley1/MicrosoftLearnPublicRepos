<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/documentprocessing/solution-manage-contracts-step3?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2025-08-04 -->

# Step 3. Use Power Automate to create the flow to process your contracts

You've created your Contract Management channel and have attached your SharePoint document library. The next step is to create a Power Automate flow to process your contracts that your document processing model identifies and classifies. You can do this step by [creating a Power Automate flow in your SharePoint document library](https://support.microsoft.com/office/create-a-flow-for-a-list-or-library-in-sharepoint-or-onedrive-a9c3e03b-0654-46af-a254-20252e580d01).

For your contracts management solution, you want to create a Power Automate flow to do the following actions:

- After a contract has been classified by your model, change the contract status to **In review**.
- The contract is then reviewed and is either approved or rejected.
- For approved contracts, the contract information is posted to a tab for payment processing.
- For rejected contracts, the team is notified for further analysis.

The following diagram shows the Power Automate flow for the contract management solution.

![Flow diagram showing the entire solution.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/flow-entire-process.png?view=o365-worldwide)

## Prepare your contract for review

When a contract is identified and classified by your unstructured document processing model, the Power Automate flow will first change the status to **In review**.

![Update status.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/flow-overview.png?view=o365-worldwide)

After checking out the file, change the status value to **In review**.

![In review status.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/in-review.png?view=o365-worldwide)

The next step is to create an adaptive card stating that the contract is waiting for review and posting it to the Contract Management channel.

![Contract review post.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/contract-approval-post.png?view=o365-worldwide)

![Create adaptive card for review.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/adaptive-card.png?view=o365-worldwide)

The following code is the JSON used for this step in the Power Automate flow.

```JSON
{
"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
"type": "AdaptiveCard",
"version": "1.0",
"body": [
    {
    "type": "TextBlock",
    "text": "Contract approval request",
    "size": "large",
    "weight": "bolder",
     "wrap": true
    },
        {
            "type": "Container",
            "items": [
                {
                    "type": "FactSet",
                    "spacing": "Large",
                    "facts": [
                        {
                            "title": "Client",
                            "value": "@{triggerOutputs()?['body/Client']}"
                        },
                        {
                            "title": "Contractor",
                            "value": "@{triggerOutputs()?['body/Contractor']}"
                        },
                        {
                            "title": "Fee amount",
                            "value": "@{triggerOutputs()?['body/FeeAmount']}"
                        },
                        {
                            "title": "Date created",
                            "value": "@{triggerOutputs()?['body/Modified']} "
                        },
                        {
                            "title": "Link",
                            "value": "[@{triggerOutputs()?['body/{FilenameWithExtension}']}](@{triggerOutputs()?['body/{Link}']})"
                        }
                    ]
                }
            ]
         },
    {
    "type": "TextBlock",
    "text": "Comment:"
    },
        {
            "type": "Input.Text",
            "placeholder": "Enter comments",
            "id": "acComments"
        }
],
"actions": [
    {
    "type": "Action.Submit",
    "title": "Approve",
    "data": {
        "x": "Approve"
    }
    },
    {
    "type": "Action.Submit",
    "title": "Reject",
    "data": {
        "x": "Reject"
    }
    }
]
}
```

## Conditional context

In your flow, next you need to create a condition in which your contract will be either [approved](#if-the-contract-is-approved) or [rejected](#if-the-contract-is-rejected).

![Conditional.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/condition.png?view=o365-worldwide)

## If the contract is approved

When a contract has been approved, the following things occur:

- On the **Contracts** tab, the status in the contract card changes to **Approved**.

  ![Card status approved.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/approved-contracts-tab.png?view=o365-worldwide)
- In your flow, the status is changed to **Approved**.

  ![Flow status approved.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/status-approved.png?view=o365-worldwide)
- In this solution, the contract data is added to the **For Payout** tab so that the payouts can be managed. This process can be extended to allow the flow to submit the contracts for payment by a third-party financial application \(for example, Dynamics CRM\).

  ![Contract moved to Pay Out.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/for-payout.png?view=o365-worldwide)
- In the flow, you create the following item to move approved contracts to the **For Payout** tab.

  ![Flow item to move to Pay Out.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/ready-for-payout.png?view=o365-worldwide)

  To get the expressions for the information needed from the Teams card, use the values shown in the following table.

  | Name | Expression |
  | --- | --- |
  | Approval state | body\('Post\_an\_Adaptive\_Card\_to\_a\_Teams\_channel\_and\_wait\_for\_a\_response'\)?\['submitActionId'\] |
  | Approved by | body\('Post\_an\_Adaptive\_Card\_to\_a\_Teams\_channel\_and\_wait\_for\_a\_response'\)?\['responder'\]\['displayName'\] |
  | Approval date | body\('Post\_an\_Adaptive\_Card\_to\_a\_Teams\_channel\_and\_wait\_for\_a\_response'\)?\['responseTime'\] |
  | Comment | body\('Post\_an\_Adaptive\_Card\_to\_a\_Teams\_channel\_and\_wait\_for\_a\_response'\)?\['data'\]?\['acComments'\] |


  The following example shows how to use the formula box in Power Automate to write an expression.


  ![Screenshot in Power Automate showing an expression formula.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/expression-formula-power-automate.png?view=o365-worldwide)

- An adaptive card stating that the contract has been approved is created and posted to the Contract Management channel.

  ![Contract approval posted.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/adaptive-card-approval.png?view=o365-worldwide)

  ![Adaptive card approval.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/adaptive-card.png?view=o365-worldwide)

  The following code is the JSON used for this step in the Power Automate flow.

```JSON
{ 
    "type": "AdaptiveCard",
    "body": [
        {
            "type": "Container",
            "style": "emphasis",
            "items": [
                {
                    "type": "ColumnSet",
                    "columns": [
                        {
                            "type": "Column",
                            "items": [
                                {
                                    "type": "TextBlock",
                                    "size": "Large",
                                    "weight": "Bolder",
                                    "text": "CONTRACT APPROVED"
                                }
                            ],
                            "width": "stretch"
                        }
                    ]
                }
            ],
            "bleed": true
        },
        {
            "type": "Container",
            "items": [
                {
                    "type": "FactSet",
                    "spacing": "Large",
                    "facts": [
                        {
                            "title": "Client",
                            "value": "@{triggerOutputs()?['body/Client']}"
                        },
                        {
                            "title": "Contractor",
                            "value": "@{triggerOutputs()?['body/Contractor']}"
                        },
                        {
                            "title": "Fee amount",
                            "value": "@{triggerOutputs()?['body/FeeAmount']}"
                        },
                        {
                            "title": "Approval by",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['responder']['displayName']}"
                        },
                        {
                            "title": "Approved date",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['responseTime']}"
                        },
                        {
                            "title": "Approval comment",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['data']?['acComments']}"
                        },
                        {
                            "title": " ",
                            "value": " "
                        },
                        {
                            "title": "Status",
                            "value": "Ready for payout"
                        }
                    ]
                }
            ]
        }
    ],
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.2",
    "fallbackText": "This card requires Adaptive Cards v1.2 support to be rendered properly."
}
```

## If the contract is rejected

When a contract has been rejected, the following things occur:

- On the **Contracts** tab, the status in the contract card changes to **Rejected**.

  ![Card status rejected.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/rejected-contracts-tab.png?view=o365-worldwide)
- In your flow, you check out the contract file, change the status to **Rejected**, and then check the file back in.

  ![Flow status rejected in contract file.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/reject-flow.png?view=o365-worldwide)
- In your flow, you create an adaptive card stating that the contract has been rejected.

  ![Flow status shows rejected on adaptive card.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/reject-flow-item.png?view=o365-worldwide)

The following code is the JSON used for this step in the Power Automate flow.

```JSON
{ 
    "type": "AdaptiveCard",
    "body": [
        {
            "type": "Container",
            "style": "attention",
            "items": [
                {
                    "type": "ColumnSet",
                    "columns": [
                        {
                            "type": "Column",
                            "items": [
                                {
                                    "type": "TextBlock",
                                    "size": "Large",
                                    "weight": "Bolder",
                                    "text": "CONTRACT REJECTED"
                                }
                            ],
                            "width": "stretch"
                        }
                    ]
                }
            ],
            "bleed": true
        },
        {
            "type": "Container",
            "items": [
                {
                    "type": "FactSet",
                    "spacing": "Large",
                    "facts": [
                        {
                            "title": "Client",
                            "value": "@{triggerOutputs()?['body/Client']}"
                        },
                        {
                            "title": "Contractor",
                            "value": "@{triggerOutputs()?['body/Contractor']}"
                        },
                        {
                            "title": "Fee amount",
                            "value": "@{triggerOutputs()?['body/FeeAmount']}"
                        },
                        {
                            "title": "Rejected by",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['responder']['displayName']}"
                        },
                        {
                            "title": "Rejected date",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['responseTime']}"
                        },
                        {
                            "title": "Comment",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['data']?['acComments']}"
                        },
                        {
                            "title": " ",
                            "value": " "
                        },
                        {
                            "title": "Status",
                            "value": "Needs review"
                        }
                    ]
                }
            ]
        }
    ],
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.2",
    "fallbackText": "This card requires Adaptive Cards v1.2 support to be rendered properly."
}
```

- The card is posted in the Contract Management channel.

  ![Flow adaptive card to reject.](https://learn.microsoft.com/en-us/microsoft-365/media/content-understanding/rejected.png?view=o365-worldwide)
