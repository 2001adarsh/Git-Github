# Git-Github

# Git

Everything about git. Including basic concepts, git flow, git commit specification and git plugin.

It is said to be a Distributed Version Control, compared to traditional Centralized Version Control systems such as SVN.
Git has the concept of local and remote repositories. So it involves the synchronization of local and remote warehouses.


## Writing Commit messages:
Commit message style guide for Git

The first line of a commit message serves as a summary.  When displayed
on the web, it's often styled as a heading, and in emails, it's
typically used as the subject.  As such, you should capitalize it and
omit any trailing punctuation.  Aim for about 50 characters, give or
take, otherwise it may be painfully truncated in some contexts.  Write
it, along with the rest of your message, in the imperative tense: "Fix
bug" and not "Fixed bug" or "Fixes bug".  Consistent wording makes it
easier to mentally process a list of commits.

Oftentimes a subject by itself is sufficient.  When it's not, add a
blank line (this is important) followed by one or more paragraphs hard
wrapped to 72 characters.  Git is strongly opinionated that the author
is responsible for line breaks; if you omit them, command line tooling
will show it as one extremely long unwrapped line.  Fortunately, most
text editors are capable of automating this.

:q

For more information as to how to write meaningful commits, visit <a href = "https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/Documentation/process/submitting-patches.rst?id=HEAD"> here</a> and <a href = "https://thoughtbot.com/blog/5-useful-tips-for-a-better-commit-message">here too!!</a>

## So Some Common Git Commands which can come very handy.

### Getting & Creating Projects

| Command | Description |
| ------- | ----------- |
| `git init` | Initialize a local Git repository |
| `git clone ssh://git@github.com/[username]/[repository-name].git` | Create a local copy of a remote repository |

### Basic Snapshotting

| Command | Description |
| ------- | ----------- |
| `git status` | Check status |
| `git add [file-name.txt]` | Add a file to the staging area |
| `git add -A` | Add all new and changed files to the staging area |
| `git add -p` | See changes before adding to staging area |
| `git commit -m "[commit message]"` | Commit changes |
| `git commit -a -m <message>` | Directly commiting the tracked files before adding to stating area |
| `git rm -r [file-name.txt]` | Remove a file (or folder) |
| `git mv [file-name.txt] [new-file-name.txt]` | Move/Rename a file (or folder) |
| `git diff` | See changes |
| `git diff --staged` | See changes (on staged files) |


### Branching, Merging & Reverting

| Command | Description |
| ------- | ----------- |
| `git branch` | List branches (the asterisk denotes the current branch) |
| `git branch -a` | List all branches (local and remote) |
| `git branch [branch name]` | Create a new branch |
| `git branch -d [branch name]` | Delete a branch (gives error if the branch is not fully merged -D to be used)|
| `git push origin --delete [branch name]` | Delete a remote branch |
| `git checkout -b [branch name]` | Create a new branch and switch to it |
| `git checkout -b [branch name] origin/[branch name]` | Clone a remote branch and switch to it |
| `git branch -m [old branch name] [new branch name]` | Rename a local branch |
| `git checkout [branch name]` | Switch to a branch |
| `git checkout -` | Switch to the branch last checked out |
| `git checkout -- [file-name.txt]` | Discard changes to a file which is Unstaged |
| `git reset [branch name (HEAD)] [file-name.txt]` | Discard changes to a file which is staged with respect to currently checked out branch |
| `git reset -p` | Ask which recent changes to discard |
| `git merge [branch name]` | Merge a branch into the active branch |
| `git merge [source branch] [target branch]` | Merge a branch into a target branch |
| `git stash` | Stash changes in a dirty working directory |
| `git stash clear` | Remove all stashed entries |
| `git commit --amend` |  modify and add changes to the most recent commit (Best to use Locally only)|
| `git revert HEAD` | create new commit with inverse changes of last commit (rollback) |
| `git revert commit-id` | revert the commit of the respective commit id |


### Sharing & Updating Projects

| Command | Description |
| ------- | ----------- |
| `git push origin [branch name]` | Push a branch to your remote repository |
| `git push -u origin [branch name]` | Push changes to remote repository (and remember the branch) |
| `git push` | Push changes to remote repository (remembered branch) |
| `git push origin --delete [branch name]` | Delete a remote branch |
| `git pull` | Update local repository to the newest commit |
| `git pull origin [branch name]` | Pull changes from remote repository |
| `git remote add origin ssh://git@github.com/[username]/[repository-name].git` | Add a remote repository |
| `git remote set-url origin ssh://git@github.com/[username]/[repository-name].git` | Set a repository's origin branch to SSH |

### Inspection & Comparison

| Command | Description |
| ------- | ----------- |
| `git log` | View changes |
| `git log --summary` | View changes (detailed) |
| `git log -p`  -"p for patch" | View changes (detailed) |
| `git show commitID` | View changes (individual changes) |
| `git show --stat` | View changes (stats) |
| `git log --oneline` | View changes (briefly) |
| `git diff [source branch] [target branch]` | Preview changes before merging |
| `git branch` | List all branches |

### .gitignore files
.gitignore files are used to tell the git tool to intentionally ignore some files in a given Git repository. For example, this can be useful for configuration files or metadata files that a user may not want to check into the master branch. Check out more at: https://git-scm.com/docs/gitignore.

