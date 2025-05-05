# gocredits-action

GitHub Action for [gocredits](https://github.com/Songmu/gocredits)

# Usage

## Check credits file

Configuration to fail the Actions workflow if there are differences in the CREDITS file output by gocredits.

```yaml
# .github/workflows/gocredits.yml
name: gocredits
on:
  push:
    branches:
      - main
  pull_request:
jobs:
  gocredits:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v4
    - uses: actions/setup-go@v5
      with:
        go-version: stable
    - uses: yasu89/gocredits-action@v1
```

## Update credits file

Configuration to update and commit the CREDITS file if there are differences in the CREDITS file output by gocredits.

```yaml
# .github/workflows/gocredits.yml
name: gocredits
on:
  push:
    branches:
      - main
  pull_request:
jobs:
  gocredits:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
    - uses: actions/checkout@v4
    - uses: actions/setup-go@v5
      with:
        go-version: stable
    - uses: yasu89/gocredits-action@v1
      with:
        mode: 'update'
```

See [action.yml](https://github.com/yasu89/gocredits-action/blob/main/action.yml) for more details on how to configure it.
