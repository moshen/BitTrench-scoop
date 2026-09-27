# BitTrench scoop bucket

A [Scoop](https://scoop.sh) bucket for
[BitTrench](https://github.com/moshen/BitTrench), so a Windows install updates
with `scoop update` instead of a download and an unzip.

## Install

```powershell
scoop bucket add bittrench https://github.com/moshen/BitTrench-scoop
scoop install bittrench
```

Later:

```powershell
scoop update bittrench
```

## Configuration

`bittrench` will not start without a `config.toml`. The install directory holds
a `config.sample.toml` to copy - `scoop prefix bittrench` prints where that is.

The first of these that exists is used:

1. `.\config.toml`, relative to wherever you run it
2. `%USERPROFILE%\.config\bittrench\config.toml`
3. `%ProgramData%\bittrench\config.toml`

Prefer the second. Scoop versions the install directory, so a config left
beside the binary is replaced by the next update, while `%USERPROFILE%` is
untouched. `-config <path>` overrides all three.

## How this bucket is updated

`bucket/bittrench.json` is written by the Release workflow in
[moshen/BitTrench](https://github.com/moshen/BitTrench), which pushes here with
a deploy key on every release. It rewrites `version`, the asset `url` and its
`hash`, so edits to those fields are overwritten - change the manifest upstream
in that workflow instead.
