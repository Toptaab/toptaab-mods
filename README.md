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

## Mods

- **[token-garden](https://github.com/Toptaab/token-garden)**: a live forecast of the context window and rate limits, in the band above the prompt.
- **[agent-roster](https://github.com/Toptaab/agent-roster)**: a live pane of every agent in the session, each a pixel Clawd at work, with its tokens and status.

## Adding a mod

Give the mod its own repository, then add an entry to `.claude-plugin/marketplace.json`:

```json
{ "name": "<mod>", "source": { "source": "github", "repo": "Toptaab/<mod>" }, "description": "<one line>" }
```

Check it with `claude plugin validate .`.
