![](https://img.shields.io/github/commit-activity/t/subhamay-bhattacharyya-gha/branch-issue-action)&nbsp;![](https://img.shields.io/github/last-commit/subhamay-bhattacharyya-gha/branch-issue-action)&nbsp;![](https://img.shields.io/github/release-date/subhamay-bhattacharyya-gha/branch-issue-action)&nbsp;![](https://img.shields.io/github/repo-size/subhamay-bhattacharyya-gha/branch-issue-action)&nbsp;![](https://img.shields.io/github/directory-file-count/subhamay-bhattacharyya-gha/branch-issue-action)&nbsp;![](https://img.shields.io/github/issues/subhamay-bhattacharyya-gha/branch-issue-action)&nbsp;![](https://img.shields.io/github/languages/top/subhamay-bhattacharyya-gha/branch-issue-action)&nbsp;![](https://img.shields.io/github/commit-activity/m/subhamay-bhattacharyya-gha/branch-issue-action)&nbsp;![](https://img.shields.io/endpoint?url=https://gist.githubusercontent.com/bsubhamay/2634bcd24d438581fd81fe06f006d1b1/raw/branch-issue-action.json?)

# Branch Issue

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

## License

MIT
