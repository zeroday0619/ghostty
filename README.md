# Ghostty

A [URI](https://github.com/uri-life/uri) patchset for [Ghostty](https://github.com/ghostty-org/ghostty).

## Quick start

Install [`uri`](https://github.com/uri-life/uri), clone this repository, move into the repository directory, and run:

```sh
uri apply tip zeroday0619_1.0 --ephemeral
```

This command creates an isolated workspace for Ghostty `tip`, applies the inherited patch graph, and reports the location and ID of the created workspace. Local sessions keep `TERM=xterm-ghostty`. When Ghostty shell integration is active, its `ssh` wrapper uses `TERM=xterm-256color` by default. The optional `ssh-terminfo` feature may select `xterm-ghostty` after a successful installation or cache hit.

The upstream `tip` tag tracks continuous releases and may move. This graph was generated against `3c1ef5b32fc5ea6b93d28493fabf193f595139cf`; regenerate and revalidate it whenever the tag changes.

Direct `/usr/bin/ssh`, `command ssh`, unsupported shells, and disabled shell integration bypass the wrapper. When you are finished, remove the workspace with:

```sh
uri vanish <ID>
```

## Build `tip` on macOS

Ghostty `tip` currently requires Zig `0.16.0`. Follow the upstream macOS workflow:

```sh
zig version
macos/build.nu --configuration ReleaseLocal --action build
```

## Pinned `v1.3.1`

The previous pinned graph remains available:

```sh
uri apply v1.3.1 zeroday0619_1.0 --ephemeral
```

## Author patches with URI

Use [URI `2.0.0-rc.5`](https://github.com/uri-life/uri/releases/tag/v2.0.0-rc.5) to generate patch files. Do not run `git format-patch` directly. URI reconstructs and validates the selected feature before replacing its patch transactionally.

```sh
uri expand . tip zeroday0619_1.0 <FEATURE> --ephemeral <ID>
```

Edit, stage, and commit the feature changes in the workspace reported by URI. The worktree must be clean before generating the patch:

```sh
uri collapse --ephemeral <ID>
```

Successful collapse writes `versions/tip/patches/zeroday0619_1.0/<FEATURE>.patch` and removes the ephemeral workspace. Use `--recursive` only when dependency patches must also be regenerated.
