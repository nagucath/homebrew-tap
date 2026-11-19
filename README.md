# nagucath Homebrew tap

Patched CLIProxyAPI and network packages. The key-policy plugin ships from its own repository releases.

## Install

The standard `cliproxyapi` formula builds the patched host from the
`nagucath/cpa-plugin-key-policy` monorepo's `main` branch. The monorepo has
not published a versioned host release yet, so install the rolling formula with
`--HEAD`.

```sh
brew tap nagucath/tap
brew install --HEAD nagucath/tap/cliproxyapi
```

The default host configuration is installed at
`$(brew --prefix)/etc/cliproxyapi.conf`. The key-policy plugin is distributed
separately from the [plugin repository releases](https://github.com/nagucath/cpa-plugin-key-policy/releases).
Put its platform library in a private plugins directory, set that directory as
`plugins.dir`, and enable `cpa-key-policy`. See the
[plugin example](https://github.com/nagucath/cpa-plugin-key-policy/blob/main/config.example.yaml)
for the complete shape.

Start the service with:

```sh
brew services start nagucath/tap/cliproxyapi
```

## Update

Fetch the latest patched host with:

```sh
brew update
brew upgrade --fetch-HEAD nagucath/tap/cliproxyapi
brew services restart nagucath/tap/cliproxyapi
```
