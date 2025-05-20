# Branch Issue Action

![Release](https://github.com/subhamay-bhattacharyya-gha/branch-issue-action/actions/workflows/release.yaml/badge.svg)&nbsp;![Commit Activity](https://img.shields.io/github/commit-activity/t/subhamay-bhattacharyya-gha/branch-issue-action)&nbsp;![Last Commit](https://img.shields.io/github/last-commit/subhamay-bhattacharyya-gha/branch-issue-action)&nbsp;![Release Date](https://img.shields.io/github/release-date/subhamay-bhattacharyya-gha/branch-issue-action)&nbsp;![Repo Size](https://img.shields.io/github/repo-size/subhamay-bhattacharyya-gha/branch-issue-action)&nbsp;![File Count](https://img.shields.io/github/directory-file-count/subhamay-bhattacharyya-gha/branch-issue-action)&nbsp;![Open Issues](https://img.shields.io/github/issues/subhamay-bhattacharyya-gha/branch-issue-action)&nbsp;![Top Language](https://img.shields.io/github/languages/top/subhamay-bhattacharyya-gha/branch-issue-action)&nbsp;![Monthly Commit Activity](https://img.shields.io/github/commit-activity/m/subhamay-bhattacharyya-gha/branch-issue-action)&nbsp;![Custom Endpoint](https://img.shields.io/endpoint?url=https://gist.githubusercontent.com/bsubhamay/2634bcd24d438581fd81fe06f006d1b1/raw/branch-issue-action.json?)

**Branch Issue Action** is a GitHub Composite Action that extracts the issue number from the current branch name and verifies its existence using the GitHub API.

---

## 🔧 Inputs

| Name            | Description                       | Required |
|-----------------|-----------------------------------|----------|
| `github-token`  | GitHub token with repo access     | Yes      |

---

## 📤 Outputs

| Name            | Description                         |
|-----------------|-------------------------------------|
| `issue-number`  | Extracted issue number from branch  |
| `issue-exists`  | `true` if the issue exists, else `false` |

---

## 🧠 How It Works

- Retrieves the current branch name from `GITHUB_REF`.
- Parses the issue number from the branch name based on a defined pattern.
- Uses the GitHub API to check whether the issue exists in the current repository.

---

## 📁 Branch Name Format

Branch names must follow this format:

```text
<type>/<project-code>-<project-sequence>.<issue-number>-<slug>
```

### Example

```text
feature/CLO-0001.6-add-cloudformat
```

**Breakdown:**

- `feature` — Branch type.
- `CLO` — First three characters of the project name (e.g., "cloudformation").
- `0001` — Project sequence.
- `6` — Issue number.
- `add-cloudformat` — Slug for the feature or task.

---

## 🚀 Usage

Add this step to your GitHub Actions workflow:

```yaml
jobs:
  check-issue:
    runs-on: ubuntu-latest
    steps:
      - name: Check branch created from issue
        uses: subhamay-bhattacharyya-gha/branch-issue-action@main
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
```

---

## 🔗 Related Tools

For automating branch creation when assigning issues, check out the companion action:  
[**create-branch-action**](https://github.com/subhamay-bhattacharyya-gha/create-branch-action)

---

## 📄 License

MIT
