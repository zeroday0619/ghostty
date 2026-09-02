# Ghostty

A [URI](https://github.com/uri-life/uri) patchset for [Ghostty](https://github.com/ghostty-org/ghostty).

## Quick start

Install [`uri`](https://github.com/uri-life/uri), clone this repository, move into the repository directory, and run:

```sh
uri apply v1.3.1 zeroday0619_1.0 --ephemeral
```

This command creates an isolated workspace for Ghostty `v1.3.1`, applies the full inherited patch graph, and reports the location and ID of the created workspace. When you are finished, remove the workspace with:

```sh
uri vanish <ID>
```

## Build on macOS

Ghostty `v1.3.1` requires Zig `0.15.2`. The patch graph includes compatibility fixes for Xcode 27 and its macOS 27 SDK.

```sh
brew install zig@0.15
/opt/homebrew/opt/zig@0.15/bin/zig build -Doptimize=ReleaseFast
```

## Author patches with URI

Use [URI `2.0.0-rc.5`](https://github.com/uri-life/uri/releases/tag/v2.0.0-rc.5) to generate patch files. Do not run `git format-patch` directly. URI reconstructs and validates the selected feature before replacing its patch transactionally.

```sh
uri expand . v1.3.1 zeroday0619_1.0 <FEATURE> --ephemeral <ID>
```

Edit, stage, and commit the feature changes in the workspace reported by URI. The worktree must be clean before generating the patch:

```sh
uri collapse --ephemeral <ID>
```

Successful collapse writes `versions/v1.3.1/patches/zeroday0619_1.0/<FEATURE>.patch` and removes the ephemeral workspace. Use `--recursive` only when dependency patches must also be regenerated.
