![](https://img.shields.io/github/commit-activity/t/subhamay-bhattacharyya-gha/branch-issue-action)&nbsp;![](https://img.shields.io/github/last-commit/subhamay-bhattacharyya-gha/branch-issue-action)&nbsp;![](https://img.shields.io/github/release-date/subhamay-bhattacharyya-gha/branch-issue-action)&nbsp;![](https://img.shields.io/github/repo-size/subhamay-bhattacharyya-gha/branch-issue-action)&nbsp;![](https://img.shields.io/github/directory-file-count/subhamay-bhattacharyya-gha/branch-issue-action)&nbsp;![](https://img.shields.io/github/issues/subhamay-bhattacharyya-gha/branch-issue-action)&nbsp;![](https://img.shields.io/github/languages/top/subhamay-bhattacharyya-gha/branch-issue-action)&nbsp;![](https://img.shields.io/github/commit-activity/m/subhamay-bhattacharyya-gha/branch-issue-action)&nbsp;![](https://img.shields.io/endpoint?url=https://gist.githubusercontent.com/bsubhamay/create-branch-action/raw/branch-issue-action.json?)

# Create Feature Branch Composite Action

A GitHub Composite Action to automatically create a feature branch from an issue using the GitHub API.

## Features

- Creates a new branch based on an existing issue.
- Generates a branch name using project info and issue title.
- Posts a comment on the issue with a link to the new branch.

## Inputs

| Name           | Description                                     | Required | Default |
|----------------|-------------------------------------------------|----------|---------|
| `base-branch`  | The base branch to create the new branch from.  | No       | `main`  |
| `title-length` | Number of characters to keep from issue title.  | Yes      | `15`    |
| `github-token` | GitHub token with repo access.                  | Yes      | –       |

## Usage

```yaml
jobs:
  create-feature-branch:
    runs-on: ubuntu-latest
    permissions:
      issues: write
      contents: write
    steps:
      - uses: your-org/create-feature-branch-action@v1
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
          title-length: 20
```

> **Note:** This action is triggered by issue events. Make sure your workflow listens to `issues` events (like `opened`).

## How It Works

1. Extracts the issue number and title.
2. Builds a branch name using:
   ```
   feature/<PROJECT_PREFIX>-<PROJECT_NO>.<ISSUE_NUMBER>-<slugified-title>
   ```
3. Uses the GitHub API to create the branch from the base branch.
4. Comments on the issue with a link to the new branch.

## Example Output

Given:
- Repo: `acme-portal`
- Issue #123 titled: `Add support for dark mode`

Generated branch might be:
```
feature/PORTAL-123-add-support
```

## Requirements

- `jq` (used internally for parsing JSON).
- A GitHub token with `repo` and `issues` permissions.

## License

MIT
