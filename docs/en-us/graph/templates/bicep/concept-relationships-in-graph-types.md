<!-- Source: https://learn.microsoft.com/en-us/graph/templates/bicep/concept-relationships-in-graph-types -->
<!-- Sitemap-Last-Modified: 2025-07-29 -->

# Model relationships in Microsoft Graph Bicep types

Microsoft Graph Bicep types let you model relationships between resources, helping you manage dependencies. This article explains the two main relationship models supported by Microsoft Graph APIs and how to use them in Bicep.

1. **Relationships between entity types**: This model links two different resource types. For example, a group and its members, who might be users, service principals, devices, or groups. You can add or remove members from a group. Deleting a group doesn't delete its user members because groups and users have independent lifecycles.
2. **Parent-child relationships**: In this model, child resources are contained within a parent resource, and their lifecycle depends on the parent. For example, `federatedIdentityCredentials` are child resources of an `application`. Deleting the application also deletes its `federatedIdentityCredentials`.

## Relationships between entity types

These relationships use the [MicrosoftGraphRelationship](https://learn.microsoft.com/en-us/graph/templates/bicep/reference/groups#microsoftgraphrelationship) type. For example, a group's `members` and `owners` properties are modeled as follows \(other required group properties are omitted for brevity\). The `relationships` array has the IDs of related Microsoft Graph resources.

```bicep
resource group 'Microsoft.Graph/groups@v1.0' = {
  members: {
    relationships: [id1, id2, id3]
  }
  owners: {
    relationships: [id4, id5]
  }
}
```

### Controlling relationship behavior

Two key behaviors control how relationships are managed in Bicep templates: `append` and `replace` semantics.

By default, relationship updates use *append* semantics. This means each ID in the list is added if it doesn't already exist, matching the default Microsoft Graph API behavior. You can also use *replace* semantics, which replaces all existing relationships with those in the Bicep template. In this example, the group's members are replaced with `id1`, `id2`, and `id3`:

```bicep
resource group 'Microsoft.Graph/groups@v1.0' = {
  members: {
    relationshipSemantics: 'replace'
    relationships: [id1, id2, id3]
  }
  owners: {
    relationships: [id4, id5]
  }
}
```

You can set the relationship behavior globally in the template by using the `extension` statement:

```bicep
extension graphV1 with {
  relationshipSemantics: 'replace'
}
```

This sets all relationships in the template to use *replace* semantics. You can override this setting for individual relationships as needed.

### Microsoft Graph Bicep extension behavior

Starting with `v0.2.0-preview`, the Microsoft Graph Bicep extension manages *replace* semantics. It checks which relationships to add or remove and batches relationship requests to handle Microsoft Graph API request limits for both reads and writes.

## Parent-child relationships

In Bicep, you can declare parent-child relationships by nesting child resources under the parent resource. For example, [federated identity credentials](https://learn.microsoft.com/en-us/graph/templates/bicep/reference/federatedidentitycredentials) are typically nested under their parent application resource.

## Related content

- [Explore samples that demonstrate how to model relationships in Microsoft Graph Bicep types](https://learn.microsoft.com/en-us/graph/templates/bicep/quickstart-additional-samples)
