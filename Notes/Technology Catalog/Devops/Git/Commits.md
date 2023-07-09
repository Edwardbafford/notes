
Commit is a snapshot of the current repository state.

Commits are chained together by pointing to their predecessors.

Snapshots of the index are stored in the object store.

Git compares the current index with the previous commit to find changed or added files which are added as new blobs. Unchanged file already exist as blobs and are re-used.

Comparisons are done using the SHA1 hashes which allow for quick analysis.

Commits are usually created by developers but can be created by git automatically in certain situations.


## Reference

#### Commit Name

SHA1 hash ID is globally unique and matches to a single commit.

Because prior commit state is used in created the hash, the line of development can be trusted to match globally as well.

#### References

References point to a commit.

Use a reference to identify a commit.

References have full names and are stored hierarchically within the repository.

Three reference namespaces:
- `refs/heads/..` for local branches
- `refs/remotes/..` for remote branches
- `refs/tags/..` for tags

Can use the full reference or last section.

Using the abbreviated version of the name can result in ambiguity which git will try to figure out with a heuristic.

#### Relative Commits

Reference a commit relative to another commit.

Given commit, C
- `C^` and `C^1` is the commits first parent
- `C^n` is the commits nth parent
- `C~n` is the commits nth ancestor

These can be chained together.


## History

`git show COMMIT`

Inspect a specific commit

`git log`

View a history of commits

Added a commit to the log command will show all commits reachable from the commit specified.

Commits reference their parents, creating a DAG, which is what git will traverse when logging.

`-n` to limit the number shown

`--pretty=<oneline,short,medium,full>` to control the amount of information logged

`--pretty=format:"..."` to create a custom logging format

`--abbrev-commit` to abbreviate the SHA1 hash IDs

`--oneline` to combine `--pretty=oneline` and `--abbrev-commit`

`-p` to show the changes introduced by the commit

`--stat` to show which files changed along with number of lines changed

`--graph` to show branches and merges across commits in graphical fashion

`start..end` to specify a start commit and end commit for the log. This will take all commits find-able from `end` and remove all commits find-able from `start`.

`A...B` to find all commits that are find-able from A or find-able from B but not find-able from both!

Append multiple commits to log to view all find-able commits from all listed commits.

Use negate notation `^` to remove commits find-able from the negated commit.


