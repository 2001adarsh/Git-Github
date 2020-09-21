# Git-Github

# Git

Everything about git. Including basic concepts, git flow, git commit specification, git plugin, and common problem solving

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

## Concept

> Don't memorize the command, but know the principle behind the command, that is, what exactly is happening behind the command.


It is said to be a Distributed Version Control, compared to traditional Centralized Version Control systems such as SVN.
Git has the concept of local and remote repositories. So it involves the synchronization of local and remote warehouses.

You can view the address information of the remote branch with the following command:

`` 
git: (daily / 0.1.0) git remote -v
origin http://gitlab.test.com/f/test.git (fetch)
origin http://gitlab.test.com/f/test.git (push)  
`` 

Git is to build a tree structure based on objects. Associate files with hashing.

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
| `git diff` | See changes |
| `git diff --staged` | See changes (on staged files) |

### Branching & Merging

| Command | Description |
| ------- | ----------- |
| `git branch` | List branches (the asterisk denotes the current branch) |
| `git branch -a` | List all branches (local and remote) |
| `git branch [branch name]` | Create a new branch |
| `git branch -d [branch name]` | Delete a branch |
| `git push origin --delete [branch name]` | Delete a remote branch |
| `git checkout -b [branch name]` | Create a new branch and switch to it |
| `git checkout -b [branch name] origin/[branch name]` | Clone a remote branch and switch to it |
| `git branch -m [old branch name] [new branch name]` | Rename a local branch |
| `git checkout [branch name]` | Switch to a branch |
| `git checkout -` | Switch to the branch last checked out |
| `git checkout -- [file-name.txt]` | Discard changes to a file |
| `git merge [branch name]` | Merge a branch into the active branch |
| `git merge [source branch] [target branch]` | Merge a branch into a target branch |
| `git stash` | Stash changes in a dirty working directory |
| `git stash clear` | Remove all stashed entries |

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

### Common scenarios and solutions

> The premise is that you need to understand the basic concepts above

1. How do I roll back a submission?

If you need to roll back a commit, you can submit a new commit to reverse the content of that commit.
This is exactly what git revert commit-id does.

2. How do I roll back to a commit?

Theoretically we can use git revert HEAD, git revert HEAD ^ 1 ...
But this is more troublesome, you can do it through git reset commit-id.

This operation is different from git revert. It directly points the pointer to the commit-id, forcing a change in the commit history.
Rather than creating a new commit, doing so is risky, so you need to force it when pushing to a remote location. git push --force

> If you want to go back to the previous version after reset after git reset. It can be viewed through git reflog, and then rolled back again through git reset commit-id.
If you think of git commit as a game archive, then git reflog is an archive record

3. I'm working on a feature and I have a bug online. But the function is half-written and cannot be submitted. What should I do?

The contents of the workspace can be stored by git stash. Then switch the new branch to complete the bug fix, switch to the unfinished branch again, execute
git stash pop restores unfinished work to the workspace.
