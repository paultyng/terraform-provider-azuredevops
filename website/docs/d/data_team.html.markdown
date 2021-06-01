---
layout: "azuredevops"
page_title: "AzureDevops: azuredevops_team"
description: |-
  Use this data source to access information about an existing Team in a Project within Azure DevOps.
---

# Data Source: azuredevops_team

Use this data source to access information about an existing Team in a Project within Azure DevOps.

## Example Usage

```hcl
resource "azuredevops_project" "project" {
  name               = "Test Project"
  work_item_template = "Agile"
  version_control    = "Git"
  visibility         = "private"
  description        = "My first project"
}

data "azuredevops_team" "team" {
  project_id = azuredevops_project.project.id
  name       = "Team Project Team"
}
```

## Argument Reference

The following arguments are supported:

- `project_id` - (Required) The Project ID.
- `name` - (Required) The name of the Team.

## Attributes Reference

The following attributes are exported:

- `id - Team identifier
- `description` - Team description.
- `administrators` - List of subject descriptors for `administrators` of the team.
- `members` - List of subject descriptors for `members` of the team.

## Relevant Links

- [Azure DevOps Service REST API 5.1 - Teams - Get](https://docs.microsoft.com/en-us/rest/api/azure/devops/core/teams/get?view=azure-devops-rest-5.1)

## PAT Permissions Required

- **vso.project**:	Grants the ability to read projects and teams.
