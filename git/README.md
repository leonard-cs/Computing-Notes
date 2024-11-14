# Git Command Notes

## Table of Contents
- [Branching & Merging](#branching--merging)
- [Browsing History](#browsing-history)
    - [Checkout a commit](#checkout-a-commit)
    - [Comparing commits](#comparing-commits)
- [Rewriting History](#rewriting-history)
    - [Undoing commits](#undoing-commits)

## Configuration
- **Name**: `git config --global user.name "Leonard Chi"`
- **Email**: `git config --global user.email "leonardocompsci@gmail.com"`
- **Default Editor**: `git config --global core.editor "code --wait"`
- **Line Ending**:

    `git config --global core.autocrlf input` (mac/linux)

    `git config --global core.autocrlf true` (windows)
- Access configuration settings: `git config --global -e`

### Level
- **System**: All users
- **Global**: All repositories of the current user
- **Local**: Current repository

## Branching & Merging

## Browsing History
### Viewing the history
```bash
git log --all --graph --oneline
```

### Checkout a commit
```bash
git checkout <hash> # Checks out the given commit
git switch - # Switch back to previous commit
```

### Comparing commits
```bash
git diff <hash1> <hash2> # Show the differences between two commits
git diff <hash1> <hash2> file.txt # Changes to file.txt only
```
To compare two commits on GitLab:
```
https://gitlab.com/<namespace>/<repository>/commits?from=<commit_hash1>&to=<commit_hash2>
```

## Rewriting History
Update commit message of previous commit
```bash
git commit -m "New message" --amend
```

### Undoing commits
```bash
# Removes the last commit, keeps changed staged
git reset --soft HEAD~1
git reset --mixed HEAD~1 # Unstages the changes as well
git reset --hard HEAD~1 # Discards local changes
```
