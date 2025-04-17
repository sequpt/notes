# git

Distributed revision control system.

- Homepage: <https://git-scm.com/>
- Repo
  - <https://git.kernel.org/pub/scm/git/git.git>
  - <https://github.com/git/git>

## Table of Contents

- [git](#git)
  - [Table of Contents](#table-of-contents)
  - [Installation](#installation)
  - [Usage](#usage)
    - [Configuration](#configuration)
    - [Creation](#creation)
    - [Branches](#branches)
    - [Staging](#staging)
    - [Commits](#commits)
    - [Tags](#tags)
    - [Remote](#remote)
    - [Log](#log)
    - [Worktree](#worktree)
  - [Snippets](#snippets)
  - [Misc](#misc)
    - [Always commit code with date in UTC timezone](#always-commit-code-with-date-in-utc-timezone)

## Installation

- Debian package: `gpg`

## Usage

### Configuration

```text
git config --global user.name "<name>"         # Set <name> globally
git config --global user.email "<email>"       # Set <email> globally
git config --local user.name "<name>"          # Set <name> locally
git config --local user.email "<email>"        # Set <email> locally
git config --global core.editor "<editor-cmd>" # [gedit -w -s] [geany -imnst] [codium --wait]
git config --global core.filemode false        # Don't interpret file permission as changes
git config --local user.signingKey <key>       # Add signing key
git config --local commit.gpgSign true         # Automatically sign commits
git config --local tag.gpgSign true            # Automatically sign tags
```

### Creation

```text
git init           # Create local repository in the current directory
git init <path>    # Create local repository in <path>
git clone <url>    # Clone repo located at <url>
git clone <url> -n # Don't checkout HEAD after cloning (--no-checkout)
```

### Branches

```text
git checkout <branch>       # Set current directory to <branch>
git checkout <commit>       # Set current directory to <commit>
git branch -d <branch>      # Delete local <branch> (--delete)
git push origin -d <branch> # Delete remote <branch> (--delete)
```

### Staging

```text
git add <file>              # Stage file
git add <dir>               # Stage directory recursively
git add .                   # Stage current directory recursively
git restore --staged <file> # Unstage file
git restore --staged <dir>  # Unstage directory recursively
git restore --staged .      # Unstage current directory recursively
```

### Commits

```text
git commit                   # Commit changes
git commit -m "<msg>"        # Commit with a message (--message)
git commit --amend           # Fix last commit
git commit --amend --no-edit # Amend commit without changing message
git reset --soft HEAD^       # Undo last commit and keep modified files
git reset --hard HEAD^       # Undo last commit and remove modified files
git show <commit>            # Show commit message and diff
```

### Tags

```text
git tag <tag>                  # Tag a commit
git push --tag                 # Push tags to origin
git push --delete origin <tag> # Delete remote tag
```

### Remote

```text
git remote add origin <url>     # Add remote repository located at <url> and named `origin`
git remote set-url origin <url> # Set new <url> for `origin`
git push -u origin <branch>     # Set `origin` as default remote for <branch> and push changes (--set-upstream)
git push --force                # Force the current state to the remote repository
```

### Log

```text
git log                  # Show commit history
git log --oneline        # One commit per line
git log --show-signature # Show signature
git log --pretty=fuller  # Show name/email and date of both author and committer
```

### Worktree

```text
git worktree add -b <branch-name> <path> # Create a new branch and checkout it in a worktree at <path>
git worktree list                        # Show list of worktrees
git worktree remove <branch-name>        # Remove worktree
git worktree prune                       # Prune worktree information
```

## Snippets

```sh
# Remove <file> from every commit
git filter-branch --tree-filter 'rm -f <file>' HEAD

# Remove <dir> from history and delete empty commits
git filter-branch --index-filter 'git rm --cached -r --ignore-unmatch <dir>' --prune-empty -- --all

# Change author's name and email of commits authored by <old-email>
git filter-branch --commit-filter '
    if [ "$GIT_AUTHOR_EMAIL" = "<old-email>" ]; then
        GIT_AUTHOR_NAME="<new-author>";
        GIT_AUTHOR_EMAIL="<new-email>";
        git commit-tree "$@";
    else
        git commit-tree "$@";
    fi' HEAD

# Set name and email of both author and committer for every commits
git filter-branch -f --commit-filter '
    GIT_AUTHOR_NAME="<name>";
    GIT_AUTHOR_EMAIL="<email>";
    GIT_COMMITTER_NAME="$GIT_AUTHOR_NAME";
    GIT_COMMITTER_EMAIL="$GIT_AUTHOR_EMAIL";
    git commit-tree "$@";
' HEAD

# Set timezone to UTC for every commits
git filter-branch -f --env-filter '
    export GIT_AUTHOR_DATE=$(echo "$GIT_AUTHOR_DATE" | sed 's/+[0-9]\{4\}/+0000/')
    export GIT_COMMITTER_DATE=$(echo "$GIT_COMMITTER_DATE" | sed 's/+[0-9]\{4\}/+0000/')
'

# Set the commit date to the author date for all commits
git rebase --committer-date-is-author-date -i --root

# Resign every commit starting at the beginning
git rebase --exec 'git commit --amend --no-edit --no-verify -S' -i --root
```

## Misc

### Always commit code with date in UTC timezone

Add `alias git='TZ=UTC0 git'` to `~/.bash_aliases`
