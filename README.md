# Ktema Systems Corpus

The published records of Ktema Systems. This repository holds no source. A producer deposits
what it has settled; a viewer reads it.

## What it holds

| Path | What it is |
|---|---|
| `corpus/vol/` | the volume the engine wrote: one record per address |
| `corpus/docs/` | the documents as written |
| `corpus/master.md` | the plan behind the corpus |
| `corpus/subjects.json`, `corpus/depends.json` | the subjects a run belongs to, and the claims a page rests on |
| `export/` | the corpus as a viewer reads it: `bench.json`, `corpus.json`, `runs.json`, `values.json`, `docs/`, `documents.txt`, `digest` |

`export/` is derived from `corpus/vol/`. A viewer reads `export/`, because a viewer that opened
`vol/` directly would make the engine's frame format a public interface.

## Reading it

Everything is served from `https://raw.githubusercontent.com/ktema-systems/corpus/main/`. A
document's list is `export/documents.txt`.

`index.json` states the digest, what the repository holds, and the renderings built from it.

## Running it

```sh
curl -sO https://raw.githubusercontent.com/ktema-systems/corpus/main/export/bench.json
```

The digest in `export/digest` is over `export/` alone, so a copy can be checked without the
volume.

## Licence

Apache 2.0.
