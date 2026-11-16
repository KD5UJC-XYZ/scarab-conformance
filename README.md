# Scarab conformance reports

Generated reports of [Scarab](https://github.com/KD5UJC-XYZ/scarab), a Cardano node in Scala, for pragma-org's
[node-diversity-conformance](https://pragma-org.github.io/node-diversity-conformance/) site. They are written by `scripts/conformance/run.py` and published on
demand by `scripts/conformance/publish.py` of the Scarab repository (`docs/running/conformance.md` there), which
also writes this file: do not edit it by hand. The Plutus scenarios report Scarab's own evaluator
(`--plutus-vm scarab`).

- `latest/<scenario>[-<era>].json.gz`: the newest report of each scenario and era, which the site reads from
  `https://raw.githubusercontent.com/KD5UJC-XYZ/scarab-conformance/main/latest/`, with its `.provenance.json` beside it.
- `reports/<scenario>/scarab-YYYYMMDD-<scenario>[-<era>].json.gz`: every published report, dated (UTC) by its
  `generated_at`, with its `.provenance.json`: the Scarab commit, the pinned inputs and their checksums, the tool, its
  arguments and the checks the report passed.

## Results

The scores of the reports in `latest/`, as pragma-org's [node-diversity-conformance](https://pragma-org.github.io/node-diversity-conformance/) site computes them by its
rules at [`9dc68a750`](https://github.com/pragma-org/node-diversity-conformance/tree/9dc68a750478335755d057288cc8978c117d7ac4), computed again each time
reports are published.
The overall score is the mean of the ratios of the site's 4 scenarios; a scenario without a
readable report counts zero.
Ratios are shown as the site shows them, cut to two decimals.

| Scenario | Met | Total | Ratio | Scored |
|---|--:|--:|--:|---|
| `cbor-decoding`, Conway | 43,276 | 43,434 | 99.63% | yes |
| `cbor-decoding`, Dijkstra | 34,049 | 40,437 | 84.20% | no |
| `ledger-rules` | 368 | 368 | 100% | yes |
| `uplc-conformance` | 1,063 | 1,064 | 99.90% | yes |
| `uplc-turbo` | 3,660 | 3,997 | 91.56% | yes |
| **Overall** | | | **97.77%** | |

- `cbor-decoding`: a sample is met when it decodes as the dataset expects.
  The site scores a node by its Conway report, or by another era's when it has no Conway report it can read.
- `ledger-rules`: a fixture of the site's corpus is met when the reported result is the one the fixture expects
  (`pass`, the failing predicate, or `DecodingFailure`); a fixture without a result fails.
- `uplc-conformance`: an expected vector is met when the vector reported for its id, Plutus version and protocol
  version gives the expected result, whitespace aside, and, where a budget is expected, the expected budget.
- `uplc-turbo`: a benchmark of the corpus is met when its CPU time is at most twice its CPU budget or within
  200 µs of it, and its memory at most twice its memory budget or within 320 KiB of it;
  a benchmark that is not reported fails.
  The times depend on the machine that took them.
  The site also fails a benchmark whose budget disagrees with the other nodes' reports, which this count leaves out.

## Reports in `latest/`

| Report | Date (UTC) | Scarab commit | sha256 of the file |
|---|---|---|---|
| [`cbor-decoding-conway`](latest/cbor-decoding-conway.json.gz) | 2026-11-16 | [`2d837171d`](https://github.com/KD5UJC-XYZ/scarab/commit/2d837171de3676d940b37ad88b2670f692c39894) | `4b8d2b660f3e5047` |
| [`cbor-decoding-dijkstra`](latest/cbor-decoding-dijkstra.json.gz) | 2026-11-16 | [`2d837171d`](https://github.com/KD5UJC-XYZ/scarab/commit/2d837171de3676d940b37ad88b2670f692c39894) | `5102d101b8d16d5b` |
| [`ledger-rules`](latest/ledger-rules.json.gz) | 2026-11-15 | [`15cb6528b`](https://github.com/KD5UJC-XYZ/scarab/commit/15cb6528b9fd9f4d78e8a1c2148f7a5bc599e248) | `a4694392891b43e2` |
| [`uplc-conformance`](latest/uplc-conformance.json.gz) | 2026-11-15 | [`15cb6528b`](https://github.com/KD5UJC-XYZ/scarab/commit/15cb6528b9fd9f4d78e8a1c2148f7a5bc599e248) | `d8137bc83de59eae` |
| [`uplc-turbo`](latest/uplc-turbo.json.gz) | 2026-11-15 | [`6ea35198b`](https://github.com/KD5UJC-XYZ/scarab/commit/6ea35198b29bb0bc291c5a68c6f923fcf8d6d0cd) | `6463013ac0134f0d` |
