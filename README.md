# gocredits-action

GitHub Action for [Songmu/gocredits](https://github.com/Songmu/gocredits)

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
    - uses: actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v4.2.2
    - uses: actions/setup-go@0aaccfd150d50ccaeb58ebd88d36e91967a5f35b # v5.4.0
      with:
        go-version-file: go.mod
    - name: Install dependencies
      shell: bash
      run: go mod tidy
    - uses: yasu89/gocredits-action@de0d1b0dbcf41cbb27ef205029e65454045790ee # v1.0.0
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
    - uses: actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v4.2.2
    - uses: actions/setup-go@0aaccfd150d50ccaeb58ebd88d36e91967a5f35b # v5.4.0
      with:
        go-version-file: go.mod
    - name: Install dependencies
      shell: bash
      run: go mod tidy
    - uses: yasu89/gocredits-action@de0d1b0dbcf41cbb27ef205029e65454045790ee # v1.0.0
      with:
        mode: 'update'
```

See [action.yml](https://github.com/yasu89/gocredits-action/blob/main/action.yml) for more details on how to configure it.
