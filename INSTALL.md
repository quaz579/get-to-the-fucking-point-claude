# How to install

<details>
<summary><strong>Antigravity (<code>agy</code>)</strong></summary>

### Install

```bash
agy plugin install https://github.com/quaz579/get-to-the-fucking-point-claude
```

### Verify

```bash
agy plugin list
```

### Update

```bash
agy plugin uninstall get-to-the-fucking-point-claude
agy plugin install https://github.com/quaz579/get-to-the-fucking-point-claude
```

### Uninstall

```bash
agy plugin uninstall get-to-the-fucking-point-claude
```

Or keep it installed and turn it off: `agy plugin disable get-to-the-fucking-point-claude`.

### Always-on (optional)

Add to `~/.gemini/GEMINI.md`:

```markdown
## Output style

The reader has ADHD. Shape every response so it can be acted on:

1. Lead with the answer or next action: command, path, or snippet first.
2. Number multi-step work; one bounded action per step.
3. End with one next action doable in under two minutes.
4. Finish the current issue before raising a new one.
5. Restate progress each turn ("step 3 of 5 done").
6. Give time estimates in concrete units, never "a bit".
7. After a change, show what now works.
8. Errors: state location, cause, and fix. No drama.
9. Cap lists at 5 items.
10. No preamble, no recaps, no closers.

Exceptions: explain fully when asked to explain. Confirm before destructive actions. After three failed fixes, stop and name the doubtful assumption. If the request is ambiguous, ask one short question.
```

</details>

<details>
<summary><strong>Claude Code</strong></summary>

### Install

```bash
claude plugin marketplace add quaz579/get-to-the-fucking-point-claude
claude plugin install get-to-the-fucking-point-claude@get-to-the-fucking-point-claude
```

Type `/get-to-the-fucking-point-claude`.

### Verify

```bash
claude plugin list
```

### Update

```bash
claude plugin marketplace update get-to-the-fucking-point-claude
```

### Uninstall

```bash
claude plugin uninstall get-to-the-fucking-point-claude
claude plugin marketplace remove get-to-the-fucking-point-claude
```

Or keep it installed and turn it off: `claude plugin disable get-to-the-fucking-point-claude`.

### Always-on (optional)

A `SessionStart` hook loads the full ruleset at the start of every session, no `/get-to-the-fucking-point-claude` needed:

```bash
touch ~/.claude/.get-to-the-fucking-point-claude-always
```

Back to on-demand:

```bash
rm ~/.claude/.get-to-the-fucking-point-claude-always
```

The hook only fires when the flag file exists, so installing the plugin changes nothing by itself. Honors `$CLAUDE_CONFIG_DIR` if you've moved your config dir. "stop adhd mode" still turns it off for the current session.

</details>


<details>
<summary><strong>Codex</strong></summary>

### Install

```bash
codex plugin marketplace add quaz579/get-to-the-fucking-point-claude --ref main
codex plugin add get-to-the-fucking-point-claude@get-to-the-fucking-point-claude
```

Invoke the skill explicitly by typing `$get-to-the-fucking-point-claude`. Codex will not activate
it automatically.

### Verify

```bash
codex plugin list
```

### Update

```bash
codex plugin marketplace upgrade get-to-the-fucking-point-claude
codex plugin remove get-to-the-fucking-point-claude
codex plugin add get-to-the-fucking-point-claude@get-to-the-fucking-point-claude
```

### Uninstall

```bash
codex plugin remove get-to-the-fucking-point-claude
codex plugin marketplace remove get-to-the-fucking-point-claude
```

### Always-on (optional)

Add to `~/.codex/AGENTS.md`:

