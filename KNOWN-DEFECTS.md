# What Scarab's reports still miss

The scores in [README.md](README.md) are computed by the site's rules from the reports in `latest/`. This page
lists every case those reports do not meet, by scenario, with what is known about each and where it is
tracked. Unlike `README.md`, it is written by hand, and it is brought up to date when reports are published;
a case leaves the page when a report meets it.

As of the reports of Scarab [`5adbb7e95`](https://github.com/KD5UJC-XYZ/scarab/commit/5adbb7e9594f67bf29aea69a07b8d19346d5addd),
published 2026-11-26.

## uplc-turbo: 4 of 3,997 programs

Measured on a GitHub-hosted runner with an Intel Xeon 6975P-C, with 3 CPUs and 8 GB given to the container.

One defect:

| Program | Missed on | CPU time | Memory | Tracked |
|---|---|---:|---:|---|
| `8100C5F1EEA24F95…-0-D0E1E5DC…-v2` | memory and CPU time | about 45 times budget | 1,646 times budget | [scarab#1475](https://github.com/KD5UJC-XYZ/scarab/issues/1475) |

It is missed in every run, on every machine, by the same margin. Its cost is in arbitrary-precision integer
arithmetic.

Programs at the CPU limit. The other three programs this report misses are over on CPU time alone, at 2.05
to 2.20 times budget, where the limit is two times. Which programs these are changes from report to report:
across eight runs on this CPU (2026-11-25 and 26) a report met between 3,992 and 3,995 programs, each
missing one to four programs on CPU time alone at 2.0 to 2.9 times budget, and not the same ones. They are
programs Scarab evaluates in about twice their budget, which a run's variation puts on either side of the
limit, so they are described here and not listed.

The score depends on the CPU that measured it. One run on an Intel Xeon Platinum 8370C met 3,857 programs,
139 of them over on CPU time alone. Reports are published only from the CPU named above, and each report's
provenance names the CPU it was written on.

Memory: 3,996 of 3,997 programs are within the memory limit, in every run.

## uplc-conformance: 1 of 1,064 vectors

| Vector | The site expects | Scarab reports | Tracked |
|---|---|---|---|
| `term_constr_constr_07_v3` (Plutus V3, protocol 11.0) | parse/decode error | evaluation failure | [scarab#1474](https://github.com/KD5UJC-XYZ/scarab/issues/1474) |

The program is a constructor whose tag is the largest 64-bit word. The cause is not yet established: the
issue records that the upstream corpus's own expectation for the program is a third answer.

## cbor-decoding, Conway: 121 of 43,434 samples

| Rule | Matched | Mismatched |
|---|---:|---:|
| `auxiliary_data_array` | 427 | 50 |
| `header` | 476 | 34 |
| `header_body` | 497 | 23 |
| `auxiliary_data` | 437 | 14 |

Every other rule of the dataset matches on all its samples. The causes have not been looked into; that
starts in [scarab#1476](https://github.com/KD5UJC-XYZ/scarab/issues/1476).

## cbor-decoding, Dijkstra: 1,128 of 40,437 samples

The site shows this report and does not score it.

| Rule | Matched | Mismatched |
|---|---:|---:|
| `block` | 1,818 | 606 |
| `block_body` | 307 | 103 |
| `transaction_body` | 342 | 103 |
| `account_balance_intervals` | 303 | 102 |
| `transaction` | 307 | 101 |
| `sub_transaction_body` | 329 | 95 |
| `header_body` | 411 | 12 |
| `header` | 407 | 5 |
| `transaction_witness_set` | 434 | 1 |

The containing rules (`block`, `block_body`, `transaction`) count a sample as mismatched when any part of
it is, so these rows overlap. The causes have not been looked into; also
[scarab#1476](https://github.com/KD5UJC-XYZ/scarab/issues/1476).

## ledger-rules: none

All 368 fixtures are met.
