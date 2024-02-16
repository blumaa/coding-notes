
## Git

Add to current commit and don’t change title

`git commit --amend --no-edit`

How to rebase

`git rebase from origin/main`

`git rebase -i HEAD~10`

How to squash commits

`git reset --soft HEAD~1`

`git commit specific files`

`git push --force-with-lease`

when editing a commit

`git commit --amend`

`git commit --continue`

see all commits for a branch

`git log --oneline`

Or, git shortlog, which groups commits by user, again showing just the subject line for concision

How to update Main Branch

`git fetch`

`git rebase origin/main`

git rebase origin/main (puts most recent changes on main before your current changes/commits)

git push --force-with-lease (necessary after we rebase or modify our git history)

### interactive rebase

git rebase -i HEAD~10

git reset --soft HEAD~1 (used to split our current commit, the soft option keeps the files so we can used them to make more commits)

How change from https to ssh:

`git remote **set**-url origin git@github.com:{USERNAME}/{PROJECTNAME}.git`

## Heroku Consoles

Access Rails console from Staging

`heroku run rails c -a localyzestaging`

————————————————————————————
