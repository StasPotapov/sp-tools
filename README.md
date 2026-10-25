# sp-tools

A [Claude Code plugin marketplace](https://code.claude.com/docs/en/plugins/install) with my tools.
Add it once, then install any plugin from it by name. [Русская версия](README.ru.md).

| Plugin | What it does |
|---|---|
| [adbm](https://github.com/StasPotapov/adbm) | The agent drives Android devices and emulators with deterministic commands instead of raw adb, plus visual before/after checks |
| [present](https://github.com/StasPotapov/present) | From an idea to an offline HTML slide deck with a presenter window, a run-through and trimming to time |
| [git-xfer](https://github.com/StasPotapov/git-xfer) | Moves commits between two unrelated git repositories |

## Install

In a Claude Code session:

```
/plugin marketplace add StasPotapov/sp-tools
/plugin install adbm@sp-tools
```

Or from the shell:

```bash
claude plugin marketplace add StasPotapov/sp-tools
claude plugin install adbm@sp-tools
```

Each plugin's README lists what it needs on the machine (for example, adbm needs `adb` and Pillow).

**No GitHub SSH key?** Claude Code clones over SSH when `ssh -T git@github.com` works. Without a key,
set `CLAUDE_CODE_PLUGIN_PREFER_HTTPS=1` in your environment, otherwise installs from `/plugin` and
updates fail.

## Updates

Every plugin here points at a release tag, such as `v1.2.0`. Commits between releases do not reach you.

- **Automatic:** `/plugin` → **Marketplaces** → `sp-tools` → **Enable auto-update**. Claude Code then
  checks for new releases in the background after a session starts.
- **By hand:** `/plugin marketplace update sp-tools`, then `/plugin update adbm@sp-tools`.

## Moving from a per-repo marketplace

Earlier each plugin was its own marketplace (`adbm@adbm`, `present@present`, `git-xfer@git-xfer`).
Those still work, but they follow the `main` branch instead of releases. To switch:

```
/plugin uninstall adbm@adbm
/plugin marketplace remove adbm
/plugin install adbm@sp-tools
```

Do not keep both: the skill then loads twice.

## License

MIT for this catalog. Each plugin has its own license in its repository.
