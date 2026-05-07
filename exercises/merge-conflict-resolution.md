# Exercise: Merge Conflict Resolution

> A hands-on exercise to practice resolving Git merge conflicts.

---

## Setup

```bash
# Create a test repository
mkdir git-conflict-exercise
cd git-conflict-exercise
git init

# Create initial file
echo "Line 1: Original content" > file.txt
git add file.txt
git commit -m "Add initial file"
```

## Create the Conflict

```bash
# Create branch A
git checkout -b branch-a

echo "Line 1: Branch A content" > file.txt
git add file.txt
git commit -m "Update file in branch A"

# Return to main and create branch B
git checkout main
git checkout -b branch-b

echo "Line 1: Branch B content" > file.txt
git add file.txt
git commit -m "Update file in branch B"
```

## Resolve the Conflict

```bash
# Try to merge branch-a into branch-b
git checkout branch-b
git merge branch-a

# You will see:
# Auto-merging file.txt
# CONFLICT (content): Merge conflict in file.txt
# Automatic merge failed; fix conflicts and then commit the result.
```

The file will look like this:

```
<<<<<<< HEAD
Line 1: Branch B content
=======
Line 1: Branch A content
>>>>>>> branch-a
```

## Resolution Steps

1. **Open the file** and decide which content to keep (or combine both)
2. **Remove conflict markers** (`<<<<<<<`, `=======`, `>>>>>>>`)
3. **Stage the resolved file**
   ```bash
   git add file.txt
   ```
4. **Complete the merge**
   ```bash
   git commit -m "Merge branch-a into branch-b, resolve content conflict"
   ```

## Best Practices

- Always review the conflicting sections carefully
- Do not blindly accept one side — understand the intent
- Test the result if possible
- Use merge tools if the conflict is complex:
  ```bash
  git mergetool
  ```

## Prevention

- Pull latest changes before starting new work
- Communicate with teammates about who is editing which files
- Keep branches short-lived
- Use feature flags for incomplete work instead of long branches
