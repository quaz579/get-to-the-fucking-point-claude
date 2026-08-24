<p align="center">
  <img src="./logo.png" alt="get-to-the-fucking-point-claude" width="140" />
</p>
<p align="center">
  <strong align="center">Make your coding assistant get to the fucking point. No preamble, no ass-kissing, no "Great question!"</strong>
</p>
<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/github/license/quaz579/get-to-the-fucking-point-claude?style=flat" alt="License"></a>
</p>

## Install

Copy/paste into your CLI prompt:

```text
Install the get-to-the-fucking-point-claude skill/plugin from https://github.com/quaz579/get-to-the-fucking-point-claude, refer to the repo's AGENTS.md for instructions.
```

Or 🔗 [check the installation instructions](INSTALL.md).

## What it does

A skill for your coding assistant that stops it from burying the answer under a pile of throat-clearing. Action first. Steps numbered. Blunt honesty instead of flattery. Zero "Hope this helps!"

## What changes

<table>
<tr>
<td width="50%">

## Before

> Great question! Let me think about this. Your auth flow has a few moving pieces: the middleware, the token verification, and the cookie handling. Looking at `src/auth.ts`, the `verifyToken` function (around lines 42-58) seems to be using an older `jsonwebtoken` API. One approach would be to update the package and rewrite that function. After making the change, you'd want to run the auth tests to confirm nothing breaks. By the way, you might also want to look at your dependency versions overall. Hope this helps! Let me know if you want to dig deeper.

</td>

<td width="50%">

## After

> Run `npm install jsonwebtoken@latest`, then edit `src/auth.ts:42`.
>
> 1. Open `src/auth.ts`
> 2. Replace `verifyToken` (lines 42–58) with the snippet below
> 3. Run `npm test -- auth.spec.ts`
>
> Next: paste the first failing line if any test fails.

</td>
</tr>
</table>

## The rules

10 rules. Full text in [SKILL.md](./skills/get-to-the-fucking-point-claude/SKILL.md).

1. Lead with the fucking answer.
2. Number multi-step tasks.
3. End with one concrete next action.
4. Kill tangents on sight.
5. Restate state every turn.
6. Real time estimates (minutes, not "a bit").
7. Show the win, don't bury it.
8. Be bluntly honest — errors and everything else.
9. Cap lists at 5 items.
10. No preamble. No recap. No ass-kissing.

## Turn it off

It stays on until you tell it to stop. Say **"normal mode"** (or "chill out") and it goes back to being polite and long-winded like everyone else.

## Tune it

Fork, edit `skills/get-to-the-fucking-point-claude/SKILL.md`, then swap your copy in:

```bash
claude plugin uninstall get-to-the-fucking-point-claude            # drop the upstream copy first:
claude plugin marketplace remove get-to-the-fucking-point-claude   # fork and upstream share both names
claude plugin marketplace add <your-username>/get-to-the-fucking-point-claude
claude plugin install get-to-the-fucking-point-claude@get-to-the-fucking-point-claude
```

Restart Claude Code, then re-invoke `/get-to-the-fucking-point-claude`.

## Credits

Shamelessly forked from [ayghri/i-have-adhd](https://github.com/ayghri/i-have-adhd), which is the same idea with better manners. Go star the original — it did the hard part.

## License

MIT.

Star ⭐ if it saved you one scroll past one "Great question!"
