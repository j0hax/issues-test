# issues-test

## Installation

Create a `.github/workflows` directory with a file for the required workflows. This repository contains some examples.

The GitHub container image in which workflows are executed has the [gh utility](https://cli.github.com/) pre-installed, which can be used to interact with the repository, including issues.

For extended options, see the [GitHub CLI](https://cli.github.com/manual/gh_issue_create) documentation.

The GitHub CLI is authorized by the `GH_TOKEN` environment variable.

## Overview of Workflows

### Automatic Issues

See the [daily.yml](/.github/workflows/daily.yml) workflow as an example workflow which opens a new issue every morning on workdays.

### Automatic Pull-Requests

The [auto-pr.yml](/.github/workflows/auto-pr.yml) workflow is designed to be called from other workflows.
It opens a pull request to merge from `src-branch` onto `dst-branch`.

#### Example

To create a pull request each morning, merging `test` onto `QA`:

```yaml
name: Merge test to QA
on:
  workflow_dispatch:
  schedule:
    - cron: '0 8 * * *'

jobs:
  test-qa:
    permissions:
      pull-requests: write
    # The 'uses' attribute must be changed to reflect the repo
    uses: j0hax/issues-test/.github/workflows/auto-pr.yml@main
    with:
      src-branch: test
      dst-branch: QA
```
