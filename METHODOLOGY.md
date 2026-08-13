# Methodology

## Scope

- Model: `xai/grok-4.6`
- Route: MERGE Gateway
- Benchmark source: Terminal-Bench 2.0
- Tasks: `fix-git`, `regex-log`, and `nginx-request-logging`
- Harnesses: Grok Build, OpenCode, Codex, Claude Code, and Pi
- Attempts: one per task/harness pair
- Total trials: 15
- Agent execution limit: 300 seconds per trial

## Timing

Time-to-green uses Harbor's `agent_execution` interval. Environment setup,
harness installation, and verification time are excluded. A timed-out attempt
is charged its full 300-second execution limit when calculating verified
solutions per agent-hour.

The displayed per-harness median is the median execution time among verified
trials. Pass counts are displayed beside each median so failures remain visible.

## Concurrency

The five `fix-git` trials ran sequentially. The `regex-log` and
`nginx-request-logging` trials ran with at most two concurrent trials to reduce
wall-clock time. No Gateway rate-limit errors occurred.

## Results and exclusions

Thirteen of fifteen trials passed verification. OpenCode timed out on `fix-git`.
Pi failed `nginx-request-logging` because Nginx was not running when the verifier
made requests.

An earlier attempt containing `build-cython-ext` was stopped because native
dependency compilation dominated the five-minute marketing sprint. Those
trials are excluded from every result in this bundle.

## Cost

The approximately $2.13 cost combines adapter-reported cost with estimates from
token logs at the MERGE Gateway rates available during the run. It should be
presented as an estimate, not an invoice total.

## Limitations

This is a small, curated, single-attempt showcase. It is suitable for a clearly
labeled marketing demonstration, not for claims about the complete
Terminal-Bench 2.0 dataset or statistical superiority over other models.
