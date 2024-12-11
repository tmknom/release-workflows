# release-workflows

Collection of release workflows.

## Description

A collection of release workflows implemented as Reusable Workflows for GitHub Actions.
It provides the following workflows:

- **GitHub Releases**: Releases artifacts to GitHub Releases for simple projects.
- **Go**: Releases Go-based CLI tools using [GoReleaser][GoReleaser].

## Usage

### GitHub Releases

This reusable workflow automates release processes that do not require build steps, such as compilation.
It handles version updates, tag creation, and artifact publishing to GitHub Releases, ensuring secure, consistent, and efficient releases.

```yaml
jobs:
  call:
    uses: tmknom/release-workflows/.github/workflows/github-releases.yml@v0
    with:
      bump-level: ${{ inputs.bump-level }}
    permissions:
      contents: write
```

### Go

This reusable workflow automates the release process for Go-based CLI tools using [GoReleaser][GoReleaser].
It handles versioning, building, signing, and publishing artifacts such as binaries and container images.

```yaml
jobs:
  call:
    uses: tmknom/release-workflows/.github/workflows/go.yml@v0
    with:
      bump-level: ${{ inputs.bump-level }}
    permissions:
      contents: write
      packages: write
      id-token: write
      attestations: write
```

## Related projects

- [template-composite-action](https://github.com/tmknom/template-composite-action): Template repository for Composite Action.
- [template-reusable-workflows](https://github.com/tmknom/template-reusable-workflows): Template repository for Reusable Workflows.
- [template-go](https://github.com/tmknom/template-go): Template repository for Go.

## Release notes

See [GitHub Releases][releases].

## License

Apache 2 Licensed. See [LICENSE](LICENSE) for full details.

[releases]: https://github.com/tmknom/release-workflows/releases
[GoReleaser]: https://goreleaser.com/
