# Contributing

## Starting with rapid Gitflow

We gonna have 3 primary types of branches: `master` branch, `dev` branch and `features` branches, which are:

- Brach `master` is latest version of workable product. Each increaments will be merged to `master`
  after sprint is finished. And it's always release-able.

- Branch `dev` is branched-off from `master`. When new sprint is started, it will reset to
  latest `master`'s state. And dev team will use this branch to demo their work or play around with other works.

- Branches `features` are changes the team want to make, likely:
  - `feat-x`, `fix-y`, `ref-z`, `chore-a` or
  - `feat-add-login-form`, `fix-bug-on-swap-eth`...

## Choose a base branch

Before starting development, you need to know which branch to base your modifications/additions on. When in doubt, use `master`.

| Type of change    |     |       Branches |
| :---------------- | :-: | -------------: |
| Production ready  |     |       `master` |
| Sprint playground |     |          `dev` |
| New changes       |     | `other-branch` |

Based on feature they work with, create new branch from master, with a team's aligned naming convention, e.g:

- Jira tasks' number, E.g TWCI-21, WP-111, GSS-53 ...
- Features' name, E.g feature-user-login, feature-mail-subscrition, feature-form-contact...
- Grouping by type, E.g feature/GSS-53, task/TWCI-21 , bug/WP-11 ...

```sh
# Switch to the desired branch
git checkout master

# Fech & Pull down any upstream changes
git fetch --all && git pull

# Create a new branch to work on
git checkout -b
git switch --create patch/1234-name-issue
```

Commit your changes, then push to origin with `git push -u` and open a pull request follow template

## Merging changes to production

If there are changes from `master`, e.g Other features being merged, then developers will need to `rebase/merge` (we prefer `rebase`) their working branches with `master` to get those updates (means keep sync with `master`)

When working branches are ready (completed `Definition of DONE`), developers will need others review his work by creating pull-requests for their branches - those PRs will point to `master`.

Whoever do QA assurance will **manually merge** it to `dev` for testing on UAT and check it's compatibility with other features.

If PR is okay, then QA will merge it to `master` (PS: Hitting the `Merge` button!)

If anything wrong, QA will tell `branch owner` to fix it.

After sprint ended, or before new sprint starts, team will reset `dev` to latest `master`, this ensure they're in sync for up-coming features.

![git-work-flow](https://i.gyazo.com/da3d65a35192e21e827b0fd0eb92ffa1.png)
