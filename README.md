# Branch Issue Action

![Commit Activity](https://img.shields.io/github/commit-activity/t/subhamay-bhattacharyya-gha/branch-issue-action)&nbsp;![Last Commit](https://img.shields.io/github/last-commit/subhamay-bhattacharyya-gha/branch-issue-action)&nbsp;![Release Date](https://img.shields.io/github/release-date/subhamay-bhattacharyya-gha/branch-issue-action)&nbsp;![Repo Size](https://img.shields.io/github/repo-size/subhamay-bhattacharyya-gha/branch-issue-action)&nbsp;![File Count](https://img.shields.io/github/directory-file-count/subhamay-bhattacharyya-gha/branch-issue-action)&nbsp;![Open Issues](https://img.shields.io/github/issues/subhamay-bhattacharyya-gha/branch-issue-action)&nbsp;![Top Language](https://img.shields.io/github/languages/top/subhamay-bhattacharyya-gha/branch-issue-action)&nbsp;![Monthly Commit Activity](https://img.shields.io/github/commit-activity/m/subhamay-bhattacharyya-gha/branch-issue-action)&nbsp;![Custom Endpoint](https://img.shields.io/endpoint?url=https://gist.githubusercontent.com/bsubhamay/2634bcd24d438581fd81fe06f006d1b1/raw/branch-issue-action.json?)

**Get the issue number associated with the current branch and check if it exists on GitHub.**

This GitHub Composite Action extracts an issue number from the branch name and verifies whether that issue exists in the repository.

---

## 🔧 Inputs

| Name          | Description      | Required |
|---------------|------------------|----------|
| `github-token` | GitHub token with repo access | ✅ Yes |

---

## 📤 Outputs

| Name            | Description                            |
|-----------------|----------------------------------------|
| `issue-number`  | Extracted issue number from branch     |
| `issue-exists`  | `true` if the issue exists, else `false` |

---

## 🧠 How It Works

- It grabs the current branch name from `GITHUB_REF`.
- It extracts the issue number based on a naming convention (e.g. `issue.123-feature-name` → `123`).
- It uses the GitHub API to check if the issue exists in the current repository.

---

## 📁 Example Branch Name Format

The action expects the branch name to follow a format where the issue number can be extracted as the second segment:

The branch name should be in the format `<Project Code>.<Issue Number>-<Project Name>-<IaC>`, e.g, `0918-api-gateway-py-cft`

---

## 🚀 Usage

To use this action in your GitHub workflow, include the following step in your `.github/workflows/<workflow-file>.yml`:

```yaml
jobs:
  check-issue:
    runs-on: ubuntu-latest
    steps:
      - name: Check Branch created from Issue
        uses: subhamay-bhattacharyya-gha/branch-issue-action@main
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}

```

---

## License

MIT
