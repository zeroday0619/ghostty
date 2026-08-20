# Ghostty

A [URI](https://github.com/uri-life/uri) patchset for [Ghostty](https://github.com/ghostty-org/ghostty).

## Quick start

Install [`uri`](https://github.com/uri-life/uri), clone this repository, move into the repository directory, and run:

```sh
uri apply v1.3.1 minacle1.0 --ephemeral
```

This command creates an isolated workspace for Ghostty `v1.3.1`, applies the full regular patch graph, and reports the location and ID of the created workspace. When you are finished, remove the workspace with:

```sh
uri vanish <ID>
```
