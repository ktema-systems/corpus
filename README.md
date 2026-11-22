# Ktema Systems Corpus

The published artifacts of the Ktema Systems corpus. This repository holds no source. A
publishing tool in the producing repository writes one commit per publish, and a reader takes
everything it needs from a single ref.

## What it holds

`export/` is the corpus as an artifact. It is produced from a volume written by the engine and
carries no timestamp of its own, so a given export names one state of the tree.

| Path | What it is |
|---|---|
| `export/bench.json` | the measurements, one entry per run with its revision and its numbers |
| `export/corpus.json` | the produced units and the subjects they belong to |
| `export/runs.json` | the demo runs |
| `export/values.json` | every fact a run establishes, addressed by coordinate |
| `export/docs/` | the documents as written, rendered by the site |
| `export/documents.txt` | the document list a site build reads |
| `export/digest` | the digest of the export it belongs to |

`index.json` names the export, the renderings built on it, and the digest they share.

## How to read it

Every file is fetched from `https://raw.githubusercontent.com/ktema-systems/corpus/main/export`.
There is no index to follow and no API call to make: a consumer resolves a unit by the address
its fields compute, which is the same rule the engine uses.

## What this does not establish

The digest proves the export is the one a publisher wrote. It does not prove the numbers behind
it, which the run's own record establishes. A rendering built from this export is a projection,
and it states the digest it was built from.

## Licence

Apache 2.0, as the tree that produced the artifacts.
