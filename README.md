# issues-test

Create automatic GitHub Issues, either periodically (`cron`-style) or manually triggered (`workflow_dispatch`).

## Installation

Create a `.github/workflows` directory with a file for each workflow. This repository contains some examples.

## Using the GitHub CLI

The GitHub container image in which workflows are executed has the [gh utility](https://cli.github.com/) pre-installed, which can be used to interact with the repository, including issues.

For extended options, see the [GitHub CLI](https://cli.github.com/manual/gh_issue_create) documentation.

The GitHub CLI is authorized by the `GH_TOKEN` environment variable.
