# Cleaner

## Usage

```yaml
name: Clean

on:
  workflow_dispatch:
  schedule:
    - cron: '0 0 * * *'

jobs:
  delete-deployments:
    name: Delete deployments
    runs-on: ubuntu-latest

    steps:
      - name: Delete deployments
        uses: apoiston/actions@cleaner
        with:
          cloudflare_account_id: ${{ secrets.CLOUDFLARE_ACCOUNT_ID }}
          cloudflare_api_token: ${{ secrets.CLOUDFLARE_API_TOKEN }}
          project_name: 'project name'
          delete_deployments_days: '7'
          enable_delete_deployments: true

  delete-releases:
    name: Delete releases
    runs-on: ubuntu-latest
    permissions:
      contents: write

    steps:
      - name: Checkout
        uses: actions/checkout@main
        with:
          fetch-depth: 0

      - name: Delete releases
        uses: apoiston/actions@cleaner
        with:
          delete_releases_days: '7'
          enable_delete_releases: true          
```
