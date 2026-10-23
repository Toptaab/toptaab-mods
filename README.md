# toptaab-mods

A Claude Code plugin marketplace: Claude Code mods by Toptaab. Each mod lives in its own repository; this one only lists them.

## Install

```
/plugin marketplace add Toptaab/toptaab-mods
/plugin install <mod>@toptaab-mods
/reload-plugins
```

From a shell:

```
claude plugin marketplace add Toptaab/toptaab-mods
claude plugin install <mod>@toptaab-mods
```

In the desktop app, where `/plugin` does not run: click + next to the prompt box, then Plugins, Add marketplace with `Toptaab/toptaab-mods`, then Add plugin.

If the marketplace is already added, run `claude plugin marketplace update toptaab-mods` to see new mods. If you added `toptaab-mods` earlier from `Toptaab/token-garden`, remove it first: `claude plugin marketplace remove toptaab-mods`.

### Install every mod

`claude plugin install` takes one plugin at a time, so loop over the list:

```
claude plugin marketplace add Toptaab/toptaab-mods
for p in token-garden agent-roster; do claude plugin install "$p@toptaab-mods"; done
```

Or paste this prompt into Claude Code:

```
Install every mod from https://github.com/Toptaab/toptaab-mods
```

### For agents

If you are an AI agent asked to install these mods, they are Claude Code plugins listed in the `Toptaab/toptaab-mods` marketplace. Do not clone the repositories or copy files by hand. Run these shell commands, in order:

1. `claude plugin marketplace add Toptaab/toptaab-mods`. If it is already added, run `claude plugin marketplace update toptaab-mods` instead; if it was added from `Toptaab/token-garden`, run `claude plugin marketplace remove toptaab-mods` first.
2. `claude plugin list --available --json`, and take every entry under `available` whose `marketplaceName` is `toptaab-mods`. Mods already installed are left out of that list. If the user asked for all mods, install each one; if they named some, install only those.
3. For each mod: `claude plugin install <name>@toptaab-mods`.

Then tell the user which mods were installed and to type `/reload-plugins` or restart the session; you cannot run that yourself.

## Mods

- **[token-garden](https://github.com/Toptaab/token-garden)**: a live forecast of the context window and rate limits, in the band above the prompt.
- **[agent-roster](https://github.com/Toptaab/agent-roster)**: a live pane of every agent in the session, each a pixel Clawd at work, with its tokens and status.

## Adding a mod

Give the mod its own repository, then add an entry to `.claude-plugin/marketplace.json`:

```json
{ "name": "<mod>", "source": { "source": "github", "repo": "Toptaab/<mod>" }, "description": "<one line>" }
```

Check it with `claude plugin validate .`.
