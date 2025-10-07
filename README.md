# Auto Release Template

[![version][version-img]][version-href]
![prs-welcome][prs-welcome-img]

Template for automated releases with semantic versioning & GitHub Actions.

Prepare a release locally, review it, and then create a GitHub Release automatically when a tag is pushed.

## How It Works

1. Commit changes following [Conventional Commits][conventional-commits-link].
1. Run `npm run release`. This bumps the version, updates `CHANGELOG.md`, creates a commit and a Git tag.
1. Push the changes using `git push --follow-tags`.
1. GitHub Action will automatically create and publish a GitHub Release with the changelog.

## Components

- [absolute-version/commit-and-tag-version][commit-and-tag-version-link] – bumps version, updates `CHANGELOG.md`, creates a commit and a Git tag.
- [yashanand1910/standard-release-notes][standard-release-notes-link] – generates release notes.
- [softprops/action-gh-release][action-gh-release-link] – creates and publishes GitHub Releases.

## Setup

### GitHub Actions

Go to repository settings → **Actions** → **Workflow permissions**, set to **Read and write permissions**.

⚠️ GitHub Actions must have **Read and write** permissions enabled, otherwise the workflow will fail.

### Customization

To customize releases (commit message format, tag prefix, or which commits appear in the changelog), edit the `.versionrc.cjs` file. Full configuration options are in the [Conventional Changelog Config Spec][conventional-changelog-spec-link].


<!-- Badges -->
[version-img]: https://img.shields.io/github/tag/VChet/auto-release-template?label=version&style=flat-square
[version-href]: https://github.com/VChet/auto-release-template/releases
[prs-welcome-img]: https://img.shields.io/badge/PRs-welcome-brightgreen?style=flat-square
<!-- Links -->
[conventional-commits-link]: https://www.conventionalcommits.org/en/v1.0.0
[commit-and-tag-version-link]: https://github.com/absolute-version/commit-and-tag-version
[standard-release-notes-link]: https://github.com/yashanand1910/standard-release-notes
[action-gh-release-link]: https://github.com/softprops/action-gh-release
[actions-quick-start-link]: https://docs.github.com/en/actions/get-started/quickstart
[conventional-changelog-spec-link]: https://github.com/conventional-changelog/conventional-changelog-config-spec/blob/master/versions/2.2.0/README.md
