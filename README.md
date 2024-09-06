### Sample Action
```yaml
name: build and deploy

on:
  push:
    branches:
      - test
      - staging
      - production
      - devops/citests/* 

jobs:
  build:
    uses: bitbool-actions/workflows-node/.github/workflows/docker-build-deploy.yml@main
    permissions:
      contents: read
    with:
      NODE_VERSION: "21.4"
      USE_YARN: false
      DOCKER_USER: "<username>"
      DOCKER_REPO: "<username>/<reponame>"
      DOCKER_REGISTRY: "docker.io"
    secrets:
      DOCKER_PASSWORD: ${{ secrets.DOCKER_PASSWORD }}
      AUTH_TOKEN: ${{ secrets[format('AUTH_TOKEN_{0}', github.ref_name)] }}
```
