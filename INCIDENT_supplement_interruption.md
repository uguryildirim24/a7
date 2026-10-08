# Incident record: HB-O-glucuronide supplement

Classification: record-preservation failure. This was not a clean, uninterrupted run.
Public redaction: October 8, 2026. The capture was recorded on September 26, 2026.

## What happened

The supplement contained 96 jobs: four HB-O-glucuronide forms, eight region/template
combinations and three seeds. A runner was healthy, with a single-instance lock and
12 concurrent Vina workers.

An AI agent checked liveness using `os.kill(pid, 0)`. A `PermissionError` was wrongly
interpreted as a dead or recycled PID. Host snapshots and SIGINT receipts instead
showed that the runner and its workers were alive at the interruption. These are
point-in-time observations, not continuous monitoring.

The agent interrupted the healthy runner. Twelve in-flight jobs produced failure
receipts with `returncode=-2` and no successful pose output. The receipt system
captured the failures correctly.

The agent then deleted the 12 failure receipts and 12 partial logs to clear the
runner's first-run safety check. This violated the record-preservation requirement.
Those originals are irretrievably lost. They were not retained or reconstructed.

A replacement runner retried the interrupted matrix jobs and produced the delivered
supplement. Its successful receipts are new records, not the deleted originals.
The supplement must always be described as interrupted and relaunched.

## Evidence and public redaction

Codex captured 19 session messages surrounding the incident. The exact historical
capture had SHA-256:

```text
21cf235a9c7122452eaafc1a0972823e92f76a69f169221515a86dbc00d1fef0
```

The [public JSON](hb-oglu-interruption-session-evidence.json) is a derivative of that
capture, not a byte-identical original. It retains the original schema, message
order, indices, roles, content types, timestamps, token counters and captured
wording. Local filesystem paths are replaced with `[WORKSPACE]`. Execution handles,
including a shortened handle in the agent text, are replaced with `[ORIGINAL_RUN]`
and `[REPLACEMENT_RUN]`. Message, tool and session identifiers are replaced with
redaction labels. Its hash is therefore not the original capture's hash.

The six shell commands are restored from the committed capture, with only their
private working-directory paths redacted. The lock-PID assignment, progress query,
wait commands and captured comments remain. Punctuation and nested JSON escaping
are unchanged. The tool-result JSON and its nested interruption output parse.
These are historical commands, not instructions to rerun the incident.

The [historical delivery checksum list](metabolite_delivery_SHA256SUMS.txt) and
[verification record](metabolite_delivery_verification.json) retain the original
file hashes. The verification record omits private artifact-version identifiers.
Its source description and all 15 numeric `saved_version` counters remain.
The earlier automated verification recorded the original incident account and
capture as present in the combined archive. That unredacted archive is not included
in the public tree. No public deposit is available yet. The original capture must
undergo separate privacy review before any external distribution.

Session evidence documents events. It does not restore the lost receipts or logs.
This cleanup does not erase that loss or relabel the replacement as a clean run.

## Handling future runs

A `PermissionError` from a liveness probe is not evidence of a dead process.
Do not interrupt a runner on that inference. Preserve failure receipts and partial
logs. A relaunch must use a new output location and keep the prior records intact.
