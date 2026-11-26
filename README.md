# Scarab conformance reports

Generated reports of [Scarab](https://github.com/KD5UJC-XYZ/scarab), a Cardano node in Scala, for pragma-org's
[node-diversity-conformance](https://pragma-org.github.io/node-diversity-conformance/) site. They are written by `scripts/conformance/run.py` and published on
demand by `scripts/conformance/publish.py` of the Scarab repository (`docs/running/conformance.md` there), which
also writes this file: do not edit it by hand. Scarab's Plutus evaluator is its own (`uplc`).

- `latest/<scenario>[-<era>].json.gz`: the newest report of each scenario and era, which the site reads from
  `https://raw.githubusercontent.com/KD5UJC-XYZ/scarab-conformance/main/latest/`, with its `.provenance.json` beside it.
- `reports/<scenario>/scarab-YYYYMMDD-<scenario>[-<era>].json.gz`: every published report, dated (UTC) by its
  `generated_at`, with its `.provenance.json`: the Scarab commit, the pinned inputs and their checksums, the tool, its
  arguments, where it ran (the runner, and the CPU and limits of its container) and the checks the report passed.

## Results

The scores of the reports in `latest/`, as pragma-org's [node-diversity-conformance](https://pragma-org.github.io/node-diversity-conformance/) site computes them by its
rules at [`628006278`](https://github.com/pragma-org/node-diversity-conformance/tree/628006278309c02a1c3e49dce00e43595d925c2e), computed again each time
reports are published.
The overall score is the mean of the ratios of the site's 4 scenarios; a scenario without a
readable report counts zero.
Ratios are shown as the site shows them, cut to two decimals.

| Scenario | Met | Total | Ratio | Scored |
|---|--:|--:|--:|---|
| `cbor-decoding`, Conway | 43,313 | 43,434 | 99.72% | yes |
| `cbor-decoding`, Dijkstra | 39,309 | 40,437 | 97.21% | no |
| `ledger-rules` | 368 | 368 | 100% | yes |
| `uplc-conformance` | 1,063 | 1,064 | 99.90% | yes |
| `uplc-turbo` | 3,993 | 3,997 | 99.89% | yes |
| **Overall** | | | **99.88%** | |

- `cbor-decoding`: a sample is met when it decodes as the dataset expects.
  The site scores a node by its Conway report, or by another era's when it has no Conway report it can read.
- `ledger-rules`: a fixture of the site's corpus is met when the reported result is the one the fixture expects
  (`pass`, the failing predicate, or `DecodingFailure`); a fixture without a result fails.
- `uplc-conformance`: an expected vector is met when the vector reported for its id, Plutus version and protocol
  version gives the expected result, whitespace aside, and, where a budget is expected, the expected budget.
- `uplc-turbo`: a benchmark of the corpus is met when its CPU time is at most twice its CPU budget or within
  200 µs of it, and its memory at most twice its memory budget or within 320 KiB of it;
  a benchmark that is not reported fails.
  The times depend on the machine that took them, which the report's provenance names.
  The site also fails a benchmark whose budget disagrees with the other nodes' reports, which this count leaves out.

## Reports in `latest/`

| Report | Date (UTC) | Scarab commit | sha256 of the file |
|---|---|---|---|
| [`cbor-decoding-conway`](latest/cbor-decoding-conway.json.gz) | 2026-11-26 | [`5adbb7e95`](https://github.com/KD5UJC-XYZ/scarab/commit/5adbb7e9594f67bf29aea69a07b8d19346d5addd) | `77d79ca1dfc5b510` |
| [`cbor-decoding-dijkstra`](latest/cbor-decoding-dijkstra.json.gz) | 2026-11-26 | [`5adbb7e95`](https://github.com/KD5UJC-XYZ/scarab/commit/5adbb7e9594f67bf29aea69a07b8d19346d5addd) | `99fda71ccadcb815` |
| [`ledger-rules`](latest/ledger-rules.json.gz) | 2026-11-26 | [`5adbb7e95`](https://github.com/KD5UJC-XYZ/scarab/commit/5adbb7e9594f67bf29aea69a07b8d19346d5addd) | `588ef6187c6195bc` |
| [`uplc-conformance`](latest/uplc-conformance.json.gz) | 2026-11-26 | [`5adbb7e95`](https://github.com/KD5UJC-XYZ/scarab/commit/5adbb7e9594f67bf29aea69a07b8d19346d5addd) | `c1e3cd0cac0e7c08` |
| [`uplc-turbo`](latest/uplc-turbo.json.gz) | 2026-11-26 | [`5adbb7e95`](https://github.com/KD5UJC-XYZ/scarab/commit/5adbb7e9594f67bf29aea69a07b8d19346d5addd) | `15f8ea96f51523ec` |
