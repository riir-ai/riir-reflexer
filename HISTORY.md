# HISTORY.md — riir-reflexer (public)

Compacted 2026-11-20: every heading kept verbatim, bodies <=2 lines of durable facts; full pre-compaction text in git history (pre-compaction HEAD 549f3a9).

## 2026-10-05 — issue 001 closed: the E18 first-mint runbook moves to Plan 005 (delegated verdict)

E18 (`DEFAULT_PINS` empty until first public vessel mint) closed TRIGGER-ONLY: verified runbook in `.plans/005_default_pins_first_mint.md` (payload is `--in`; `--vessel-print` early-returns, no combine with `--vessel`). Minting is deterministic; `.plans/003` E18 rows superseded.

## 2026-10-04 — vessel-mint genesis: the keygen tool, the stub worker, and the public key record (`e81d66d` + `d29de0b` + `4b40003`)

`vmint-keygen` (`e81d66d`, `d29de0b`), placeholder `cloudflare/vessel-mint` (all routes 503, secrets persist across deploys; wrangler `secret put` takes `--name`), `GENESIS.md` public keys (ROOT offline + MINT online key_id 1). Seeds only in `~/cold` + CF secret, never committed; lost mint seed = ROOT re-delegation. Relation-flow WALK joined `.docs/06_resources` (`2433a80`).

## 2026-10-04 — `.docs/06_resources`: the relation section + the first mirrored figure (`ba943d8`)

Plan 004: `.docs/06_resources/resources.md` is the owning doc for the Reflex-Reflexer relation (placed after `#rethink`) with the `reflexer_relation_flow` gfflow block; repo joined renderer SOURCES + sync_mirror roots. Landed with riir-ai Plan 620 P1.

## 2026-09-30 — sigmoid delegated to the substrate, adjudicated pick-level (`fb6ac8f`; issue 002 closed)

Local sigmoid deleted; `use katgpt_core::exact_sigmoid_f64 as sigmoid` (G1 pin is PICK-level; bit-identical x>=0, 8-ulp on negatives). Permanent arm `sigmoid_delegation_matches_frozen_legacy_body` reds if the substrate kernel drifts, forcing re-adjudication.

## 2026-09-27 — the class-aware payload cap (`049a583`): HOSTED-ONLY may carry 16 MiB; the public reader's 1 MiB untrusted bound is UNCHANGED

Cap is per-class: HOSTED-ONLY up to `MAX_HOSTED_PAYLOAD` 16 MiB, PUBLIC-RELEASE stays `MAX_PAYLOAD` 1 MiB (public reader = untrusted input). `peek()` reads class from the signed header; `open()` refuses a hosted-declaring file before any payload byte (`HostedOnlyPath`); reflexer-wasm never loosens. Format v1 unchanged; no class-1 encoder. Consumer cap-pin gate: riir-instinct `f2fd12a`.

## 2026-09-25 — pre-birth

Design closed; public engine (riir-shader posture). Docs landed md-only; P0 filed as katgpt-rs Issue 893. Improvement/hosted/deploy concerns live in private siblings.

## 2026-09-25 — PUBLIC BIRTH (P1)

MIT; BOUNDARY.md `Visibility: public` + `## Owns`; boundary guard check C3b (public-leaf law: a public repo may path-dep only katgpt-rs). Remote gist-rs/riir-reflexer.

## 2026-09-25 — P0 LANDED (the substrate crate exists)

katgpt-rs Issue 893 resolved (`243c38a1b`): `katgpt-tetris` leaf crate, Bench-891/892 bit-identity PASS, G2 0.32-0.33 ms/decision, champion genome `68cae9d382014662` pinned as frozen REFERENCE.

## 2026-09-25 — P2 LANDED (engine bin + measurement lane + submission client)

- Engine bin serves ONE frozen champion genome (`68cae9d382014662`, asserted at load); unknown questions ABSTAIN structurally (never a threshold in replay); sigmoid margins, never softmax. `options_count` is the fail-closed bit-identity defense.
- G1 `tests/g1_champion_replay.rs` byte-identical to oracle; measurement lane refuses on battery/over MAX_LOAD; G2 budget: no-hold p50 <= 500 us, hold p50 <= 1000 us, p99 <= 3000 us.
- Opt-in `--record` signed Ed25519 trajectory manifest; no billing code, ever.

## 2026-09-25 — P3 LANDED (the vessel format crate)

`crates/reflexer-vessel` format v1 (68-byte header + 64-byte ed25519-STRICT sig + payload; `commitment = blake3(header||payload)`; payload-agnostic). `encode_public` is the only public writer; reader refuses HOSTED-ONLY only after authenticity. Monotonic apply (`OlderThanCurrent`/`VersionFork`; `--vessel-force-downgrade` logs). Hardening `50409ec`; cargo-fuzz deferred to first public artifact. Vessel failures are LOUD boot failures. Gates: Bench 002, 47/47 on aarch64 + x86_64.

## 2026-10-06 — Issue 004 CLOSED: artifact class vocabulary + manifest schema v0 + runtime per-env pin refusal (riir-ai Plan 623 T2)

Artifact class vocabulary + manifest schema v0 DRAFT + runtime per-env pin refusal (`3757649`, `e251274`, `76853af`, `593a30f`; riir-ai Plan 623 T2). Fixture/mock only; v0->v1 bump awaits A10 ratification; T7 `artifact-sync lint` must agree with the fixture validator.

## 2026-10-05 — Issue 003 CLOSED: compiled-in authority pins, dev_pins-gated wildcard, persisted apply floor (riir-rethink Plan 009 P1)

Closed at `0c7d7fb`: `DEFAULT_PIN_KEYS` carries authority ROOT key-id 1 (const assert forbids empty); `--vessel-pubkey` refused (exit 2) unless built with `dev_pins` (default off); persisted apply floor in `src/vessel_apply.rs` (atomic 0600, corrupt state LOUD never genesis; `--vessel-state` overrides). Wildcard tests live in `tests/vessel_dev_gates.rs` (key-id 7). Mint-side key split: riir-train Issue 612.
- 2026-10-17 Issue 005 (`Manifest.proto` zero-read) closed keep+repair `9fe57dc`: `MANIFEST_FORMAT = 1` owns the value; unsigned field, future reader rule (missing = 1, unknown fails closed); removal would break old readers.
