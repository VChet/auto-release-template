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

## Publishing to NPM

### NPM package manager

If you want to publish the package automatically, you can use the [npm-publish action][npm-publish-action-link]. Pay attention to the **You probably don't need this!** section if you want to trigger the action differently or use a different package manager. A more advanced scenario using GitHub Release is described below.

### NPM Publishing via GitHub Release & PNPM package manager

#### Draft GitHub Release

If you're confident your releases are ready, you can skip this step.

I suggest adding a `draft` flag to the *Create GitHub Release* step in the `release.yaml` workflow, so that `npm publish` runs only after you manually review and publish the release.

```diff
  - name: Create GitHub Release
    with:
      ...
+     draft: true
```

#### Workflow

See [publish-workflow-link] for an example workflow that publishes the package after the GitHub Release goes public. This workflow uses `pnpm` and sets the `NPM_CONFIG_PROVENANCE` flag to generate provenance statements. You can read more about [provenance statements here][npm-provenance-link].

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
[npm-publish-action-link]: https://github.com/marketplace/actions/npm-publish
[publish-workflow-link]: ./examples/publish.example.yaml
[npm-provenance-link]: https://docs.npmjs.com/generating-provenance-statements
