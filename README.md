# Deploy to StaticHost.eu - GitHub Action

A GitHub Action to deploy static sites to [StaticHost.eu](https://www.statichost.eu).

## Inputs

| Input | Required | Description |
|-------|----------|-------------|
| `api-token` | Yes | StaticHost.eu API token |
| `site-name` | Yes | Name of the site on StaticHost.eu |
| `path` | Yes | Path to the directory to deploy |

## Usage

```yaml
- uses: tournament.io/deploy-statichost-action@v1
  with:
    api-token: ${{ secrets.STATICHOST_API_TOKEN }}
    site-name: my-site
    path: ./dist
```

### Full workflow example

```yaml
name: Deploy

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Build
        run: npm ci && npm run build

      - name: Deploy to StaticHost.eu
        uses: tournament.io/deploy-statichost-action@v1
        with:
          api-token: ${{ secrets.STATICHOST_API_TOKEN }}
          site-name: my-site
          path: ./dist
```

## API Token

Create an API token at [builder.statichost.eu/account](https://builder.statichost.eu/account), then add it as a repository secret named `STATICHOST_API_TOKEN`.
