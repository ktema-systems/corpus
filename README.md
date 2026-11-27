# Ktema Systems Corpus Board

The records the Ktema Systems corpus publishes: what each run measured, the documents
written about it, and the rows a viewer draws.

## What it holds

| Path | What it is |
|---|---|
| `export/` | the corpus as a viewer reads it: `bench.json`, `corpus.json`, `runs.json`, `values.json`, `docs/`, `documents.txt`, `digest` |
| `corpus/docs/` | the documents as written |
| `corpus/vol/` | the records, one file per address |
| `corpus/subjects.json`, `corpus/depends.json` | the subjects a run belongs to, and the claims a page rests on |

`export/` is derived from `corpus/vol/` and is what the viewer reads. `export/digest` is over
that directory alone, so a copy can be checked without the volume.

## Reading it

Everything is served from `https://raw.githubusercontent.com/ktema-systems/corpus-board/main/`.
`index.json` states the digest, what the board holds, and the pages built from it.
`export/documents.txt` lists the documents.

```sh
curl -sO https://raw.githubusercontent.com/ktema-systems/corpus-board/main/export/bench.json
```

## Licence

Apache 2.0.
