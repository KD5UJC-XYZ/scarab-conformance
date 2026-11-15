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

| Report | Date (UTC) | Scarab commit | sha256 of the file |
|---|---|---|---|
| [`cbor-decoding-conway`](latest/cbor-decoding-conway.json.gz) | 2026-11-15 | [`82dbb87b4`](https://github.com/KD5UJC-XYZ/scarab/commit/82dbb87b44c15c8baf2dcf8792e7035bdc516440) | `a5bbabefddce86f7` |
| [`cbor-decoding-dijkstra`](latest/cbor-decoding-dijkstra.json.gz) | 2026-11-15 | [`82dbb87b4`](https://github.com/KD5UJC-XYZ/scarab/commit/82dbb87b44c15c8baf2dcf8792e7035bdc516440) | `2ddb7c86c64be928` |
| [`ledger-rules`](latest/ledger-rules.json.gz) | 2026-11-15 | [`15cb6528b`](https://github.com/KD5UJC-XYZ/scarab/commit/15cb6528b9fd9f4d78e8a1c2148f7a5bc599e248) | `a4694392891b43e2` |
| [`uplc-conformance`](latest/uplc-conformance.json.gz) | 2026-11-15 | [`15cb6528b`](https://github.com/KD5UJC-XYZ/scarab/commit/15cb6528b9fd9f4d78e8a1c2148f7a5bc599e248) | `d8137bc83de59eae` |
| [`uplc-turbo`](latest/uplc-turbo.json.gz) | 2026-11-15 | [`6ea35198b`](https://github.com/KD5UJC-XYZ/scarab/commit/6ea35198b29bb0bc291c5a68c6f923fcf8d6d0cd) | `6463013ac0134f0d` |
