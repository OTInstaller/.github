## Stop fixing OSINT tools. Start using them.

OTInstaller is the package manager and largest registry built only for OSINT tools: over 130 tools and a set of
investigation guides, free at [otinstaller.com](https://otinstaller.com). One command installs, runs, updates or
removes any of them, and every tool takes the same typed inputs and returns the same JSON.

**otlite** is every popular OSINT tool, managed for you, on Linux and macOS with no Docker:

```sh
curl -fsSL https://get.otinstaller.com/otlite | sh
otlite init                         # creates ~/.otlite; accept once
otlite install sherlock             # own virtualenv, tested version
otlite run sherlock -- u:johndoe    # saved by tool, target and time
```

**`ot`** runs every tool in the registry, on Windows too, each in a locked-down container (needs Docker or Podman):

```sh
curl -fsSL https://get.otinstaller.com/ot | sh         # macOS and Linux
irm https://get.otinstaller.com/ot.ps1 | iex           # Windows (PowerShell)
ot run osintverse-community/holehe e:ada@example.com   # installs it on first use, then runs it
```

[Getting started](https://otinstaller.com/docs/getting-started) ·
[otlite](https://otinstaller.com/otlite) ·
[CLI reference](https://otinstaller.com/docs/cli) ·
[Security model](https://otinstaller.com/docs/security)

### What it replaces

| Job | Today | With OTInstaller |
| --- | --- | --- |
| Install a tool | Clone it, find a Python it still works with, untangle requirements that conflict | `otlite install sherlock` or `ot install osintverse-community/holehe` |
| Run it | Read each README for its flags | The same typed inputs for every tool: `u:` `e:` `d:` `p:` `ip:` `url:` |
| Use the results | Text, CSV, HTML and JSON, a different shape per tool | Every run saved under `results/` in one JSON shape, ready for scripts and AI agents |
| Keep API keys | Config files, `.env` files and shell history | One place; each tool gets only the keys it declares |
| Keep it working | Find out a tool broke in the middle of a case | `ot outdated` and `ot update --all`; broken tools are flagged on their page |
| Trust it | Run a stranger's script with full access to your files | Pinned, signature-checked, scanned and run in a container that can't read your files |
| Remove it | Leftovers in your system Python | `otlite remove sherlock` or `ot uninstall osintverse-community/holehe` |

### Repositories

| Repository | What it is |
| --- | --- |
| [otinstaller](https://github.com/OTInstaller/otinstaller) | The open-source code: `ot` (Go), otlite (Python), the registry API, the manifest spec, the scanner and the seed |
| [ot](https://github.com/OTInstaller/ot) | Signed release downloads of `ot` |
| [agent-plugin](https://github.com/OTInstaller/agent-plugin) | The plugin for Claude Code and Cursor: open-source OSINT tools for AI agents, with your consent |
| [feedback](https://github.com/OTInstaller/feedback) | Bug reports and ideas for the registry, the website, `ot` and otlite |
| [osintverse-community](https://github.com/osintverse-community) | The launch seed: first-party tools, community wrappers of third-party tools, and guides |

### For AI agents

`ot mcp install claude` (or `claude-desktop`, `cursor`, `vscode`, `codex`, `gemini`) adds a local MCP server that
searches, installs and runs tools on your machine. The agent asks you before any run that goes online, touches a
target or involves a person's identifiers, and every run is written to a local audit log. The remote server at
`https://api.otinstaller.com/mcp` searches the registry and reads guides with nothing installed.
[AI agents and MCP](https://otinstaller.com/docs/agents).

### Publish a tool or a guide

`ot init` writes a starter manifest, Dockerfile and release workflow, and `ot import <repository-url>` drafts one for
a project that already exists. Every release is validated and security-scanned (signature, Trivy, GuardDog and a
sandboxed smoke test) before it is published. [Publishing](https://otinstaller.com/docs/publishing).

### Get in touch

- Bugs and ideas: [OTInstaller/feedback](https://github.com/OTInstaller/feedback/issues), or `ot feedback "..."`.
- A problem with a published tool: **Report a problem** on its page on otinstaller.com.
- A security problem in OTInstaller itself: email security@otinstaller.com instead of opening an issue.
- Anything else: support@otinstaller.com.

<sub>Apache License 2.0 · for lawful investigation, within the
[acceptable use policy](https://otinstaller.com/policy/acceptable-use) · by [OSINTverse](https://osintverse.com)</sub>
