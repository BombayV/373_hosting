# Lesson 01 specification

## STUDIO-001 · Launch a tested calculator on an existing server

**Status:** Repeat runtime/public HTTPS/API verification passed. Learner reported matching results, chose to keep the deployment and approved the corrected summary. Full E2E/CI and GitHub completion remain pending.
**Next step:** Review the scoped diff and authorize commit/push/PR.
**Instructor implementation:** [issue #9](https://github.com/kaw393939/373_hosting/issues/9).
Create your own issue from the [lesson template](.github/ISSUE_TEMPLATE/studio-calculator.md).

## Agreed result

Launch the supplied published calculator image through your existing Traefik
network and a nonconflicting HTTPS hostname. Preserve unrelated services and
host access. Do not add another proxy/updater or build a substitute image.
The [release selection](studio/calculator-release.json) supplies the expected
commit and multi-platform digest independently of the running website.
An explicitly agreed adoption of a matching existing deployment is recorded
as adoption, not a fresh launch. This bounded lesson does not certify the whole
server baseline or a vulnerability-free image.

- **Public hostname:** https://373ai.bombayv.com.
- **New launch or adopted deployment, and reason:** New launch agreed by the learner; read-only doctor returned `ready` / `launch-new` with no selected routing conflict.
- **Own issue / feature branch:** [Issue #1](https://github.com/BombayV/373_hosting/issues/1); `codex/studio-001-calculator`.
- **Agreed scope or actual access/configuration gap:** One pinned published calculator image on the existing Docker/Traefik server and `traefik-proxy` network, preserving existing proxy and applications. Laptop setup, launch with reviewed routing repairs, and repeat public HTTPS/API checks completed.
- **Release source:** [calculator-release.json](studio/calculator-release.json), image digest `sha256:aec414c990a5de6ed74c9e8dcb105b78f6358c03a8cea70a9d40dcda51c3a8fa`, expected commit `4600202bad42da0c5ffb11d83ce8364671293d3d`.
- **Reviewed compatibility adjustment:** The existing `websecure` entrypoint has no default TLS setting. Learner approved explicit calculator router labels `tls=true` and `tls.certresolver=letsencrypt`, using the existing resolver. This adjustment is in the ignored remote Compose manifest; the template generator does not yet reproduce it. Proxy and unrelated application configuration are unchanged.
- **Actual routing repair:** Further inspection established that Traefik enables only its file provider and does not read Docker labels. With learner approval, added only `/home/bombayv/traefik/dynamic/studio-calculator.yml`, routing the agreed hostname on `websecure` to `http://is373-studio-calculator-calculator-1:8000`, with the existing `letsencrypt` resolver. Existing routing file hashes and unrelated container IDs/start times were unchanged; Traefik was not restarted. The earlier labels alone did not fix routing. Both direct-origin trusted HTTPS and public Cloudflare HTTPS subsequently returned HTTP 200 for `/health` with the expected commit. The template CLI does not yet reproduce this file-provider adjustment.
- **Launch evidence limit:** The initial launch started the calculator but failed public verification during DNS/routing troubleshooting. No successful initial new-launch report was produced; any later `already-managed` report establishes repeat verification only.

Private SSH targets and configuration stay in ignored local state. Share only
reviewed, selected evidence; never commit credentials or raw server output.

## Evidence to keep

| Evidence | Actual result / link |
|---|---|
| Prepared Black/Pylint/pytest and real-image browser checks | Fast checks passed after checker change: Black, Pylint, 91 tests. Two E2E tests deselected; full CI remains pending because local Docker is not running. |
| Hosted image/commit, trusted HTTPS, valid and rejected API cases | Repeat verification passed; [sanitized evidence](studio/evidence.json). Report correctly says `already-managed`, not a successful initial new-launch report. |
| Preservation of unrelated services | Existing route file hashes and unrelated container IDs/start times unchanged during repair; repeat verifier confirms three unrelated containers' selected identity/state/ports unchanged. |
| Own prediction, check interpretation, browser observation and keep/revise reason | [LEARNING.md](LEARNING.md), drafted from this chat with AI assistance and learner corrections disclosed. Learner clarified prior knowledge of Traefik and unclear question wording; no knowledge gap is inferred. Own-site numeric results were not stated. |
| Accuracy review before publishing learner excerpts | Learner approved the corrected summary in chat; edited explanation is labeled as supplied through the local file. |
| Actual PR, latest CI, merge and issue closure | Pending |

Link the exported `studio/evidence.json`, actual CI and issue/PR when available.
The checker now identifies HTTP requests as `IS373-Studio/1.0`: Cloudflare
rejected Python's default identity with HTTP 403/error 1010. TLS validation and
all health/API assertions remain intact. Cloudflare settings were not changed.
CI does not deploy this server. A fixture, green check, timestamp, closed issue
or AI assertion alone does not establish the full result. `status` reports
recorded evidence and readiness for instructor review; it does not grade,
certify authorship or establish understanding.

## Optional instructor history

The records below are background, not steps to repeat. Their original anchors
remain here so earlier links continue to work.

## HOST-001 · Keep the Traefik dashboard private

[Historical requirement and evidence](book/changes/hosting-spec-history.md#host-001--keep-the-traefik-dashboard-private).

## HOST-002 · Controlled host maintenance

[Historical requirement and evidence](book/changes/hosting-spec-history.md#host-002--controlled-host-maintenance).

## HOST-003 · Companion image security maintenance

[Historical requirement and evidence](book/changes/hosting-spec-history.md#host-003--companion-image-security-maintenance).
