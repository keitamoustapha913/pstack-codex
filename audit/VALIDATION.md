# PStack validation

## Release codex.3 — operator-reported runtime evidence (2026-11-25)

The operator reported a fresh Codex CLI 0.172.0 end-to-end test. This is a record of their reported evidence, not an independently reproduced live test in this packaging environment.

| Check | Reported result | Evidence |
|---|---|---|
| Orchestrator | PASS | Parent turn_context: gpt-6.2-sol / medium |
| Skill discovery | PASS | 62 enabled, zero load errors |
| Supporting resources | FAIL | 58 skill-tree relative links resolved; installed README escaped the package and eight historical documentation links failed |
| Named-role discovery (fresh CLI) | PASS | Three shipped TOMLs byte-matched; agent_type exposed all roles |
| Named-role selection (active API session) | FAIL / host limitation | Schema had no agent_type; explicit approved model/effort pairs worked |
| Swarm | PASS | Two independent Luna/high workers completed |
| Interrogate | PASS | Three independent approved-profile reviewers completed |
| Delegation, routing and collection | PASS | Eight active-session workers and three fresh CLI workers completed with approved turn_context pairs |

Fresh CLI named-role workers confirmed Luna/high, Terra/medium and Sol/medium in actual child session records; each read-only command exited successfully. The worktree reportedly remained clean.

## Release codex.4 — static package checks

- 62 skills, 22 playbooks, 24 principles and the three unchanged model profiles.
- All 519 upstream skill files tracked by SHA-256: 438 byte-identical, 81 adapted.
- Installed validation report included within the plugin boundary; eight historical links repaired with bundled reference documents. All 319 relative Markdown links in an isolated copy of the plugin resolved inside the package.
- Named-role and exact-pair instructions use the same pinned allowlist; missing capabilities are explicitly reported.
- Both plugin manifests agree on the new version. Agent TOMLs, model policy, playbooks and principles are unchanged from codex.3.

The codex.4 static checks do not establish live installation or execution of this revised package. Reinstall/update and repeat the relevant smoke checks in a real CLI and API session. Arena, actual feature delivery, and every optional upstream workflow were not established by the reported smoke test. Cursor-only unattended automation and cross-vendor diversity remain compatibility limits.
