# Humanizer — Installation & Usage

Rewrite AI-sounding text so it reads like the writer without changing what it says. This document explains how to install and use the Humanizer skill. The upstream project is `blader/humanizer`. This repository, `wangxin116/humanizer-install`, contains a copy of `SKILL.md` and these installation instructions. The sections below identify which repository each installation method uses.

## Requirements / Prerequisites

- A skills-capable agent or environment that supports Markdown-based skills (examples: Skills CLI, local agent frameworks, Claude plugin marketplaces).
- Git (optional, for cloning the repo).
- Node.js / npm available if using certain CLI installers (some installers use npx).
- Basic familiarity with running commands in a terminal.

## Quick install (recommended)

The following Skills CLI examples install from the upstream repository, `blader/humanizer`, if your skills manager supports this pattern. To install the copy included in this repository, use the manual installation instructions below.

```bash
# global install for the current user (example)
npx skills add blader/humanizer --global

# or install for the current project only (omit --global)
npx skills add blader/humanizer
```

Notes:
- Use `--agent <name>` or `--agent '*'` if your CLI supports targeting a specific agent.
- After installation, reload or restart your agent so it picks up the new skill.
- The skill registers the `/humanizer` command (or equivalent) in environments that expose skill commands.

## Install as a plugin (example: Claude plugin marketplace)

The following example targets the upstream repository's plugin marketplace, `blader/humanizer`; it does not install from this distribution repository. Use it only if your platform supports that marketplace and command syntax:

```text
/plugin marketplace add blader/humanizer
/plugin install humanizer@humanizer
```

Then invoke the plugin with its command (platform-dependent), for example:
- `/humanizer` or `/humanizer:humanizer`

## Manual install (download / local install)

1. Clone this distribution repository or download its ZIP:

```bash
git clone https://github.com/wangxin116/humanizer-install.git
cd humanizer-install
```

The following steps use the `SKILL.md` included in this repository. The upstream project is available at https://github.com/blader/humanizer.

2. Copy the SKILL.md (or the repository contents) into your agent's skills directory as required by your agent:
- e.g. paste `SKILL.md` into a `skills/` folder, or add the repo as an installed skill per your agent docs.

3. Restart or reload the agent so it discovers the new skill.

## File mode and embedding

Humanizer supports multiple response modes as described in [SKILL.md](./SKILL.md):

- Pasted text (default)
  - Returns: the draft, a short list of remaining patterns, and the final rewrite.

- File mode
  - When the user names a file (e.g., `docs/guide.md`), the skill performs the full edit process and writes only the final text to that file.
  - The skill changes prose only. It preserves code blocks, inline code, commands, paths, YAML metadata, data, tables, and other machine-parsable content.

- Embedded mode
  - When used by another task (PR description, commit message, or other automation), the skill returns only the final rewritten text.

Adapt the exact invocation to your agent’s file-mode syntax (e.g., `/humanizer file:docs/guide.md` or a UI file action).

## Usage examples

1. Quick paste:
```
/humanizer
Please humanize this text:
[PASTE AI-GENERATED TEXT HERE]
```

2. Voice matching:
```
/humanizer
Here's a writing sample:
[PASTE WRITING SAMPLE HERE]
Now humanize this text:
[PASTE AI-GENERATED TEXT HERE]
```
- If you provide a writing sample, the skill will match sentence length, word choice, punctuation, openings, and transitions.

3. File rewrite:
```
/humanizer docs/launch-post.md
```
- Runs the full edit flow, then writes the final prose back to the named file (platform must support file editing).

## Behavior & guarantees

- The Humanizer skill rewrites AI-sounding text to read like the writer while keeping the original meaning.
- It does not invent facts, names, dates, numbers, or citations. Do not expect it to add new factual content.
- The skill follows the editing rules in [SKILL.md](./SKILL.md) (see that file for the full list of patterns it targets: staging, rhythm by rule, inflation, formatting, leftovers, etc.).

## Testing & verification

- After installation, test with a short sample to confirm the command is available:
```
/humanizer
Humanize: "This is not just a change, it's a revolution. The impact will be huge."
```
- Confirm the returned draft and final rewrite meet your expectations. For file mode, check that code blocks and metadata were preserved.

## Troubleshooting

- Skill command not found:
  - Ensure the agent was reloaded after installation.
  - Confirm the skill file (SKILL.md) is placed in the correct skills directory for your agent.
  - Check agent logs for skill-loading errors.

- Rewrites add or drop facts:
  - The skill should not add facts. If you see additions, provide a more specific prompt or include a writing sample to anchor style without changing facts.

- Platform-specific issues:
  - Consult your agent/platform documentation for how to register or enable Markdown skills or plugins.
  - For plugin marketplace issues, ensure the marketplace has the correct package identifier and permissions.

## Contributing & source

- Upstream project: https://github.com/blader/humanizer
- Current distribution repository and installation instructions: https://github.com/wangxin116/humanizer-install
- Included skill: [SKILL.md](./SKILL.md)
- License: MIT
- Version metadata in the included [SKILL.md](./SKILL.md): 3.0.0

## Example install.md changelog (optional)
- 2026-09-14 — Initial generated install.md (based on SKILL.md from the upstream project, blader/humanizer)
