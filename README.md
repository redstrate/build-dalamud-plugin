# build-dalamud-plugin

A simple action for building simple plugins. Can be used on both GitHub and Forgejo.

## Example (GitHub)

Here is the simplest workflow to build a plugin:

```yml
name: Build

on:
  push:
  pull_request:

jobs:
  build:
    name: "Build"
    runs-on: ubuntu-latest
    
    steps:
      - uses: actions/checkout@v4
      - name: Build Plugin
        uses: redstrate/build-dalamud-plugin@main
```

## Example (Forgejo)

Here is the simplest workflow to build a plugin:

```yml
name: Build

on:
  push:
  pull_request:

jobs:
  build:
    name: "Build"
    runs-on: docker
    container:
      image: ghcr.io/catthehacker/ubuntu:act-22.04

    steps:
      - name: Checkout
        uses: actions/checkout@v4
      - name: Build Plugin
        uses: https://github.com/redstrate/build-dalamud-plugin@main
```

Notice that the `uses` directive changed (because your instance is not on GitHub's domain) and you need to explicitly specify a container image. I chose that specific Ubuntu image because it has `node` and `git` pre-installed.
