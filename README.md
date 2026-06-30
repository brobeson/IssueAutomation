# Issue Automation

Automate issue and pull request processing

[![Workflow Quality](https://github.com/brobeson/IssueAutomation/actions/workflows/workflow_quality.yaml/badge.svg)](https://github.com/brobeson/IssueAutomation/actions/workflows/workflow_quality.yaml)
![GitHub Release](https://img.shields.io/github/v/release/brobeson/IssueAutomation?logo=github)

This is a reusable workflow to automate repetitve issue and pull request tasks.
It adds issues and pull requests to a GitHub project specified by the calling workflow.

## Getting Started

To use this workflow, first, create a personal access token (PAT) with project permission.
Add the PAT to your repository as a secret.

Then, call this workflow with the `uses` key of a job in your project's workflow file.

```yaml
on:
  issues:
    types: [opened]
  pull_request:
    types: [opened]
jobs:
  issue-automation:
    name: Issue Automation
    uses: brobeson/IssueAutomation/.github/workflows/issue_automation.yaml@v1
    secrets
      personal_access_token: ${{ secrets.PERSONAL_ACCESS_TOKEN }}
    with:
      project_owner: you
      project_id: 42
```

## Inputs

<!-- prettier-ignore -->
| Key       | Required |  Type  | Description                              |
| :-------- | :------: | :----: | :--------------------------------------- |
| `personal_access_token` |   yes    | string | The PAT you created and added to your repository. This must be in the `secrets` object in the calling job. |
| `project_owner` | yes | string | The account name of the user who owns the project to add issues to. _Organization projects are not supported._ |
| `project_id` | yes | number | The ID number of the project to update. |

## Steps

The workflow runs the following steps.

1. **Add new issues to the specified project.**  
   The PAT must project permission in the calling repository.

## Issue Tracking

[![GitHub Issues or Pull Requests by label](https://img.shields.io/github/issues/brobeson/ActionRelease/bug?logo=github&label=Bugs)](https://github.com/brobeson/ActionRelease/issues?q=is%3Aissue+is%3Aopen+label%3Abug)
[![GitHub Issues or Pull Requests by label](https://img.shields.io/github/issues/brobeson/ActionRelease/enhancement?logo=github&label=Enhancements)](https://github.com/brobeson/ActionRelease/issues?q=is%3Aissue+is%3Aopen+label%3Aenhancement)
[![GitHub Issues or Pull Requests by label](https://img.shields.io/github/issues/brobeson/ActionRelease/new%20step?logo=github&label=New%20Steps)](https://github.com/brobeson/ActionRelease/issues?q=is%3Aopen+is%3Aissue+label%3A%22new+step%22)
[![GitHub milestone details](https://img.shields.io/github/milestones/progress/brobeson/ActionRelease/1?logo=github)](https://github.com/brobeson/ActionRelease/milestone/1)

[Report a bug](https://github.com/brobeson/ActionRelease/issues/new?assignees=brobeson&labels=bug&projects=&template=bug.yaml) |
[Request a new step](https://github.com/brobeson/ActionRelease/issues/new?assignees=brobeson&labels=new+step&projects=&template=new_step.yaml) |
[Update an existing step](https://github.com/brobeson/ActionRelease/issues/new?assignees=brobeson&labels=enhancement&projects=&template=enhancement.yaml)
