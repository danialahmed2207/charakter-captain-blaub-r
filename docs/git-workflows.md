# Git Workflows

> Overview of common Git workflows for individual and team projects.

---

## 1. Centralized Workflow

Best for: Small teams, simple projects

```
main
 └── [everyone commits directly to main]
```

- Everyone commits to a single branch
- Simple but risky for larger teams
- Requires discipline and communication

## 2. Feature Branch Workflow

Best for: Most team projects

```
main
 ├── feature/login
 ├── feature/api
 └── bugfix/memory-leak
```

- Create a branch for every feature or bugfix
- Merge back to main via pull request
- Allows code review before merging

## 3. Gitflow Workflow

Best for: Projects with scheduled releases

```
main
 ├── develop
 │    ├── feature/login
 │    ├── feature/api
 │    └── release/v1.0
 ├── hotfix/security-patch
```

| Branch | Purpose |
|--------|---------|
| `main` | Production-ready code |
| `develop` | Integration branch for features |
| `feature/*` | New features |
| `release/*` | Release preparation |
| `hotfix/*` | Urgent production fixes |

## 4. Forking Workflow

Best for: Open source projects

- Each developer forks the main repository
- Work happens in personal forks
- Changes proposed via pull requests to the upstream repo

## 5. Trunk-Based Development

Best for: Continuous deployment, experienced teams

- Short-lived feature branches (hours to days)
- Frequent merges to main
- Feature flags for incomplete work
- Requires robust CI/CD

---

## Choosing a Workflow

| Team Size | Release Cadence | Recommended Workflow |
|-----------|----------------|----------------------|
| 1–2 people | Any | Feature Branch or Centralized |
| 3–8 people | Periodic | Feature Branch or Gitflow |
| 8+ people | Continuous | Trunk-Based |
| Open source | Any | Forking |
