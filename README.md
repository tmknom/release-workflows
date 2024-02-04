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

## Related projects

- [template-composite-action](https://github.com/tmknom/template-composite-action): Template repository for Composite Action.
- [template-reusable-workflows](https://github.com/tmknom/template-reusable-workflows): Template repository for Reusable Workflows.

## Release notes

See [GitHub Releases][releases].

## License

Apache 2 Licensed. See [LICENSE](LICENSE) for full details.

[releases]: https://github.com/tmknom/release-workflows/releases
