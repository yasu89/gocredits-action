# gocredits-action

GitHub Action for [gocredits](https://github.com/Songmu/gocredits)

# Synopsis

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
    - uses: yasu89/gocredits-action@v0.0.1
```
