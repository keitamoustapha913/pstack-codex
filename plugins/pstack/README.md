# PStack for Codex

Unofficial, source-based Codex port of [Poteto PStack](https://github.com/cursor/plugins/tree/main/pstack) by Lauren Tan. Upstream 0.15.48; port 0.15.48-codex.3. MIT licensed. This repository contains the actual converted skill files, not a converter, generator or dependency on the upstream repository at installation time.

**Source:** uploaded GitHub archive of `cursor/plugins`, revision recorded in `../../audit/manifest.json` as `41e400932eca14f289e7db717a70455256b6d388`. The archive's ZIP comment supplies that revision; its authenticity was not independently verified against GitHub.

## Install

### Local ZIP (no GitHub publishing required)

1. Extract the entire ZIP into a permanent directory, keeping hidden folders. The root is `pstack-codex/`.
2. In a terminal at the extracted repository root, register the marketplace:

   ```sh
   codex plugin marketplace add .
   ```

3. Restart or refresh the ChatGPT desktop app / Codex Plugins Directory as appropriate. Select the **PStack for Codex** marketplace, install the **PStack for Codex** (`pstack`) plugin, and start a new Codex session. The marketplace command registers a source; it does not itself guarantee that the plugin is installed.

### GitHub

Create a GitHub repository named `pstack-codex`, commit this repository's contents (including `.agents/plugins/marketplace.json` and `plugins/pstack/.codex-plugin/plugin.json`), and push. Then register it from any supported Codex client:

```sh
codex plugin marketplace add YOUR_GITHUB_USERNAME/pstack-codex
```

Use the Plugins Directory to install the plugin. Private repositories require appropriate Git access. Pin a ref with `--ref` when desired. To refresh the marketplace after publishing a release, use `codex plugin marketplace upgrade pstack-codex` and the client's plugin update/reload mechanism.

### One-time setup (required)

Start a Sol Medium Codex session, select the installed `setup-pstack` skill with the `$` skill picker, and approve registration of the three shipped custom agent TOMLs. These definitions are bundled at `plugins/pstack/agents/` but are not automatically registered merely because they are in a plugin. Setup copies only the three approved files to `$CODEX_HOME/agents/` (normally `~/.codex/agents/`) or `<project>/.codex/agents/` with your permission. It validates the exact models, efforts and active role definitions, and preserves the original optional verification-skill setup. Restart Codex if agent discovery requires it. A conflicting existing file or unavailable role is a blocker, not a silent overwrite or model substitution.

If you prefer manual registration, copy the three TOMLs into the chosen agents directory only after checking for conflicts, then run `$setup-pstack` to validate. Nothing else needs to be installed to discover these skills. Individual verification workflows may require project-specific runtimes, credentials, browsers, `gh`, `git`, Bun, or other tools.

## Use

Launch Codex with the mandatory parent profile (or select it in the client):

```sh
codex -m gpt-6.2-sol -c 'model_reasoning_effort="medium"'
```

Invoke the installed skill with the `$` picker (use the qualified name if shown):

```text
$poteto-mode Implement the feature, preserve the existing contracts, and prove it works against the real application.
```

Select `$poteto-help` for help. The entry point reads the upstream playbook, selects its actual downstream skill files, and delegates by work-slice complexity. A skill cannot change the parent model or enforce a platform-wide model firewall: Poteto Mode stops if Sol Medium cannot be confirmed. No automatic Cursor Custom Mode persistence is assumed.

## Fixed model policy

| Profile | Model ID | Effort | Role |
|---|---|---|---|
| poteto-sol | gpt-6.2-sol | medium | Mandatory parent orchestrator; selective complex delegates |
| poteto-terra | gpt-6.1-terra | medium | Default worker for ordinary engineering, feature implementation and focused integration |
| poteto-luna | gpt-6-luna | high | Simple features, bounded work, exploration, tests and parallel checks |

No other models or reasoning levels. Choose the least intensive adequate approved worker for each slice. Escalate when evidence warrants it; de-escalate when the complex part is resolved. Keep all original review and proof requirements. Cross-vendor panels become independent OpenAI-only panels, with the reduction in diversity disclosed.

## Contents

- `plugins/pstack/skills/`: 59 original PStack skills and 3 bundled MIT-licensed team-kit dependencies (`deslop`, `control-cli`, `control-ui`). Includes all 22 playbooks, 24 principle skills, source resources and scripts. The two original agent role briefs are adapted as references, preserving Comment Sicko's behavior without adding a fourth model.
- `plugins/pstack/agents/`: three pinned Codex agent definitions.
- `plugins/pstack/plugin.json` and `.codex-plugin/plugin.json`: portable manifest and compatibility fallback.
- `.agents/plugins/marketplace.json`: native marketplace catalog.
- `plugins/pstack/docs/`, `UPSTREAM-README.md`: preserved upstream guide material, not authoritative for Codex-specific commands. The current README and adapter govern host compatibility.
- `../../upstream-reference/`: original Cursor plugin manifests, agent role definitions and optional Benny automation materials. These are preserved for reference only, not installed as active skills or automations.
- `../../audit/`: exact original-to-port diff, source-file hashes, residual host-reference report, validation summary. No upstream checkout needed to install.

## Compatibility boundaries

Cursor's `Task`, Project worker, custom mode, model slugs, and `/loop` are not assumed to exist. The host adapter maps their intent to available native Codex mechanisms. Worktrees must be explicitly allocated; remote/unattended execution requires real host support. Access to session history, review bots, connected tools, and the app under test is runtime-dependent. Missing evidence is not a pass. The optional `make-bot-ui` skill preserves the upstream webhook workflow as a reference, but is blocked unless an authorized OpenAI-compatible webhook mechanism is available; the separate Benny automations are not installed. No Grok, Claude, Gemini, Astra or other unapproved model may be used.

The upstream worktree audit script was minimally changed so it never scans Cursor transcripts by default; an explicitly authorized workspace-scoped transcript export is required to classify chat recency, otherwise it reports unknown and flags candidates for review. The rest of the original non-Markdown skill resources are byte-identical. The port respects host approvals and sandbox restrictions and does not widen permissions.

**Validation status:** actual uploaded source converted and packaged; static file completeness, metadata, model policy, audit hashes, and shell syntax checked. Live installation, model entitlement, actual subagent execution, and end-to-end workflows have not been tested in a running Codex client in this environment. Review `../../audit/VALIDATION.md` and run `$setup-pstack` before use.

Docs: [OpenAI plugin packaging](https://developers.openai.com/plugins/build/plugins), [Codex skill authoring](https://learn.chatgpt.com/docs/build-skills), [Codex custom agents](https://learn.chatgpt.com/docs/agent-configuration/subagents).
