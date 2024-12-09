# Release to GitHub Releases

Releases artifacts to GitHub Releases for simple projects.

## Description

This reusable workflow automates release processes that do not require build steps, such as compilation.
It handles version updates, tag creation, and artifact publishing to GitHub Releases, ensuring secure, consistent, and efficient releases.
It is ideal for Composite Actions, Reusable Workflows, and standard workflows in GitHub Actions.

## Key Features

- **Automatic Versioning**: Updates version numbers (patch, minor, major) based on your input.
- **Version Tagging**: Creates and pushes new version tags to the repository.
- **GitHub Releases Integration**: Uploads artifacts, generates release notes, and publishes them to GitHub Release.

## Benefits

- **Complete Automation**: Reduces manual tasks and human errors by automating the entire release process.
- **Proven Reliability**: Ensures consistent results with the tested workflow, eliminating uncertainty.
- **Enhanced Security**: Operates with least permissions to minimize risks and protect your projects.
- **Easy Integration**: Adapts seamlessly to various projects, enabling efficient and standardized workflows across repositories.

## Usage

To use this workflow in your repository, call it from another workflow and specify the `bump-level` input:

```yaml
name: Release
on:
  workflow_dispatch:
    inputs:
      bump-level:
        type: choice
        required: true
        description: Bump up to [patch / minor / major]
        options:
          - patch
          - minor
          - major

jobs:
  call:
    uses: tmknom/release-workflows/.github/workflows/github-releases.yml@v0
    with:
      bump-level: ${{ inputs.bump-level }}
    permissions:
      contents: write
```

## Related projects

N/A
