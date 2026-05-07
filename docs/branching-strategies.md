# Branching Strategies

> How to structure branches for clean, manageable version control.

---

## Naming Conventions

| Prefix | Purpose | Example |
|--------|---------|---------|
| `feature/` | New functionality | `feature/user-authentication` |
| `bugfix/` | Non-urgent fixes | `bugfix/login-redirect` |
| `hotfix/` | Urgent production fixes | `hotfix/security-patch` |
| `release/` | Release preparation | `release/v2.1.0` |
| `docs/` | Documentation updates | `docs/api-reference` |
| `refactor/` | Code restructuring | `refactor/database-layer` |

## Solo Developer Strategy

```bash
# Start new work
git checkout -b feature/new-script

# Work, commit, push
git add .
git commit -m "Add backup automation script"
git push origin feature/new-script

# Merge via pull request (even solo, for discipline)
# Then delete branch
git branch -d feature/new-script
```

## Team Strategy

1. **Pull latest main before starting work**
   ```bash
   git checkout main
   git pull origin main
   git checkout -b feature/my-feature
   ```

2. **Commit frequently with clear messages**

3. **Push branch and open pull request early** (draft if incomplete)

4. **Require code review before merging**

5. **Delete merged branches** to keep the repository clean

## Protecting Main Branch

Configure branch protection rules in GitHub:

- Require pull request reviews
- Require status checks (CI tests)
- Require linear history (no merge commits)
- Restrict who can push to main

## Common Anti-Patterns

| Anti-Pattern | Why It Is Bad | Better Approach |
|--------------|---------------|-----------------|
| Long-lived branches | Merge conflicts accumulate | Keep branches short (hours to days) |
| Vague branch names | Hard to understand purpose | Use descriptive names with prefixes |
| Committing to main directly | Risk of breaking code | Use feature branches and PRs |
| Not deleting old branches | Cluttered repository | Delete after merge |
