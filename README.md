# Auto Release Template

This repository demonstrates a fully automated release workflow using `npm run release` and GitHub Actions.

⚠️ Make sure GitHub Actions have **write access** enabled, otherwise the workflow will fail. See the [Repository Settings](#repository-settings) section below.

## Features

- **Automatic versioning**: Running `npm run release` automatically determines the next semantic version.
- **Changelog generation**: Generates a `CHANGELOG.md` based on conventional commits.
- **Local commit & tag**: All changes, including version bump, changelog update, and Git tag, happen locally — no automatic push is performed, so you can review everything before publishing.
- **GitHub release on push**: After manually pushing the tag to GitHub, a GitHub Action will automatically create a GitHub release with the generated changelog.

## Repository Settings

This is required so that GitHub Actions can create GitHub releases.

- Go to `https://github.com/%owner%/%repository%/settings/actions`
- In **Workflow permissions**, select **Read and write permissions**

## Customizing Releases

If you want to adjust how releases are generated — for example, changing the commit message format, tag prefix, or which commits appear in the changelog — you can edit the `.versionrc` file.
See the [Conventional Changelog Configuration Spec][conventional-changelog-spec-link] for all available options.

## Usage

1. Make changes in your repository and commit following the [Conventional Commits convention][conventional-commits-link].
1. Run the release script `npm run release`.
1. Push the generated tag to GitHub `git push --follow-tags`.
1. The GitHub Action will automatically create a GitHub Release with the changelog.

<!-- Links -->
[conventional-changelog-spec-link]: https://github.com/conventional-changelog/conventional-changelog-config-spec/blob/master/versions/2.2.0/README.md
[conventional-commits-link]: https://www.conventionalcommits.org/en/v1.0.0
