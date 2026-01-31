# Git Commands Reference - Comprehensive Guide

## Configuration
### Set user identity
```bash
git config --global user.name "Zayan-Mohamed"
git config --global user.email "your-email@example.com"
```

### Check configuration
```bash
git config --list
git config --global user.name
git config --global user.email
```

## Repository Setup
### Initialize new repository
```bash
git init
git init project-name  # Initialize and create directory
```

### Clone existing repository
```bash
git clone <repository-url>
git clone <repository-url> <local-directory-name>
```

### Clone specific repository
```bash
git clone https://github.com/Zayan-Mohamed/paf-lab.git
git clone git@github.com:Zayan-Mohamed/paf-lab.git
```

## Basic Workflow Commands
### Check repository status
```bash
git status
git status -s  # Short format
git status --porcelain  # Machine readable
```

### Add files to staging area
```bash
git add filename.txt
git add .                    # Add all files in current directory
git add -A                   # Add all files including deletions
git add *.js                 # Add all JavaScript files
git add src/                 # Add all files in src directory
```

### Commit changes
```bash
git commit -m "Commit message"
git commit -m "Fix bug" -m "Detailed description"
git commit                   # Opens editor for detailed commit message
```

### Amend last commit
```bash
git commit --amend
git commit --amend -m "New commit message"
```

## Branching
### Create and switch branches
```bash
git branch feature-branch          # Create branch
git checkout feature-branch       # Switch to branch
git checkout -b new-feature        # Create and switch to branch
git switch -b new-feature          # Modern alternative (Git 2.23+)
```

### List branches
```bash
git branch              # List local branches
git branch -r           # List remote branches
git branch -a           # List all branches
git branch -v           # List with last commit info
```

### Delete branches
```bash
git branch -d feature-branch      # Delete merged branch
git branch -D feature-branch      # Force delete branch
git push origin --delete feature-branch  # Delete remote branch
```

### Rename branch
```bash
git branch -m old-name new-name   # Rename current branch
git branch -m feature-branch       # Rename current branch
```

### Merge branches
```bash
git checkout main
git merge feature-branch           # Merge feature into main
git merge --no-ff feature-branch  # Merge without fast-forward
git merge --abort                  # Abort merge in progress
```

### Rebase branches
```bash
git checkout feature-branch
git rebase main                    # Rebase feature onto main
git rebase -i HEAD~3              # Interactive rebase of last 3 commits
git rebase --continue             # Continue after resolving conflicts
git rebase --abort                # Cancel rebase
```

## Remote Repository Management
### Add remote repository
```bash
git remote add origin https://github.com/Zayan-Mohamed/paf-lab.git
git remote add upstream https://github.com/original/repo.git
```

### List remotes
```bash
git remote
git remote -v  # Verbose with URLs
```

### Push to remote
```bash
git push origin main
git push -u origin main           # Set upstream and push
git push --all origin             # Push all branches
git push --tags                   # Push all tags
git push origin feature-branch    # Push specific branch
```

### Pull from remote
```bash
git pull origin main
git pull --rebase origin main     # Pull with rebase instead of merge
```

### Fetch from remote
```bash
git fetch origin                  # Fetch all branches
git fetch origin main             # Fetch specific branch
git fetch --all                   # Fetch from all remotes
```

## Viewing History
### View commit history
```bash
git log
git log --oneline                 # Compact format
git log --graph --oneline         # ASCII graph
git log --author="Zayan-Mohamed"  # Filter by author
git log --since="2 weeks ago"     # Filter by time
git log -p                        # Show changes (patch)
git log --stat                    # Show statistics
```

### View specific commit
```bash
git show                          # Show last commit
git show <commit-hash>           # Show specific commit
git show HEAD~2                  # Show 2 commits before HEAD
```

### Diff commands
```bash
git diff                          # Working directory vs staging
git diff --staged                 # Staging vs last commit
git diff HEAD                     # Working directory vs last commit
git diff branch1 branch2          # Compare branches
git diff HEAD~1 HEAD             # Show changes in last commit
```

## Undoing Changes
### Unstage files
```bash
git reset HEAD filename.txt       # Unstage specific file
git reset HEAD                    # Unstage all files
```

### Discard local changes
```bash
git checkout -- filename.txt      # Discard changes to file
git restore filename.txt          # Modern alternative
git restore .                     # Discard all changes in directory
```

### Reset commits
```bash
git reset --soft HEAD~1           # Move HEAD back, keep changes staged
git reset --mixed HEAD~1          # Move HEAD back, keep changes unstaged (default)
git reset --hard HEAD~1           # Move HEAD back, discard all changes
```

### Revert commits
```bash
git revert HEAD                   # Create new commit that reverses last commit
git revert <commit-hash>          # Revert specific commit
```

## Stashing
### Save work in progress
```bash
git stash                         # Stash current changes
git stash -m "Work in progress"   # Stash with message
git stash push -m "Message"       # Push stash with message
```

### View and apply stashes
```bash
git stash list                    # List all stashes
git stash show                    # Show most recent stash
git stash apply                   # Apply most recent stash
git stash pop                     # Apply and remove most recent stash
git stash apply stash@{1}         # Apply specific stash
```

