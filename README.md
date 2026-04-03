> [!TIP]
> The features of this plugin are - since version [2.6.0-alpha3](https://github.com/camunda/c8ctl/releases/tag/v2.6.0-alpha.3) - shipped as default plugin with [c8ctl](https://github.com/camunda/c8ctl). Hence this repo was archived.

# c8ctl-plugin-c8run

A [c8ctl](https://github.com/camunda/c8ctl) plugin that provides an opinionated way to download, start, and stop a local Camunda 8 cluster using [c8run](https://docs.camunda.io/docs/self-managed/setup/deploy/local/c8run/).

## Installation

```bash
c8ctl load plugin --from https://github.com/MaxTru/c8ctl-plugin-c8run
```

## Usage

```bash
# Start a local Camunda 8 cluster (downloads c8run automatically if needed)
c8ctl c8run start

# Start with a specific version
c8ctl c8run start 8.9.0-alpha5

# Start with debug output (streams raw c8run logs)
c8ctl c8run start --debug

# Stop the running cluster
c8ctl c8run stop
```

## How it works

1. **Download**: Automatically downloads the correct c8run binary for your platform from the Camunda Download Center
2. **Cache**: Stores downloaded binaries in a platform-specific cache directory
3. **Start**: Launches c8run in the background and waits for the cluster to become healthy
4. **Stop**: Gracefully shuts down the running cluster

### Cache locations

| Platform | Path |
|----------|------|
| macOS    | `~/Library/Caches/c8run/` |
| Linux    | `~/.cache/c8run/` |
| Windows  | `%LOCALAPPDATA%\c8run\cache\` |

Set `C8RUN_CACHE_DIR` environment variable to override.

## Supported platforms

- macOS (x86_64, aarch64)
- Linux (x86_64, aarch64)
- Windows via WSL

## Contributor

Idea and code from this repo from @bojtospeter.

## License

MIT
