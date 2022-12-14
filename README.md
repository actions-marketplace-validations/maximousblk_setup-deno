# Setup Deno

GitHub Action to set up Deno.

# Usage

### Inputs

- `deno-version` - Deno version.
  - values: `<semver>`, `<commit>`, `'canary'` or `'latest'`
  - default: `'latest'`

### Outputs

- `version` - tag of the installed Deno binary
- `deno_path` - path of the installed Deno binary

# Examples

Basic:

```yml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - name: Setup Deno
        uses: maximousblk/setup-deno@v2 # Installs latest version

      - run: deno -V
```

Matrix:

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        deno: ['v1.23.0', 'v1.23.x', '1.x', '1', 'latest', 'canary']

steps:
  - uses: actions/checkout@v3

  - name: Setup Deno (${{ matrix.deno }})
    uses: maximousblk/setup-deno@v2
    with:
      deno-version: ${{ matrix.deno }}

  - run: deno -V
```

## License

This project is licensed under [The MIT License](./LICENSE)
