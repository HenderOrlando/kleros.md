## Releases, Versions, and Changelog

Whenever the `develop` branch is ready to become a new release. We run `yarn run standard-version` which looks at the conventional commit messages since the last semver git tag and bumps the version accordingly. It then updates the `CHANGELOG.md`, commits, and tags the commit with the new version tag. See [https://github.com/conventional-changelog/standard-version](https://github.com/conventional-changelog/standard-version) for more info.



