# Git Code Style and Guidelines

These are the git conventions and guidelines we'll be sticking to across our repos. We use [https://conventionalcommits.org](https://conventionalcommits.org) for branch names and commit messages to enforce consistency and enjoy automatic `CHANGELOG.md` generation.

---

## Branches

Choose short and descriptive names with a conventional commits `type` prefix:

* ```bash
  # Good
  $ git checkout -b feat/oauth-login

  # Bad - too vague
  $ git checkout -b feat/new-login

  # Bad - no `type` prefix
  $ git checkout -b oauth-login
  ```
* Always use a slash to separate the prefix and use hyphens to separate words.

* When several people are working on the same branch, it might be convenient to have personal branches and a team-wide branch. Use the following naming convention:

  ```bash
  # team-wide branch
  $ git checkout -b feat/oauth-login

  # Alice's personal branch
  $ git checkout -b feat/oauth-login/maria  

  # Bob's personal branch
  $ git checkout -b feat/oauth-login/nick
  ```

  Merge the personal branches to the team-wide branch at will. Eventually, the team-wide branch will be merged to `develop`.

* Delete your branch from the upstream repository after it's merged, unless there is a specific reason not to.

  Tip: Use the following command while being on `develop`, to list merged branches:

  ```bash
  $ git branch --merged | grep -v "\*"
  ```

## Commits

Each commit should be a single logical change. Don't make several logical changes in one commit. For example, if a patch fixes a bug and optimizes the performance of a feature, split it into two separate commits.

* Tip: Use`git add -p`to interactively stage specific portions of the modified files.

* Don't split a single logical change into several commits. For example, the implementation of a feature and the corresponding tests should be in the same commit.

* Commit early and often. Small, self-contained commits are easier to understand and revert when something goes wrong.

* Commits should be ordered logically. For example, if commit X depends on changes done in commit Y, then commit Y should come before commit X.

Note: While working alone on a local branch that has not yet been pushed, it's fine to use commits as temporary snapshots of your work. However, it still holds true that you should apply all of the above before pushing it.

## Commit Messages

We use [https://github.com/commitizen](https://github.com/commitizen). Just run `yarn run cz` in your terminal and follow the prompts. Note that all the words in a commit message are in **present tense** except for the first word in the footer, e.g. _Closes_, _Fixes_, etc.

## Merging

**Do not rewrite published history. **The repository's history is valuable in its own right and it is very important to be able to tell what actually happened. Altering published history is a common source of problems for anyone working on the project.

* However, there are cases where rewriting history is legitimate. These are when:

  * You are the only one working on the branch and it is not being reviewed.

  * You want to tidy up your branch, \(e.g. squash commits\), and/or rebase it onto `develop` in order to merge it later.

  That said, never rewrite the history of the `master`, `develop` or any other special branches, \(i.e. used by production or CI/CD servers\).

* Keep the history clean and simple. Just before you merge your branch:

  1. Make sure it conforms to the style guide and perform any needed actions if it doesn't, \(squash/reorder commits, reword messages, etc.\).

  2. Rebase it onto the branch it's going to be merged into:

  ```bash
  [feat/oauth-login] $ git fetch
  [feat/oauth-login] $ git rebase origin/develop
  # Then merge
  ```

## Misc.

Test before you push. Do not push half-done work.

* Use [lightweight tags](http://git-scm.com/book/en/v2/Git-Basics-Tagging#Lightweight-Tags) for personal use, such as to bookmark commits for future reference.

* Keep your repositories in good shape by performing maintenance tasks occasionally:

  * [`git-gc(1)`](http://git-scm.com/docs/git-gc)
  * [`git-prune(1)`](http://git-scm.com/docs/git-prune)
  * [`git-fsck(1)`](http://git-scm.com/docs/git-fsck)



