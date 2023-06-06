---
title: "GitHub Pages"
date: 2023-06-02
weight: 5
description: >
  GitHub Pages for Docsy
---

## Deploy to GitHub Pages

> <https://docs.github.com/en/pages>

### Ensure `package-lock.json` file has been committed

> If not, then create amd commit `package-lock.json`!

```shell
npm install
```

### Publishing with a custom GitHub Actions workflow

> - <https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site#publishing-with-a-custom-github-actions-workflow>
> - <https://gohugo.io/hosting-and-deployment/hosting-on-github/>
> - <https://github.com/actions/starter-workflows/blob/main/pages/hugo.yml>

1. On GitHub, navigate to your site's repository.
2. Under your repository name, click Settings. If you cannot see the "Settings" tab, select the dropdown menu, then click Settings.
3. In the "Code and automation" section of the sidebar, click Pages.
4. Under "Build and deployment", under "Source", select GitHub Actions.
5. GitHub will suggest several starter workflows. Select suggested `Hugo Starter Workflow`, which automatically creates `.github/workflows/hugo.yml`
6. To see your published site, under Pages, click Visit site.

#### `.github/workflows/hugo.yml`

> <https://github.com/gohugoio/hugo/releases>

```yaml
# Sample workflow for building and deploying a Hugo site to GitHub Pages
name: Deploy Hugo site to Pages

on:
  # Runs on pushes targeting the default branch
  push:
    branches: ["master"]

  # Allows you to run this workflow manually from the Actions tab
  workflow_dispatch:

# Sets permissions of the GITHUB_TOKEN to allow deployment to GitHub Pages
permissions:
  contents: read
  pages: write
  id-token: write

# Allow only one concurrent deployment, skipping runs queued between the run in-progress and latest queued.
# However, do NOT cancel in-progress runs as we want to allow these production deployments to complete.
concurrency:
  group: "pages"
  cancel-in-progress: false

# Default to bash
defaults:
  run:
    shell: bash

jobs:
  # Build job
  build:
    runs-on: ubuntu-latest
    env:
      HUGO_VERSION: 0.113.0
    steps:
      - name: Install Hugo CLI
        run: |
          wget -O ${{ runner.temp }}/hugo.deb https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/hugo_extended_${HUGO_VERSION}_linux-amd64.deb \
          && sudo dpkg -i ${{ runner.temp }}/hugo.deb
      - name: Install Dart Sass Embedded
        run: sudo snap install dart-sass-embedded
      - name: Checkout
        uses: actions/checkout@v3
        with:
          submodules: recursive
      - name: Setup Pages
        id: pages
        uses: actions/configure-pages@v3
      - name: Install Node.js dependencies
        run: "[[ -f package-lock.json || -f npm-shrinkwrap.json ]] && npm ci || true"
      - name: Build with Hugo
        env:
          # For maximum backward compatibility with Hugo modules
          HUGO_ENVIRONMENT: production
          HUGO_ENV: production
        run: |
          hugo \
            --minify \
            --baseURL "${{ steps.pages.outputs.base_url }}/"
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v1
        with:
          path: ./public

  # Deployment job
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v2
```
