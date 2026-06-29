# autoresearch

Agents and skills for coordinating AI research loops in the Meridian ecosystem.

## Releasing

Use `mars version` (or `meridian -C "$PWD" mars version`) for releases:

```bash
mars version patch --push       # 0.1.2 → 0.1.3, commit, tag, push
mars version minor --push       # 0.1.3 → 0.2.0
```

This bumps `mars.toml`, promotes CHANGELOG.md `[Unreleased]` to the new
version, commits, tags, and optionally pushes. Write changelog entries under
`[Unreleased]` as you work — `mars version` handles the rest.

**Meridian session roots:** Meridian spawns resolve `MERIDIAN_TASK_DIR` for the
checkout where source work happens, but `MERIDIAN_PROJECT_DIR` stays anchored to
the session control root for state, profiles, and context. Nested
`meridian ...` commands use project-root resolution, so CWD alone may not target
this package. For package releases, pass the package root explicitly:

```bash
meridian -C "$PWD" mars version patch --push
```

Use explicit `-C <package-root>` whenever running Meridian commands for this
package from an inherited Meridian environment. For task checkouts, prefer
`meridian -C "$MERIDIAN_TASK_DIR" ...`.

### After Release

Downstream repos pick up new versions via:

```bash
meridian mars add autoresearch@vX.Y.Z
meridian mars sync
```

## Structure

```text
agents/           # Agent profiles (.md with YAML frontmatter)
skills/           # Skill definitions (SKILL.md + optional resources/)
mars.toml         # Package manifest
mars.lock         # Generated local lock — ignored, do not track
.mars/            # Generated — do not edit directly
```

## Editing

Edit source files only:

- Agent definitions: `agents/*.md`
- Skills: `skills/*/SKILL.md` and their resources

Do not edit `.mars/`. Regenerate it with `meridian mars sync`.
Do not edit generated target directories such as `.agents/`, `.claude/`,
`.codex/`, `.cursor/`, or `.opencode/`; source changes will overwrite them.

## Validation

From this package root:

```bash
meridian mars check
meridian mars sync
```

When running from an inherited Meridian session, prefer an explicit package root:

```bash
meridian -C "$PWD" mars check
meridian -C "$PWD" mars sync
```