```markdown
## Output style

The reader has ADHD. Shape every response so it can be acted on:

1. Lead with the answer or next action: command, path, or snippet first.
2. Number multi-step work; one bounded action per step.
3. End with one next action doable in under two minutes.
4. Finish the current issue before raising a new one.
5. Restate progress each turn ("step 3 of 5 done").
6. Give time estimates in concrete units, never "a bit".
7. After a change, show what now works.
8. Errors: state location, cause, and fix. No drama.
9. Cap lists at 5 items.
10. No preamble, no recaps, no closers.

Exceptions: explain fully when asked to explain. Confirm before destructive actions. After three failed fixes, stop and name the doubtful assumption. If the request is ambiguous, ask one short question.
```

</details>

<details>
<summary><strong>Gemini CLI</strong></summary>

Gemini CLI has no plugin marketplace, so there are two native routes: a **custom command** (opt-in, off until you invoke it) or an **extension** (always-on once installed). The command route matches this skill's default posture; pick it unless you want the rules on every session.

### Install (command, opt-in)

```bash
mkdir -p ~/.gemini/commands
curl -fsSL https://raw.githubusercontent.com/quaz579/get-to-the-fucking-point-claude/main/skills/get-to-the-fucking-point-claude/agents/gemini.toml \
  -o ~/.gemini/commands/get-to-the-fucking-point-claude.toml
```

Start a new session, type `/get-to-the-fucking-point-claude`. It stays on for that session.

### Install (extension, always-on)

```bash
gemini extensions install https://github.com/quaz579/get-to-the-fucking-point-claude
```

The extension loads `GEMINI.md`, which imports the full skill, so the rules apply from message one. `git` must be installed.

### Verify

```bash
gemini extensions list          # extension route
ls ~/.gemini/commands           # command route: get-to-the-fucking-point-claude.toml present
```

Or type `/` in a session and confirm `get-to-the-fucking-point-claude` is listed.

### Update

```bash
gemini extensions update get-to-the-fucking-point-claude    # extension route
# command route: re-run the curl above
```

### Uninstall

```bash
gemini extensions uninstall get-to-the-fucking-point-claude    # extension route
rm ~/.gemini/commands/get-to-the-fucking-point-claude.toml     # command route
```

</details>

<details>
<summary><strong>GitHub Copilot (VS Code and Copilot CLI)</strong></summary>

Copilot reads Agent Skills natively: the same `SKILL.md`, no conversion. It scans `.github/skills/`, `.claude/skills/`, and `.agents/skills/` in the project, and `~/.copilot/skills/`, `~/.claude/skills/`, and `~/.agents/skills/` globally.

### Install

```bash
npx skills add quaz579/get-to-the-fucking-point-claude -a github-copilot        # this project
npx skills add quaz579/get-to-the-fucking-point-claude -a github-copilot -g     # all projects
```

Without the CLI, copy the skill folder into any directory Copilot scans:

```bash
git clone https://github.com/quaz579/get-to-the-fucking-point-claude
mkdir -p ~/.copilot/skills
cp -R get-to-the-fucking-point-claude/skills/get-to-the-fucking-point-claude ~/.copilot/skills/
```

### Verify

Type `/` in the chat input and confirm `get-to-the-fucking-point-claude` appears. Or:

```bash
npx skills list
npx skills ls -g    # if installed globally
```

### Update

```bash
npx skills update get-to-the-fucking-point-claude
```

Or re-copy the folder after `git pull`.

### Uninstall

```bash
npx skills remove get-to-the-fucking-point-claude
```

Or delete the `get-to-the-fucking-point-claude` folder from the skills directory it landed in.

### Activation note

