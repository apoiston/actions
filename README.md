# Builder

## Usage

```yaml
jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout
        uses: actions/checkout@main

      - name: Build
        uses: apoiston/actions@builder
        with:
          private_key: ${{ secrets.PRIVATE_KEY }}
          public_key: ${{ secrets.PUBLIC_KEY }}
```
