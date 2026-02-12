# Auto Release Template

[![version][version-img]][version-href]
![prs-welcome][prs-welcome-img]

Template for automated releases with semantic versioning & GitHub Actions.

Prepare a release locally, review it, and the workflow will automatically create a GitHub Release when a tag is pushed.

## How It Works

1. Commit your changes following the [Conventional Commits][conventional-commits-link].
1. Run `npm run release`, which bumps the version, updates `CHANGELOG.md`, creates a commit, and adds a Git tag.
1. Push the changes using `git push --follow-tags`.
1. The GitHub Action detects the new tag and publishes a GitHub Release with the generated changelog.

## Components

- [absolute-version/commit-and-tag-version][commit-and-tag-version-link] – bumps version, updates `CHANGELOG.md`, creates a commit and a Git tag.
- [yashanand1910/standard-release-notes][standard-release-notes-link] – generates release notes.
- [softprops/action-gh-release][action-gh-release-link] – creates and publishes GitHub Releases.

## Customization

To customize commit message formatting, tag prefix, or which commits appear in the changelog, edit the [.versionrc.cjs](.versionrc.cjs) file.

For the full list of supported options, check the [Conventional Changelog Config Spec][conventional-changelog-spec-link].

### Advanced

More use cases and workflow examples are documented [in the wiki][wiki-link].

<!-- Badges -->
[version-img]: https://img.shields.io/github/tag/VChet/auto-release-template?label=version&style=flat-square
[version-href]: https://github.com/VChet/auto-release-template/releases
[prs-welcome-img]: https://img.shields.io/badge/PRs-welcome-brightgreen?style=flat-square
<!-- Links -->
[conventional-commits-link]: https://www.conventionalcommits.org/en/v1.0.0
[commit-and-tag-version-link]: https://github.com/absolute-version/commit-and-tag-version
[standard-release-notes-link]: https://github.com/yashanand1910/standard-release-notes
[action-gh-release-link]: https://github.com/softprops/action-gh-release
[conventional-changelog-spec-link]: https://github.com/conventional-changelog/conventional-changelog-config-spec/blob/master/versions/2.2.0/README.md
<!-- Wiki -->
[wiki-link]: https://github.com/VChet/auto-release-template/wiki
