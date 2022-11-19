# actions

Shared Github Actions Workflows

Most jobs expect a Personal Access Token to be set as an organizational secret named `GH_ORG_TOKEN` which has permissions for:
* repo
* write:packages

You can generate this token here: https://github.com/settings/tokens/new?scopes=repo,read:packages

## Example

### Github Release

*.github/workflows/release.yaml*
```yaml
name: release
on:
  push:
    branches:
    - main

jobs:

  release:
    uses: CloudNativeEntrepreneur/actions/.github/workflows/github-release.yaml@main
    secrets: inherit
    with:
      docker: true # optional, set to build/release a Dockerfile
      helm: true # optional, set to release helm chart
```

### Node Quality

*.github/workflows/pr.yaml*
```yaml
name: Pull Request

on:
  pull_request:
    branches: [ main ]

jobs:

  quality:
    uses: CloudNativeEntrepreneur/actions/.github/workflows/node-quality.yaml@main
```

### Node Semantic Release

Release an NPM library with semantic-release.

*.github/workflows/release.yaml*
```yaml
name: Release

on:
  push:
    branches:
      - main

jobs:
  
  release:
    uses: CloudNativeEntrepreneur/actions/.github/workflows/node-semantic-release.yaml@main
    secrets: inherit
```