### Drop/clear stashes
```bash
git stash drop stash@{1}          # Drop specific stash
git stash clear                   # Clear all stashes
```

## Tagging
### Create tags
```bash
git tag v1.0.0                    # Lightweight tag
git tag -a v1.0.0 -m "Version 1.0.0"  # Annotated tag
git tag -a v1.0.0 <commit-hash>   # Tag specific commit
```

### List and view tags
```bash
git tag                           # List all tags
git show v1.0.0                   # Show tag details
```

### Push tags
```bash
git push origin v1.0.0            # Push specific tag
git push origin --tags            # Push all tags
```

### Delete tags
```bash
git tag -d v1.0.0                 # Delete local tag
git push origin --delete v1.0.0   # Delete remote tag
```

## File Operations
### Remove files
```bash
git rm filename.txt               # Remove and stage deletion
git rm --cached filename.txt      # Remove from tracking but keep file
git rm -r directory/             # Remove directory
```

### Move/Rename files
```bash
git mv oldname.txt newname.txt    # Rename/move file
```

## Searching
### Search commits
```bash
git log --grep="search term"      # Search commit messages
git log --author="name"           # Search by author
git log -- filename.txt           # History of specific file
```

### Search code
```bash
git grep "search term"            # Search current working tree
git grep "search term" HEAD~1     # Search in previous commit
```

## Cherry-picking
```bash
git cherry-pick <commit-hash>     # Apply commit to current branch
git cherry-pick <hash1> <hash2>   # Apply multiple commits
git cherry-pick --abort           # Abort cherry-pick with conflicts
git cherry-pick --continue        # Continue after resolving conflicts
```

## Bisect (Finding Bugs)
```bash
git bisect start                  # Start bisect
git bisect bad                    # Mark current commit as bad
git bisect good <commit-hash>     # Mark known good commit
git bisect run <command>          # Run test command
git bisect reset                  # End bisect session
```

## Clean Up
### Remove untracked files
```bash
git clean -n                      # Dry run (show what would be deleted)
git clean -f                      # Force remove untracked files
git clean -df                     # Remove files and directories
git clean -xf                     # Remove ignored files too
```

### Garbage collection
```bash
git gc                            # Garbage collection
git gc --aggressive               # Aggressive garbage collection
```

## Configuration Aliases
### Common aliases
```bash
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.cm commit
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last 'log -1 HEAD'
git config --global alias.visual '!gitk'
```

## Useful One-liners
### Show file changes
```bash
git log --follow -- filename.txt  # Show file history including renames
git whatchanged filename.txt      # Show changes to specific file
```

### Find commit that introduced bug
```bash
git log -S "function_name"        # Find commits that added string
git log -p -- filename.txt | grep "search"
```

### Show merge history
```bash
git log --merges
git log --no-merges
```

## Submodules
### Add submodule
```bash
git submodule add <repository-url> <path>
git submodule add https://github.com/user/repo.git lib/repo
```

### Initialize and update
```bash
git submodule init                # Initialize submodules
git submodule update              # Update submodules
git submodule update --init --recursive  # Clone and update all
```

## Archive and Export
### Create archive
```bash
git archive --format=zip --output=archive.zip HEAD
git archive --format=tar.gz --output=archive.tar.gz HEAD
git archive --format=zip --output=source.zip v1.0.0
```

## Troubleshooting
### Common issues
```bash
# Fix broken branch reference
git update-ref -d refs/heads/branch-name

# Recover lost commit
git reflog
git checkout <lost-commit-hash>

# Fix detached HEAD
git checkout main
git merge <detached-commit-hash>
```

### Conflict resolution
```bash
git status                        # Check conflicts
git mergetool                     # Use merge tool
git add .                         # Mark conflicts as resolved
git commit                        # Complete merge
```

## Workflow Examples

### Basic feature workflow
```bash
# Start new feature
git checkout -b feature/new-feature
git add .
git commit -m "Add new feature"

# Push to remote
git push -u origin feature/new-feature

# Merge to main
git checkout main
git pull origin main
git merge feature/new-feature
git push origin main

# Clean up
git branch -d feature/new-feature
git push origin --delete feature/new-feature
```

### Hotfix workflow
```bash
# Create hotfix from main
git checkout main
git pull origin main
git checkout -b hotfix/urgent-fix

# Make and commit fix
git add .
git commit -m "Fix urgent bug"

# Merge and tag
git checkout main
git merge hotfix/urgent-fix
git tag v1.0.1
git push origin main --tags

# Clean up
git branch -d hotfix/urgent-fix
```

### Rebase workflow
```bash
# Keep feature branch updated
git checkout feature-branch
git fetch origin
git rebase origin/main

# Interactive rebase for cleanup
git rebase -i HEAD~5  # Interactive rebase of last 5 commits
```

---

**Repository-specific commands for paf-lab:**
```bash
# Clone the repository
git clone https://github.com/Zayan-Mohamed/paf-lab.git
cd paf-lab

# Set up remote tracking
git push -u origin main

# Create feature branch
git checkout -b feature/your-feature-name
```

**Best Practices:**
- Write descriptive commit messages
- Pull before pushing to avoid conflicts
- Use branches for new features
- Regularly push to remote as backup
- Use `.gitignore` to exclude unnecessary files
- Review changes before committing with `git diff --staged`

