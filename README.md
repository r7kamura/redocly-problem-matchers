# redocly-problem-matchers

GitHub Action to setup [Problem Matchers](https://github.com/actions/toolkit/blob/1cc56db0ff126f4d65aeb83798852e02a2c180c3/docs/problem-matchers.md) for [redocly/openapi-cli](https://github.com/Redocly/openapi-cli).

## Usage

Add this action as a step before running openapi-cli:

```yaml
name: test

on:
  pull_request:
  push:
    branches:
      - main

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
        with:
          ref: ${{ github.event.pull_request.head.sha }}
      - uses: r7kamura/redocly-problem-matchers@v1
      - uses: mhiew/redoc-lint-github-action@v2
        with:
          args: schema.oas.yml --format stylish
        env:
          NO_COLOR: '1'
```

Note: `NO_COLOR=1` and `--format stylish` are required for this problem matchers to work well.

### Screenshot

![screenshot](/images/screenshot.png)
