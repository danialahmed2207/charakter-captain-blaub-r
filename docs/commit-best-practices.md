# Commit Best Practices

> How to write commits that help your future self and your team.

---

## The Seven Rules of a Great Commit Message

1. Separate subject from body with a blank line
2. Limit the subject line to 50 characters
3. Capitalize the subject line
4. Do not end the subject line with a period
5. Use the imperative mood in the subject line
6. Wrap the body at 72 characters
7. Use the body to explain what and why, not how

## Good vs. Bad Examples

| Bad | Good |
|-----|------|
| `fixed bug` | `Fix DNS resolution timeout in network check script` |
| `update` | `Update Linux commands cheatsheet with systemd examples` |
| `WIP` | `Add disk usage monitoring to system-info script` |
| `changes` | `Refactor backup script to use timestamped directories` |
| `fix` | `Fix permissions on log-check-demo.sh` |

## Commit Message Structure

```
Summarize changes in 50 characters or less

More detailed explanatory text, if necessary. Wrap it to about 72
characters. In some contexts, the first line is treated as the subject
of the commit and the rest of the text as the body.

- Bullet points are okay
- Use a hyphen or asterisk for bullet points

Resolves: #123
See also: #456, #789
```

## Commit Granularity

- **One logical change per commit**
- Do not mix bug fixes and feature additions
- Do not mix formatting changes with functional changes

### Example of Good Granularity

```bash
git add system-info.sh
git commit -m "Add disk usage check to system-info script"

git add README.md
git commit -m "Document new disk usage feature in system-info"
```

## Commit Frequency

- Commit when a logical unit of work is complete
- Do not commit broken code
- If you need to save work-in-progress, use `git stash` or a draft branch

## Atomic Commits

An atomic commit is a commit that:
- Passes all tests
- Builds successfully
- Represents a single logical change

This makes bisecting (finding which commit introduced a bug) much easier.

## Useful Commands

```bash
# Amend last commit
git commit --amend -m "New message"

# Amend without changing message
git commit --amend --no-edit

# Interactive rebase to clean history
git rebase -i HEAD~5

# View commit history compactly
git log --oneline --graph --all
```
