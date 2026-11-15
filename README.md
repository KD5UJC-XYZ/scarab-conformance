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
| [`uplc-turbo`](latest/uplc-turbo.json.gz) | 2026-11-15 | [`6ea35198b`](https://github.com/KD5UJC-XYZ/scarab/commit/6ea35198b29bb0bc291c5a68c6f923fcf8d6d0cd) | `6463013ac0134f0d` |
