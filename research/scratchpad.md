# Docs layout (JTBD / ODI-shaped)

**Outcome and requirement naming (searchability)**

- Keep **outcome** folders and **requirement** files **fully described**: include a stable ID **and** a **unique descriptive slug** (kebab-case) so global search and grep rarely collide.
- Avoid bare tokens alone (`O001/`, `R001.md`) as the only name — path gives context, but **basenames should still read as the thing** when they appear in search results or editor tabs.
- Example pattern: `JE-CFJ-DEF-O001-minimize-time-to-arrange-tracks-for-listening/` and `JE-CFJ-DEF-O001-R001-remember-last-used-sort-across-sessions.md`.

**Actor split**

- **JE** — job executor: core functional job, related jobs, emotional jobs.
- **PLST** — product lifecycle support team: consumption chain jobs (software buckets below).
- **PDM** — purchase decision maker: financial / purchase outcomes.

**Core functional job (CFJ)**

- One folder per job under `CFJ-core-functional-job/`.
- Universal job map: **eight sibling step folders** `01-DEF` … `08-CLS` (conclude = **CLS**, not CNC).
- Under each step: **outcome** folders, then **requirement** files for those outcomes.
- Outcome IDs use **`JE-CFJ-`** consistently (core functional job), e.g. `JE-CFJ-DEF-O001-<descriptive-slug>/` (see **Outcome and requirement naming** above).

**Related jobs (RJ)**

- One folder per related job.
- **Complex:** same eight steps as CFJ; outcomes under steps (e.g. `JE-RJ001-DEF-O001-…`).
- **Simple:** no step folders — outcomes directly under the job folder (`JE-RJ002-O001-…`).

**Emotional jobs (EJ)**

- Default: **no** universal map — outcomes (and requirements) directly under the job folder (`JE-EJ001-O001-…`).
- **Optional:** if an emotional job is large or multi-phase enough to need process decomposition, use the **same eight steps** as CFJ/RJ (rare; same rule as RJ: complexity-driven).

**Consumption chain jobs (CCJ)** — software-aligned buckets

- Same **decomposition rule as RJ:** each bucket is one job folder; use **eight steps only when** that consumption-chain job is heavy enough to warrant step-level outcomes.
- Otherwise: **README** + outcome folders **directly under** the bucket (`PLST-CCJ-NNN-O001-…`).
- Outcome/requirement structure matches CFJ/RJ: **outcome folder → requirement file(s)**.
- Bucket order is lifecycle-ish for software (tune names to your product): obtain → install → configure → learn-to-use → operate → integrate → maintain → monitor → secure → support → upgrade → cancel.

---

```text
docs/
	product/
		README.md
		JE-job-executor/
			README.md
			CFJ-core-functional-job/
				JE-CFJ-some-job/
					README.md
					01-DEF-define/
						README.md
						JE-CFJ-DEF-O001-minimize-time-to-arrange-tracks-for-listening/
							README.md
							JE-CFJ-DEF-O001-R001-remember-last-used-sort-across-sessions.md
					02-LOC-locate/
					03-PRP-prepare/
					04-CNF-confirm/
					05-EXE-execute/
					06-MON-monitor/
					07-MOD-modify/
					08-CLS-conclude/
			RJ-related-jobs/
				JE-RJ001-some-complex-related-job/
					README.md
					01-DEF-define/
						README.md
						JE-RJ001-DEF-O001-minimize-steps-to-merge-calendars/
							README.md
							JE-RJ001-DEF-O001-R001-two-way-sync-with-provider-x.md
					02-LOC-locate/
					03-PRP-prepare/
					04-CNF-confirm/
					05-EXE-execute/
					06-MON-monitor/
					07-MOD-modify/
					08-CLS-conclude/
				JE-RJ002-some-simple-related-job/
					README.md
					JE-RJ002-O001-minimize-time-to-crop-photos-to-print-size/
						README.md
						JE-RJ002-O001-R001-preset-aspect-ratios-for-common-frames.md
			EJ-emotional-jobs/
				JE-EJ001-some-emotional-job/
					README.md
					JE-EJ001-O001-minimize-likelihood-of-feeling-rushed-during-setup/
						README.md
						JE-EJ001-O001-R001-clear-progress-with-safe-pause-and-resume.md
				JE-EJ002-some-complex-emotional-job/
					README.md
					01-DEF-define/
						README.md
						JE-EJ002-DEF-O001-minimize-anxiety-when-sharing-screen-with-clients/
							README.md
							JE-EJ002-DEF-O001-R001-one-click-hide-sensitive-panels.md
					02-LOC-locate/
					03-PRP-prepare/
					04-CNF-confirm/
					05-EXE-execute/
					06-MON-monitor/
					07-MOD-modify/
					08-CLS-conclude/
		PLST-product-lifecycle-support-team/
			README.md
			CCJ-consumption-chain-jobs/
				PLST-CCJ001-obtain/
					README.md
					PLST-CCJ001-O001-minimize-time-to-verify-license-eligibility-before-checkout/
						README.md
						PLST-CCJ001-O001-R001-inline-seat-count-vs-entitlements.md
				PLST-CCJ002-install/
					README.md
					01-DEF-define/
						README.md
						PLST-CCJ002-DEF-O001-minimize-likelihood-of-silent-install-failure-on-windows/
							README.md
							PLST-CCJ002-DEF-O001-R001-log-bundle-path-on-failed-exit-code.md
					02-LOC-locate/
					03-PRP-prepare/
					04-CNF-confirm/
					05-EXE-execute/
					06-MON-monitor/
					07-MOD-modify/
					08-CLS-conclude/
				PLST-CCJ003-configure/
					README.md
					PLST-CCJ003-O001-minimize-time-to-connect-sso-and-map-groups-to-roles/
						README.md
						PLST-CCJ003-O001-R001-guided-idp-metadata-and-test-login.md
				PLST-CCJ004-learn-to-use/
				PLST-CCJ005-operate/
				PLST-CCJ006-integrate/
				PLST-CCJ007-maintain/
				PLST-CCJ008-monitor/
				PLST-CCJ009-secure/
				PLST-CCJ010-support/
				PLST-CCJ011-upgrade/
				PLST-CCJ012-cancel/
		PDM-purchase-decision-maker/
			README.md
			PDM-FM-O001-minimize-three-year-tco-vs-incumbent-stack/
				README.md
				PDM-FM-O001-R001-exportable-roi-assumptions-for-procurement.md
```
