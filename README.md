# Ghostty

A [URI](https://github.com/uri-life/uri) patchset for [Ghostty](https://github.com/ghostty-org/ghostty).

## Quick start

Install [`uri`](https://github.com/uri-life/uri), clone this repository, move into the repository directory, and run:

```sh
uri apply v1.3.1 minacle1.0 --ephemeral
uri apply v1.3.1 zeroday0619_1.0 --ephemeral
```

Each command creates a separate isolated workspace for Ghostty `v1.3.1`, applies the selected patchset, and reports the location and ID of the created workspace. Use `minacle1.0` for the existing macOS patches and `zeroday0619_1.0` for the SSH terminfo fallback patch. When you are finished, remove each workspace with:

```sh
uri vanish <ID>
```
