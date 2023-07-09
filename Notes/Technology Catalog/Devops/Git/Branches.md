
Branches are used for working on separated lines of development.

New branches can be created from a current branch and merged into other branches.

Common uses
- Stages of development lifecycle
- Implementing complex features

Names
- default branch name is `master` but can be configured to something else
- can organize branches using hierarchical naming with `/`
- cannot end with a `/`
- cannot start with `.` or `-`
- cannot contain `..`, whitespace, or character with special meaning in git


## Creating

Working directory will show documents in the state of the current active branch.

Branch name points to a commit, representing the most recent commit for that branch.

When creating a branch it must start by pointing to a commit. Default is the commit of the current commit.

`git branch <NAME> <START>`


## Listing

Branches have no order

`git branch`

Shows branches with an asterisk for the branch currently checked into.

View remote branches with `-r` and remote and local with `-a`

`git show-branch`

Shows branches in a more detailed view
- `*` denotes current branch
- `!` denotes other branch
- Current commit message shown

List of commits are shown in descending order
- `+` shows a commit is in a non-active branch
- `*` shows a commit is in the active branch
- `-` is a merge commit
- message shows the branch the commit originated from
- last commit is the first commit where all branches contain the commit

Use `--more=<NUM>` to show specific number of commits

Only show some branches by extending command with branch names or filtering with wildcard matching.


## Switching

`git checkout <BRANCH>`

`<BRANCH>` is now the current checked out branch.

Changes working directory to match branch commit. 

Untracked files are left alone.

Issues a warning if changed files exist before checking out. If forced using `-f` this data will be lost. This included staged files.

Try to merge local operations into into the target branch with `-m`. This does not create a commit but can create merge conflicts.

Use `-b` to create a new branch then checkout into it all in one operation. A start point can be added as an argument.

### HEAD

Head points to the current checked out commit which is usually the same commit that a branch is pointing to.

`git checkout <SHA/TAG/BRANCH>`

A detached HEAD is created when checking out a commit that is not referenced by a branch.

`git branch` will show a detached HEAD.

An untracked commit is a commit with a reference - tag, branch, or other commit.

Untracked commits will be removed by git daemon processes.

A detached HEAD can create untracked commits by commiting off of commits in the middle of a branch.


## Deleting

`git branch -d <BRANCH>`

Cannot be the currently checked out branch.

Git prevents you from deleting branches that have unique commits. This can be overridden with `-D` flag.

