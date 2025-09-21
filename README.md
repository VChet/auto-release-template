# Auto Release Template

Template for automated releases with semantic versioning & GitHub Actions.

Prepare release locally, review, then publish automatically on tag push.

## How It Works

1. Commit changes following [Conventional Commits][conventional-commits-link].
1. Run `npm run release`. This bumps the version, updates `CHANGELOG.md`, creates a commit and a Git tag.
1. Push changes `git push --follow-tags`.
1. GitHub Action will automatically create and publish a GitHub Release with the changelog.

## Components

- [absolute-version/commit-and-tag-version][commit-and-tag-version-link] – bumps version, updates `CHANGELOG.md`, creates a commit and a Git tag.
- [yashanand1910/standard-release-notes][standard-release-notes-link] – generates release notes.
- [softprops/action-gh-release][action-gh-release-link] – creates and publishes GitHub Releases.

## Setup

### GitHub Actions

⚠️ **Important:** GitHub Actions must have **Read and write** permissions enabled, otherwise the workflow will fail.

- Enable [GitHub Actions][actions-quick-start-link].
- Go to repository settings → **Actions** → **Workflow permissions**, set to **Read and write permissions**.
- Ensure developers have push access for tags.

### Customization

To customize releases (commit message format, tag prefix, or which commits appear in the changelog), edit the `.versionrc` file. Full configuration options are in the [Conventional Changelog Config Spec][conventional-changelog-spec-link].

<!-- Links -->
[conventional-commits-link]: https://www.conventionalcommits.org/en/v1.0.0
[commit-and-tag-version-link]: https://github.com/absolute-version/commit-and-tag-version
[standard-release-notes-link]: https://github.com/yashanand1910/standard-release-notes
[action-gh-release-link]: https://github.com/softprops/action-gh-release
[actions-quick-start-link]: https://docs.github.com/en/actions/get-started/quickstart
[conventional-changelog-spec-link]: https://github.com/conventional-changelog/conventional-changelog-config-spec/blob/master/versions/2.2.0/README.md
