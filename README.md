# release-workflows

A collection of release workflows.

## Description

A collection of release workflows implemented as Reusable Workflows for GitHub Actions.

## Usage

### Reusable Workflows

```yaml
jobs:
  call:
    uses: tmknom/release-workflows/.github/workflows/reusable-workflows.yml@v0
    with:
      level: ${{ inputs.level }}
    permissions:
      contents: write
```

## Release notes

See [GitHub Releases][releases].

## License

Apache 2 Licensed. See [LICENSE](LICENSE) for full details.

[releases]: https://github.com/tmknom/release-workflows/releases
