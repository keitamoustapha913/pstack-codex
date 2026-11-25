---
name: setup-pstack
description: Register and validate PStack’s three fixed Codex model profiles and Sol Medium orchestrator. Use for $setup-pstack or checking PStack model availability and configuration.
---

**Codex host:** Read `../poteto-mode/references/codex-compatibility.md` relative to this SKILL.md before executing. Its host mappings govern all downstream instructions and resources; retain the original workflow.

# Setup pstack

Read the host adapter and `codex-models.toml` in the installed `poteto-mode/references/` directory. This configuration is a fixed user-approved allowlist, not a menu of interchangeable models or reasoning budgets.

## Steps
### 1. Discover available models
Check the actual Codex client, model selector and subagent capabilities. Confirm `gpt-6-luna` at `high`, `gpt-6.1-terra` at `medium`, and `gpt-6.2-sol` at `medium`. Do not claim availability based on documentation alone. Use a current Codex client that supports all three profiles; model access is account-dependent. Check whether the live delegation schema supports named roles, exact model/effort overrides, both, or neither.

### 2. Register the three shipped custom agents

Resolve the plugin root from this skill's actual installed absolute path (`../..` from the directory containing this SKILL.md). The three source TOMLs are in `<plugin-root>/agents/`. Read them and the fixed policy before copying. Ask whether the operator wants personal registration (`$CODEX_HOME/agents` when CODEX_HOME is set, otherwise `~/.codex/agents`) or project registration (`<trusted-project>/.codex/agents`). Ask permission for the writes if not already given. Create only missing files, using the shipped bytes. An identical file needs no change. A differing file, symlink or shadowing role is a conflict: show the diff and obtain approval before replacing; never overwrite blindly. Do not edit unrelated config, install hooks or widen permissions. If the plugin files cannot be found, stop and report the missing path. Start a fresh Codex session if required for discovery. Confirm all three roles are active when the live schema supports named-role selection. If it does not, record that limitation separately from successful file registration; validate the exact-pair path described in the host adapter instead.

### 2a. Load current state
Read `codex-models.toml` and compare its profiles and orchestrator setting against `codex-models.defaults.toml`. The orchestrator setting must be `sol`. Verify the three installed custom agents `poteto-luna`, `poteto-terra`, and `poteto-sol` pin their exact model and effort. Check the current parent session's model and effort: GPT-6.2 Sol (`gpt-6.2-sol`) at `medium` is mandatory. If unknown, obtain operator confirmation; if different, request a switch to Sol/medium. Stop before running Poteto Mode or spawning workers if Sol/medium is unavailable or remains unconfirmed. Do not substitute Terra or Luna for the parent.

### 3. Select by complexity
Keep the fixed profiles. Luna handles clear bounded work, Terra handles ordinary delegated engineering, Sol owns orchestration and handles genuinely difficult or uncertain delegated work. Role mappings are starting preferences, not mandatory escalation based on category. The original budget labels, where encountered, mean scope and complexity only; they never change the fixed effort of a profile. Preserve original panel counts and verification requirements.

### 4. Validate
Check every role entry and panel seat against the three exact profiles, including its custom agent name. Flag any mismatch. Confirm availability and the active role definitions as far as the runtime allows. Distinguish registered files, named-role discovery/selection, explicit-pair selection, and actual child runtime model/effort. Report untested checks separately. If a delegate profile is unavailable, use only a confirmed approved alternative when adequate for the task and compatible with panel independence. Otherwise stop the affected work and report the blocker. Never use an unapproved model, effort or implicit inheritance.

### 5. Configuration
Do not offer new models or effort levels. Keep the shipped three-profile policy intact; if the local PStack configuration has drifted, show the diff and ask before restoring the approved baseline. Do not edit the user's global Codex config or permissions. Do not silently rewrite the pinned agent definitions.

### 6. Confirm
Report the three approved pairs, the parent session pair (or unverified status), installed custom agent paths, availability, supported delegation mode (named role, exact pair, or blocked), and unresolved constraints. Do not mark unsupported profiles or unperformed checks as verified.


### 7. Offer a verification skill (optional)

Check whether the project has a way to drive the real app for proof (a `verify-*` skill, or an existing harness). If not, offer once: "want a project-local verification skill, so agents can drive the app the way a user does and prove changes work? I can generate one with $create-verification-skill." On yes, invoke `$create-verification-skill` (resolves wherever pstack is installed: workspace, user, or plugin). On no, move on without pushing.

### 8. Offer a formal verification skill (optional)

Check whether the project already has a formal verification skill (a project skill that runs a model checker, a proof, or another verifier against the code). If not, offer once: "want a formal verification skill, so agents can prove a key property of your code holds in every case in scope, not only the cases tests reach? I can generate one with /create-formal-verification-skill." On yes, invoke `$create-formal-verification-skill` (resolves wherever pstack is installed: workspace, user, or plugin). On no, move on without pushing.
