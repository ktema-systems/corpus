# Ktema Systems Corpus

The published corpus of Ktema Systems. This repository holds no source. A publishing tool in the
producing repository writes one commit per publish, and a reader takes what it needs from a ref.

## What it holds

The hub carries the corpus rather than one of its renderings.

| Path | What it is |
|---|---|
| `corpus/vol/` | the volume the engine wrote: one record per address, byte for byte |
| `corpus/docs/` | the documents as written |
| `corpus/master.md` | the plan and the decisions behind the corpus |
| `corpus/subjects.json`, `corpus/depends.json` | the subjects a run belongs to and the claims a page depends on |
| `export/` | the corpus as a viewer reads it: `bench.json`, `corpus.json`, `runs.json`, `values.json`, `docs/`, `documents.txt`, `digest` |

`export/` is derived from `corpus/vol/` by the producing repository's assembly stage. It is here
because it is the stable contract a viewer reads; a viewer that opened `vol/` directly would make
the engine's frame format a public interface.

`index.json` states the digest, what the hub holds, and the renderings built from it.

## How to read it

Everything is fetched from `https://raw.githubusercontent.com/ktema-systems/corpus/main/`. A viewer
reads `export/`; a reader that wants the primary record reads `corpus/vol/`.

A document's list travels as `export/documents.txt` rather than as a directory listing, because a
raw host serves files and not directories.

## What this does not establish

The digest proves the export is the one a publisher wrote. It does not prove the numbers behind
it: each run's own record establishes those. A rendering built from this export is a projection,
and it states the digest it was built from.

The media a demonstration was recorded from is not here. A manifest in `corpus/` names what a run
was made from, and the recorded video is served from the asset bucket.

## Licence

Apache 2.0, as the tree that produced the corpus.
