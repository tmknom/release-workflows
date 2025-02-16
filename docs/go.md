# Release Go

Releases Go-based CLI tools using GoReleaser.

## Description

This reusable workflow automates the release process for Go-based CLI tools using [GoReleaser][GoReleaser].
It handles versioning, building, signing, and publishing artifacts such as binaries, container images, and provenance data.
It automates the entire release process, ensuring secure, consistent, and efficient releases.
With built-in security features like keyless signing via [Cosign][Cosign], it simplifies compliance with modern software supply chain standards.

### Key Features

- **Automatic Versioning**: Updates version numbers (patch, minor, major) based on your input.
- **Cross-Platform Builds**: Compiles binaries for Linux, Windows, macOS, and architectures like x86_64 and arm64.
- **Container Image Publishing**: Publishes multi-architecture container images (amd64, arm64) to GitHub Container Registry.
- **Reproducible Builds**: Ensures consistent outputs across builds by enforcing reproducibility standards such as `SOURCE_DATE_EPOCH` and Go's `-trimpath` flag.
- **Keyless Signing**: Signs binaries, container images, and checksum files using [Cosign][Cosign].
- **Artifact Attestation**: Generates cryptographically signed provenance and SBOMs (Software Bill of Materials).
- **GitHub Releases Integration**: Creates Git tags, uploads artifacts, and generates release notes to GitHub Releases.

## Benefits

- **Complete Automation**: Reduces manual tasks and human errors by automating the entire release process.
- **Broad Platform Compatibility**: Builds for multiple OSs and architectures, increasing accessibility and reach.
- **Enhanced Security**: Signs artifacts to ensure their authenticity and integrity.
- **Auditable Build Process**: Provides cryptographic proofs for all artifacts, guarantee compliance and traceability.
- **Streamlined Homebrew Support**: Automatically updates Homebrew formulae, making it easier for macOS users to install and update your software.
- **Effortless Release Management**: Adapts seamlessly to Go projects, enabling efficient and standardized workflows across repositories.

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
    uses: tmknom/release-workflows/.github/workflows/go.yml@v0
    with:
      bump-level: ${{ inputs.bump-level }}
    permissions:
      contents: write
      packages: write
      id-token: write
      attestations: write
```

<!-- actdocs start -->

## Inputs

| Name | Description | Type | Default | Required |
| :--- | :---------- | :--- | :------ | :------: |
| bump-level | Determines which part of the version to increment [patch/minor/major] | `string` | n/a | yes |
| go-version-file | Path to the version file for Go, such as .go-version, go.mod or go.work. | `string` | `go.mod` | no |

## Secrets

N/A

## Outputs

N/A

## Permissions

| Scope        | Access |
| :----------- | :----- |
| contents     | write  |
| packages     | write  |
| id-token     | write  |
| attestations | write  |

<!-- actdocs end -->

## Related projects

- [GoReleaser][GoReleaser]: Builds Go binaries for several platforms.
- [Cosign][Cosign]: Signs binaries and container images using [Sigstore](https://sigstore.dev/)

[GoReleaser]: https://goreleaser.com/
[Cosign]: https://github.com/sigstore/cosign
