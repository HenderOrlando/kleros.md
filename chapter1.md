# Contributing

We use Github issues, projects, and milestones to track development work. Every repo has its own automated Kanban board and the general contribution flow goes like this:

1. Changes are proposed in an issue on the project's repo.
2. Discussion takes place and someone gets assigned to the issue.
3. The issue gets added to the repo's Kanban board and to a milestone, \(we run milestones from Monday to Monday to align with open dev meetings\).
4. The assignee creates a new branch on the project's repo and submits a pull request to `develop` when ready.
5. Travis runs linters, formatters, tests, and [https://coveralls.io](https://coveralls.io) to report on coverage changes.
6. The pull request is merged once all the changes are reviewed and accepted, and any requested changes are made.

The branch `develop` builds to staging and the branch `master` builds to production. We merge `develop` into `master` whenever we release a new version of the repo's package and/or app.

