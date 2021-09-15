# Soft-Serve Action

A Github Action that synchronize repositories to your own [soft-serve](https://github.com/charmbracelet/soft-serve) server.

## Example

```yaml
name: Soft-Serve

on:
  push:
    branches:
      - master

jobs:
  soft-serve:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v2
        with:
          fetch-depth: 0 # git cannot push a shallow clone

      - name: Push to Soft-Serve
        uses: charmbracelet/soft-serve-action@master
        with:
          server: my.soft-serve.srv
          ssh-key: ${{ secrets.SOFT_SERVE_KEY }} # only required if soft-serve is configured to accept certain keys only
          name: foobar # soft-serve repository name (defaults to current repository name)
```

## License

[MIT](https://github.com/charmbracelet/soft-serve-action/raw/master/LICENSE)

***

Part of [Charm](https://charm.sh).

<a href="https://charm.sh/"><img alt="the Charm logo" src="https://stuff.charm.sh/charm-badge-unrounded.jpg" width="400"></a>

Charm热爱开源 • Charm loves open source
