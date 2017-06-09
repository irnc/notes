# git rebase notes

Steps:

- checkout branch to be rebased
- run `git rebase origin/master`

Diff and UI notes:

- remote refers to rebased branch
- local refers to base branch
- diff shows local above, remote below
  - first it is commit hash of a local commit (from a base branch)
  - local changes, than separator, remote changes (from a rebased branch)
  - and closing is a commit message from a commit to be rebased
- first diff column is for remote, second is for local
