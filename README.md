# semdev-test

Disposable target repo for exercising the semdev issue→PR flow end-to-end.

`example.com/health` classifies cpu/mem pressure. There is a known boundary bug
in `Classify` (see the open issue); its test fails until the boundary is fixed.

## Submodule fixture layout (semsource#185)

This repo doubles as the git-submodule ingestion fixture for
[semsource#185](https://github.com/C360Studio/semsource/issues/185). It links
[`semdev-test-sub`](https://github.com/C360Studio/semdev-test-sub) **twice at
different pinned commits**:

| Path                     | Pin | Distinguishing symbol            |
| ------------------------ | --- | -------------------------------- |
| `semdev-test-sub`        | v2  | has `greeter.Farewell`           |
| `nested/semdev-test-sub` | v1  | no `Farewell` (baseline greeter) |

The dual pin exercises shared-submodule dedup and gitlink-SHA version scoping;
the `nested/` path exercises submodules below the repo root. Do not "helpfully"
sync the two pins to the same SHA — the divergence is the point. SemSource
tests read these gitlink SHAs; move a pin only additively (both repos keep
history append-only).