Copilot respects `disable-model-invocation`: nothing applies until you invoke the skill, same as Claude Code (tested in [#60](https://github.com/quaz579/get-to-the-fucking-point-claude/pull/60)).

### Always-on (optional)

Add the block below to `.github/copilot-instructions.md` in the project (Copilot reads it into every chat):

```markdown
## Output style

The reader has ADHD. Shape every response so it can be acted on:

1. Lead with the answer or next action: command, path, or snippet first.
2. Number multi-step work; one bounded action per step.
3. End with one next action doable in under two minutes.
4. Finish the current issue before raising a new one.
5. Restate progress each turn ("step 3 of 5 done").
6. Give time estimates in concrete units, never "a bit".
7. After a change, show what now works.
8. Errors: state location, cause, and fix. No drama.
9. Cap lists at 5 items.
10. No preamble, no recaps, no closers.

Exceptions: explain fully when asked to explain. Confirm before destructive actions. After three failed fixes, stop and name the doubtful assumption. If the request is ambiguous, ask one short question.
```

</details>


<details>
<summary><strong>Hermes</strong></summary>

### Install

```bash
hermes skills install quaz579/get-to-the-fucking-point-claude/skills/get-to-the-fucking-point-claude
```

Type `/get-to-the-fucking-point-claude`. The skill installs into `~/.hermes/skills/` and is exposed as a slash command at the next session start.

Prefer to browse first? Add this repo as a skill source (a "tap"), then search and install:

```bash
hermes skills tap add quaz579/get-to-the-fucking-point-claude
hermes skills search adhd
hermes skills install quaz579/get-to-the-fucking-point-claude/skills/get-to-the-fucking-point-claude
```

### Verify

```bash
hermes skills list
```

### Update

```bash
hermes skills update get-to-the-fucking-point-claude
```

### Uninstall

```bash
hermes skills uninstall get-to-the-fucking-point-claude
```

Or remove the tap too: `hermes skills tap remove quaz579/get-to-the-fucking-point-claude`.

### Always-on (optional)

Add to the `AGENTS.md` in your working directory (Hermes loads it per workdir), or to your persona `SOUL.md` for every session:

```markdown
## Output style

The reader has ADHD. Shape every response so it can be acted on:

1. Lead with the answer or next action: command, path, or snippet first.
2. Number multi-step work; one bounded action per step.
3. End with one next action doable in under two minutes.
4. Finish the current issue before raising a new one.
5. Restate progress each turn ("step 3 of 5 done").
6. Give time estimates in concrete units, never "a bit".
7. After a change, show what now works.
8. Errors: state location, cause, and fix. No drama.
9. Cap lists at 5 items.
10. No preamble, no recaps, no closers.

Exceptions: explain fully when asked to explain. Confirm before destructive actions. After three failed fixes, stop and name the doubtful assumption. If the request is ambiguous, ask one short question.
```

</details>

<details>
<summary><strong>Kimi Code CLI</strong></summary>

### Install

Start a Kimi Code session, then:

1. Run `/plugins`.
2. Choose **Custom**.
3. Paste `https://github.com/quaz579/get-to-the-fucking-point-claude` and press `Enter`.
4. Choose **Trust and install**.

Use slash command `/skill:get-to-the-fucking-point-claude` to invoke the skill explicitly.

### Update

`/plugins` in Kimi Code session, cursor to **I Have ADHD**, press `R`.

### Uninstall

`/plugins` in Kimi Code session, cursor to **I Have ADHD**, press `D`.


</details>

<details>
<summary><strong>OpenCode</strong></summary>

OpenCode loads this repository as a server plugin: `.opencode/plugins/get-to-the-fucking-point-claude.mjs` registers the `skills/` entry point and the `/get-to-the-fucking-point-claude` command, and injects the ruleset when always-on is enabled. OpenCode also reads `skills/` natively, so the skill still works even without the plugin — the plugin adds the `/get-to-the-fucking-point-claude` command and the always-on flag.

### Install

Clone the repo and point OpenCode at the plugin. An absolute path shares one checkout across every project:

```bash
git clone https://github.com/quaz579/get-to-the-fucking-point-claude ~/.config/opencode/vendor/get-to-the-fucking-point-claude
```

Add to your `opencode.json` (global: `~/.config/opencode/opencode.json`):

```json
{ "plugin": ["/absolute/path/to/get-to-the-fucking-point-claude/.opencode/plugins/get-to-the-fucking-point-claude.mjs"] }
```

Or run OpenCode from the checkout — it ships a root `opencode.json` with the plugin already wired up.

Start a new session and turn on ADHD-friendly output for the session:

```text
/get-to-the-fucking-point-claude
```

Rules stay on until `stop adhd mode` or `normal mode`.

### Verify

Start OpenCode, type `/`, and confirm `get-to-the-fucking-point-claude` appears in the command list.

### Update

```bash
git -C ~/.config/opencode/vendor/get-to-the-fucking-point-claude pull
```

### Uninstall

Remove the `plugin` entry from `opencode.json`.

### Always-on (optional)

```bash
touch ~/.config/opencode/.get-to-the-fucking-point-claude-always
```

While the flag exists, the plugin appends the full ruleset to the system prompt every turn — the OpenCode equivalent of the Claude Code `SessionStart` hook. `stop adhd mode` or `normal mode` disables it for the current session; delete the flag to turn always-on off for good:

```bash
rm ~/.config/opencode/.get-to-the-fucking-point-claude-always
```

</details>


<details>
<summary><strong>Pi</strong></summary>

Pi discovers this repository as a native package: `extensions/` provides the session-persistent mode and `skills/` keeps the Agent Skills entry point available.

### Install

```bash
pi install https://github.com/quaz579/get-to-the-fucking-point-claude
```

Start a new Pi session. Toggle ADHD-friendly output for the current session:

```text
/get-to-the-fucking-point-claude
```

The footer shows `● BLUNT ON` while the mode is active. Run the command again to turn it off, or be explicit:

```text
/get-to-the-fucking-point-claude on
/get-to-the-fucking-point-claude off
stop adhd mode
```

Like the Claude Code hook, the extension adds the ruleset to the conversation once instead of rewriting the system prompt on every request, and adds it again after compaction drops it.

The existing Agent Skills command remains available as an alias:

```text
/skill:get-to-the-fucking-point-claude
```

Start a new Pi session with the mode enabled by default:

```bash
pi --adhd
```

### Verify

```bash
pi list
```

Confirm the GitHub package is listed, then type `/get-to-the-fucking-point-claude` and check that `● BLUNT ON` appears in the footer.

### Update

```bash
pi update https://github.com/quaz579/get-to-the-fucking-point-claude
```

Or update every unpinned Pi package with `pi update --extensions`.

### Uninstall

```bash
pi remove https://github.com/quaz579/get-to-the-fucking-point-claude
```

### Always-on (optional)

Create a flag in Pi's agent configuration directory:

```bash
touch ~/.pi/agent/.get-to-the-fucking-point-claude-always
```

The extension checks the flag at every new, resumed, forked, or reloaded session. A saved choice for the current session wins over this default, so `stop adhd mode` keeps that session disabled.

Back to on-demand:

```bash
rm ~/.pi/agent/.get-to-the-fucking-point-claude-always
```

If `PI_CODING_AGENT_DIR` is set, put `.get-to-the-fucking-point-claude-always` in that directory instead. Run `/reload` or start a new session after changing the flag.

</details>


<details>
<summary><strong>Oh My Pi (OMP)</strong></summary>

### Install

```bash
omp plugin marketplace add quaz579/get-to-the-fucking-point-claude
omp plugin install --scope user get-to-the-fucking-point-claude@get-to-the-fucking-point-claude
```

Start a new OMP session and run `/get-to-the-fucking-point-claude` to toggle the mode.

### Update

```bash
omp plugin marketplace update get-to-the-fucking-point-claude
omp plugin upgrade --scope user get-to-the-fucking-point-claude@get-to-the-fucking-point-claude
```

### Uninstall

```bash
omp plugin uninstall --scope user get-to-the-fucking-point-claude@get-to-the-fucking-point-claude
omp plugin marketplace remove get-to-the-fucking-point-claude
```

</details>


<details>
<summary><strong>Qwen Code</strong></summary>

### Install

```bash
qwen extensions install quaz579/get-to-the-fucking-point-claude
```

Qwen Code supports the GitHub shorthand and installs the repository as a
native extension. The extension discovers the skill under `skills/`.

Type `/get-to-the-fucking-point-claude` to invoke the skill explicitly. Installing the extension
does not change output until the skill is invoked.

### Verify

```bash
qwen extensions list
```

Then start a new Qwen Code session and run:

```text
/skills
```

Confirm that `get-to-the-fucking-point-claude` appears in the list.

### Update

```bash
qwen extensions update get-to-the-fucking-point-claude
```

### Uninstall

```bash
qwen extensions uninstall get-to-the-fucking-point-claude
```

</details>

<details>
<summary><strong>Zed</strong></summary>

Zed's Agent reads Agent Skills natively: the same `SKILL.md`, no conversion. (Zed's older "Rules" were replaced by Skills plus `AGENTS.md` instructions.)

### Install

In the Agent Panel, open the Skills manager and choose **Create skill from URL** (also in the command palette as `agent: create skill from url`), then paste:

```
https://github.com/quaz579/get-to-the-fucking-point-claude/blob/main/skills/get-to-the-fucking-point-claude/SKILL.md
```

Save it in **User** scope for every project, or **Project** scope for one. Then type `/get-to-the-fucking-point-claude` in the Agent Panel.

Prefer the filesystem? Clone the repo and drop the skill folder into your user skills directory:

```bash
git clone https://github.com/quaz579/get-to-the-fucking-point-claude
cp -R get-to-the-fucking-point-claude/skills/get-to-the-fucking-point-claude ~/.config/zed/skills/
```

### Verify

Open the Skills manager in the Agent Panel and confirm `get-to-the-fucking-point-claude` is listed. Or type `/` and confirm it appears.

### Update

Re-import from the same URL (overwrites), or re-copy the folder after `git pull`.

### Uninstall

Remove `get-to-the-fucking-point-claude` from the Skills manager, or delete `~/.config/zed/skills/get-to-the-fucking-point-claude`.

### Always-on (optional)

Add to your personal `~/.config/zed/AGENTS.md`:

```markdown
## Output style

The reader has ADHD. Shape every response so it can be acted on:

1. Lead with the answer or next action: command, path, or snippet first.
2. Number multi-step work; one bounded action per step.
3. End with one next action doable in under two minutes.
4. Finish the current issue before raising a new one.
5. Restate progress each turn ("step 3 of 5 done").
6. Give time estimates in concrete units, never "a bit".
7. After a change, show what now works.
8. Errors: state location, cause, and fix. No drama.
9. Cap lists at 5 items.
10. No preamble, no recaps, no closers.

Exceptions: explain fully when asked to explain. Confirm before destructive actions. After three failed fixes, stop and name the doubtful assumption. If the request is ambiguous, ask one short question.
```

</details>

<details>
<summary><strong>Cursor, Amp, and any other agent-skills harness</strong></summary>

Works with any harness that reads agent skills. Swap `-a <agent>` for yours.

### Install

```bash
npx skills add quaz579/get-to-the-fucking-point-claude                  # this workspace
npx skills add quaz579/get-to-the-fucking-point-claude -g               # all projects
npx skills add quaz579/get-to-the-fucking-point-claude -a cursor -y     # one agent only
npx skills add quaz579/get-to-the-fucking-point-claude -a opencode -y
```

New agent chat, type `/get-to-the-fucking-point-claude`.

Without the CLI, copy the skill folder into whatever path your agent scans:

```bash
git clone https://github.com/quaz579/get-to-the-fucking-point-claude
mkdir -p ~/.cursor/skills     # Cursor. Use .agents/skills for OpenCode, or your agent's own path
cp -R get-to-the-fucking-point-claude/skills/get-to-the-fucking-point-claude ~/.cursor/skills/
```

### Verify

```bash
npx skills list
npx skills ls -g    # if installed globally
```

### Update

```bash
npx skills update get-to-the-fucking-point-claude
npx skills update -g    # if installed globally
```

### Uninstall

```bash
npx skills remove get-to-the-fucking-point-claude
npx skills remove get-to-the-fucking-point-claude -g    # if installed globally
```

### Always-on (optional)

Paste this into your agent's persistent rules file. Cursor: **Settings → Rules → User Rules**, or a project rule under `.cursor/rules/` with `alwaysApply: true`. OpenCode: `~/.config/opencode/AGENTS.md`.

```markdown
## Output style

The reader has ADHD. Shape every response so it can be acted on:

1. Lead with the answer or next action: command, path, or snippet first.
2. Number multi-step work; one bounded action per step.
3. End with one next action doable in under two minutes.
4. Finish the current issue before raising a new one.
5. Restate progress each turn ("step 3 of 5 done").
6. Give time estimates in concrete units, never "a bit".
7. After a change, show what now works.
8. Errors: state location, cause, and fix. No drama.
9. Cap lists at 5 items.
10. No preamble, no recaps, no closers.

Exceptions: explain fully when asked to explain. Confirm before destructive actions. After three failed fixes, stop and name the doubtful assumption. If the request is ambiguous, ask one short question.
```
</details>


## How activation works

1. **Installed, not invoked.** In Claude Code, Qwen Code, and Codex, nothing happens until you invoke the skill explicitly. Claude Code and Qwen Code honor `disable-model-invocation: true` in `SKILL.md`; Codex honors `policy.allow_implicit_invocation: false` in `agents/openai.yaml`. Other harnesses may load every skill's description at startup and activate the skill themselves.
2. **You invoke it explicitly.** Type `/get-to-the-fucking-point-claude` in Claude Code or Qwen Code, or `$get-to-the-fucking-point-claude` in Codex. Rules stay on for that session. "stop adhd mode" or "normal mode" turns them off.
3. **You touch `~/.claude/.get-to-the-fucking-point-claude-always`** (Claude Code). A `SessionStart` hook loads the full ruleset from message one, every session.
4. **You add the always-on snippet above** (other harnesses). Keeps the core rules in your agent's persistent context.

In Claude Code, Qwen Code, and Codex, no middle ground: if you did not turn it on, it is off.

## Troubleshooting

**`/get-to-the-fucking-point-claude` not in autocomplete.** Restart the agent. The plugin index is read at startup.

**Always-on flag has no effect.** Update the plugin (`claude plugin marketplace update get-to-the-fucking-point-claude`) and restart. Hooks are read at startup, and the flag needs the plugin version that ships `hooks/hooks.json`.

**`claude plugin marketplace add` fails.** Use the `owner/repo` form. A local path must point at the repo root, not `.claude-plugin/`.

**Installed but replies still preamble.** Open a new session. If it still drifts, tighten the wording in `skills/get-to-the-fucking-point-claude/SKILL.md`.

**Want different rules.** Fork, edit `skills/get-to-the-fucking-point-claude/SKILL.md`, then swap your copy in:

```bash
claude plugin uninstall get-to-the-fucking-point-claude            # drop the upstream copy first:
claude plugin marketplace remove get-to-the-fucking-point-claude   # fork and upstream share both names
claude plugin marketplace add <your-username>/get-to-the-fucking-point-claude
claude plugin install get-to-the-fucking-point-claude@get-to-the-fucking-point-claude
```

Restart, then re-invoke `/get-to-the-fucking-point-claude`.

**Skill missing after `npx skills add`.** Start a new agent chat. Skills are indexed at session start. Confirm the folder landed where your agent scans (`~/.cursor/skills/` for Cursor, `.agents/skills/` for OpenCode) and that the frontmatter `name` matches the folder name.
