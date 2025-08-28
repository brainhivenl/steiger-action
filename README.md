# Steiger GitHub Action

A GitHub Action to run [Steiger](https://github.com/brainhivenl/steiger) commands in your CI/CD pipeline. Steiger is a high-performance container build orchestrator with native Bazel and Docker BuildKit.

## Usage

```yaml
name: Check Architecture
on: [push, pull_request]

jobs:
  steiger:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: brainhivenl/steiger-action@v1
        with:
          cmd: build
          args: --strict
          version: v0.0.1
```

## Inputs

| Input     | Description                      | Required | Default  |
| --------- | -------------------------------- | -------- | -------- |
| `cmd`     | Command to run                   | Yes      | `build`  |
| `args`    | Arguments to pass to the command | No       | `""`     |
| `version` | Version of Steiger to use        | No       | `v0.0.1` |

## Examples

### Basic usage

```yaml
- uses: brainhivenl/steiger-action@v1
```

### With custom command and arguments

```yaml
- uses: brainhivenl/steiger-action@v1
  with:
    cmd: check
    args: --verbose --config steiger.config.js
```

### With specific version

```yaml
- uses: brainhivenl/steiger-action@v1
  with:
    cmd: build
    version: v0.1.0
```

## Requirements

- This action runs on Linux runners only (uses `x86_64-unknown-linux-gnu` binary)
- Your repository should be checked out before using this action

## How it works

1. Downloads the specified version of Steiger from GitHub releases
2. Extracts and makes the binary executable
3. Runs the specified command with the provided arguments

## License

[MIT](LICENSE)
