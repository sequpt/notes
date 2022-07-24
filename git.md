# git

OpenSSH remote login client

- Website: <https://git-scm.com/>
- Repo: <https://git.kernel.org/pub/scm/git/git.git>
- Mirror: <https://github.com/git/git>

## Installation

- Debian: `sudo apt-get install git`

## Usage

### Configuration

```text
git config --global user.name "<name>"        : Set <name> globally
git config --global user.email "<email>"      : Set <email> globally
git config --local user.name "<name>"         : Set <name> locally
git config --local user.email "<email>"       : Set <email> locally
git config --global core.editor "<editor-cmd>": [gedit -w -s] [geany -imnst] [codium --wait]
git config --global core.filemode false       : Don't interpret file permission as changes
git config --local user.signingKey <KEY>      : Add signing key
git config --local commit.gpgSign true        : Automatically sign commits
```

### Creation

```text
git init       : Create local repository in the current directory
git init <path>: Create local repository in <path>
```

### Branches

```text
git checkout <branch>      : Set current directory to <branch>
git checkout <commit>      : Set current directory to <commit>
git branch -d <branch>     : Delete local <branch> (--delete)
git push origin -d <branch>: Delete remote <branch> (--delete)
```

### Staging

```text
git add <file>             : Stage file
git add <dir>              : Stage directory recursively
git add .                  : Stage current directory recursively
git restore --staged <file>: Unstage file
git restore --staged <dir> : Unstage directory recursively
git restore --staged .     : Unstage current directory recursively
```

### Commits

```text
git commit                  : Commit changes
git commit -m "<msg>"       : Commit with a message (--message)
git commit --amend          : Fix last commit
git commit --amend --no-edit: Amend commit without changing message
git reset --soft HEAD^      : Undo last commit and keep modified files
git reset --hard HEAD^      : Undo last commit and remove modified files
git tag <tag>               : Tag a commit
git push --tag              : Push tags to origin
```

### Remote

```text
git remote add origin <url>    : Add remote repository located at <url> and named `origin`
git remote set-url origin <url>: Set new <url> for `origin`
git push -u origin <branch>    : Set `origin` as default remote for <branch> and push changes (--set-upstream)
```

### Log

```text
git log          : Show commit history
git log --oneline: One commit per line
```
