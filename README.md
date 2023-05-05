# Action Node.js with `node_modules` cache

GitHub Action for setting up Node.js via [actions/setup-node](https://github.com/actions/setup-node) with [actions/cache](https://github.com/actions/cache) to cache `node_modules`.

## Usage

```yaml
jobs:
  main:
    name: Use Node.js
    runs-on: ubuntu-latest
    steps:
      - name: Setup Node.js with cache
        id: node-with-cache
        uses: flipgroup/action-nodejs-with-module-cache@main
        with:
          version-file: .nvmrc
          # alternatively, use `version` input
          #version: 18.x
          additional-cache-path: ~/add/another/path # optional input argument
          cache-key-suffix: key-suffix              # optional input argument
      - name: Install npm packages
        if: steps.node-with-cache.outputs.cache-hit != 'true'
        run: npm ci
```
