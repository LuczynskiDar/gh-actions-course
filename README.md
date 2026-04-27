# gh-actions-course

A repository of GitHub Actions workflow samples covering topics from basic building blocks to advanced security practices, built as part of a hands-on learning course.

## Related Repository

This repo is related to the forked course repository:
[LuczynskiDar/GitHub-Actions-Masterclass-From-Beginner-to-Advanced](https://github.com/LuczynskiDar/GitHub-Actions-Masterclass-From-Beginner-to-Advanced)

---

## Workflows

| # | File | Topic |
|---|------|-------|
| 01 | `01-building-blocks.yml` | Basic workflow structure — jobs, steps, runners |
| 02 | `02-workflow-events.yml` | Workflow trigger events |
| 03 | `03-workflow-runners.yml` | Runner types and configuration |
| 04 | `04-using-actions.yml` | Using marketplace and built-in actions |
| 05-1 | `05-1-filters-activity-types.yml` | Event filters and activity types |
| 05-2 | `05-2-filters-activity-types.yml` | Advanced filters |
| 06 | `06-contexts.yml` | GitHub contexts (`github`, `env`, `secrets`, etc.) |
| 07 | `07-expressions.yml` | Expressions and conditional logic |
| 08 | `08-variables.yml` | Environment variables and secrets |
| 09 | `09-functions.yml` | Built-in workflow functions |
| 10 | `10-execution-flow.yml` | Job dependencies and execution flow |
| 11 | `11-inputs.yml` | Workflow inputs (`workflow_dispatch`) |
| 12 | `12-outputs.yml` | Job and step outputs |
| 13 | `13-caching.yml` | Dependency caching |
| 14 | `14-artifacts.yml` | Uploading and downloading artifacts |
| 15 | `15-matrices.yml` | Matrix strategy for parallel jobs |
| 16 | `16-environments.yml` | Deployment environments and protection rules |
| 17-1 | `17-1-custom-actions-composite.yml` | Custom composite actions |
| 17-2 | `17-2-custom-actions-js.yml` | Custom JavaScript actions |
| 17-3 | `17-3-custom-actions-docker.yml` | Custom Docker container actions |
| 18-1 | `18-1-reusable-workflows.yml` | Reusable workflows — caller |
| 18-2 | `18-2-reusable-workflows.yml` | Reusable workflows — called |
| 18-3 | `18-3-reusable-workflows.yml` | Reusable workflows — advanced patterns |
| 19-1 | `19-1-concurency.yml` | Concurrency groups |
| 19-2 | `19-2-concurency.yml` | Concurrency with cancellation |
| 20 | `20-workflow-security.yml` | Workflow security — unsafe vs. safe input handling |

---

## Custom Actions

Located in `.github/actions/`:

| Action | Type | Description |
|--------|------|-------------|
| `composite-cache-deps` | Composite | Sets up Node.js and caches npm dependencies |
| `js-dependency-update` | JavaScript | Checks and updates JS dependencies via PR |
| `docker-ping-url` | Docker | Pings a URL from inside a Docker container (Python) |
| `security-safe-input` | JavaScript | Safely handles untrusted PR title input to prevent script injection |

---

## Security (Lesson 20)

The `20-workflow-security.yml` workflow demonstrates three approaches to handling untrusted user input (e.g. PR titles):

- **`unsafe-pr`** — directly interpolates `${{ github.event.pull_request.title }}` into a `run` shell script (vulnerable to script injection)
- **`safer-pr`** — passes the value via an `env` variable, preventing direct injection
- **`js-safer-pr`** — delegates validation to a custom JavaScript action (`security-safe-input`) for the safest handling
