# Soft Serve Action

![soft-serve-action-banner](https://user-images.githubusercontent.com/42545625/199863722-1a195d17-43f7-4775-b1d9-d2d178b867b2.png)

Synchronize GitHub repositories to your own [Soft Serve](https://github.com/charmbracelet/soft-serve) server on every push with GitHub actions. By the way, [Soft Serve](https://github.com/charmbracelet/soft-serve) is a self-hostable Git server for the command line.

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

      - name: Push to Soft Serve
        uses: charmbracelet/soft-serve-action@master
        with:
          # Repository name on Soft Serve (defaults to GitHub repository name)
          name: foobar
          # The server hosting Soft Serve
          server: my.yummy.server.srv
          # Required only if Soft Serve is configured with authentication
          ssh-key: ${{ secrets.SOFT_SERVE_KEY }}
          # SSH user name, defaults to: git
          ssh-user: abc
          # Port on which the SSH server is running, defaults to: 22
          ssh-port: 23231
          # Whether or not to use git mirror to mirror the repository
          mirror: true

```

## Feedback

We’d love to hear your thoughts on this project. Feel free to drop us a note!

* [Twitter](https://twitter.com/charmcli)
* [The Fediverse](https://mastodon.social/@charmcli)
* [Discord](https://charm.sh/chat)

## License

[MIT](https://github.com/charmbracelet/vhs/raw/main/LICENSE)

***

Part of [Charm](https://charm.sh).

<a href="https://charm.sh/">
  <img
    alt="The Charm logo"
    width="400"
    src="https://stuff.charm.sh/charm-badge.jpg"
  />
</a>

Charm热爱开源 • Charm loves open source
