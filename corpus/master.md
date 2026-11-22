# Ktema corpus master

Status: living. This file is updated as work lands, and it is the only place the
plan's state is written.

The specs it rests on are `docs/spec/ktema-corpus-0.1.md`, which states the corpus,
a project, and a projection, and `docs/spec/ktema-evidence-0.1.md`, which states
the record and its key. Where this file and a spec disagree, the spec wins and
this file is wrong.

## Where it stands

| Work | State | Where |
|---|---|---|
| the corpus spec | done | `docs/spec/ktema-corpus-0.1.md` |
| the bench lander | done | `corpus/assembly/land.sh` |
| bench records | landed, 17 across 12 revisions | `corpus/vol/`, keys under `bench/` |
| bench lands itself | done, both suites | `bench/run.sh`, `bench/peers/run.sh` |
| the project list | done, 4 subjects | `apps/delta/tools/corpus.mjs` in kletos |
| a take's claim sentence | done, three packages | `demo/<package>/claim.txt` |
| a take's revision stamp | next | `demo/_shared/run.sh` |
| demo records | done, 2 of 3 packages | `corpus/vol/`, keys under `demo/` |
| the demo documents | done | `corpus/docs/`, exported to the center |
| `depends` per claim | done | `corpus/depends.json` |
| the ladder a projection draws, declared | done | `corpus/subjects.json` |
| the corpus stored on the engine | done | `vol/` is a volume; `assembly/migrate.sh` moved it |
| the shape per revision, as a record | next | `verify/shape` |
| a digest over sorted test names | next | `verify/shape/check.sh` |
| `corpus/state.sh`, the four states | after the three above | `corpus/` |
| the centre page | after the states | `ktema_www/demo` |
| the Delta board | done, one room per activity | `apps/delta/tools/corpus-board.mjs` in kletos |
| the edge board | later, and not on this path | the node section below |

## This stage

Demonstration and measurement. Each is one command that ends at a page, and the page
states no number the records do not carry.

A take is performed by a person and its artifacts are made by hand. The corpus does not ask
that to change; it asks each artifact to enter at the place the format names, so a page reads
it rather than keeping a copy. What stays manual is listed under `What stays manual` further
down, and none of it is a defect.

| Work | What it unblocks |
|---|---|
| `peer-baselines` measured at one revision with `volume-sweep` | a comparison whose two halves name one revision |
| the take's revision written at recording time, and `bundle.sh` reading it | a demo record that does not say `revision_inferred` |
| `fpga-icesugarpro-keyspace` either a take or an intent | every package with a claim has a state |
| `verify/shape` per revision, and a digest over sorted test names | the four states |
| `corpus/state.sh` | `current`, `shape-current`, `stale`, `unknown` |

A subject states its space and its row shape, and the export reads both (#93). The comparison
page draws the baseline rows from the record, and its source line cites the two keys.

The peers were measured at `8f7da4a+` and the sweep at `8b5e3a3+`, so the page names both until
one run measures the pair at a single revision.

A measurement is still triggered by a person. The stage moves what a finished run reaches,
not how often a run happens.

Trial is built and not in this stage. `trial/run.sh` passes, no record lands, and no page
draws it. It waits on a party, and the flow it would use is the one above, exercised on
demonstration and measurement first.

## The work this replaces

Three chores repeat whenever the engine's shape moves. A benchmark goes stale and
nobody knows by how much. A demo that showed the old shape keeps being shown. A
page states a number the current run no longer produces. Each has been done by
hand, and each hand correction is one more place where the record and the page can
disagree.

The flow below exists to make those three chores mechanical.

## Three stages

```text
raw source  →  corpus  →  projection
bench, demo take, trial     records by key     a selection, rendered
```

A raw source runs. The corpus holds what the run established, addressed by the key
of `ktema-evidence-0.1.md`. A projection selects entries and renders them for one
reader.

Nothing downstream adds a number. Nothing upstream decides how it will be drawn.

The projections are one export read three ways: the center renders the documents and the rows
a page draws, the Delta board renders the subjects as rooms, and a document build renders the
same text as a PDF. The export reaches the Delta tree by a copy a person runs, because the
board reads files rather than the volume the assembler wrote. That copy is the first
migration, and it is the one step in the flow a person performs.

A page is read for that migration and not after it. A take bundled from now on states where it
can be fetched (`VIDEO_URL` when `demo/_shared/bundle.sh` runs), so the record is the whole of
what a board needs; a record that names a file this tree holds is one made before that, and
the page is read for it once.

## Who does what

| Actor | Does | Never does |
|---|---|---|
| ktema | writes a record when a run happens | reads |
| kletos | aggregates records and answers over a volume | invents a number |
| an analyst, a model or a person | reads records and writes a derived record | stays in the read path |
| Delta | reads a volume and draws it | calls a model |

The model is an ingestion-time tool. What it concludes becomes a record with its own
key, its own `claim`, and the keys it derived from. From then on the conclusion is
readable without the model, by walking to those keys.

That is what makes the corpus worth keeping. A reader of a page never waits on a
model, and a page a model wrote is still checkable by a person, because every
sentence in it reduces to records that were written before it.

A derived record is `partial` by construction. A tree of them is what the FIH tree
is: each node cites its parents, so a conclusion unwinds to the runs under it and a
new analysis of the same records is a new record rather than an overwrite.

One gap follows. `parent` is singular in version 0.1, so a node derived from two
sources cannot state both in its key. The tree needs the list, which is version
0.2.

## The tree

```text
corpus/
  vol/                records by key, and nothing else
  out/                what a run produced: takes and reports, not tracked
  assembly/land.sh       what assembles a run's output into a record
  assembly/export.sh     what assembles records into the rows a page reads
  export/             what export.sh wrote: the rows a page reads, tracked
  master.md           this file
  AGENTS.md           the rules, for whoever changes this directory
```

The producers are outside: `demo/`, `bench/`, and `trial/` at the root, next to
`crates/` and `verify/`. The corpus consumes what they leave, so it can be moved to
another repository without taking a producer with it.

The interface is one directory and two commands. A producer writes a bundle into
`corpus/out/<activity>/<subject>/<created>/` with a manifest that states what the run
was and a payload that is its output, `land.sh` turns that into `corpus/vol/`, and
`export.sh` turns the volume into the file a page reads.

Because the manifest states the run, the assembler knows no stack. An adapter that
talks to a board, a crate, or a serial port belongs with the stack it serves, and
what crosses into the corpus is a file whose meaning is written on it.

`assembly/` is the corpus's own code, and it plays the role the engine plays one
layer down: it loads what every stack left, assembles that into records, and writes
what a page reads. It is not named `engine` because that word already names the
subject in every other sentence.

Its test is that it assembles and never measures. A script that measures belongs
with the stack it measures.

`vol` is a ktema volume: `facts/f_<coordinate>.fact`, `blob/<sha256>.bin` with its
media type, and a `format` file. A record is deposited by name and the engine
computes the coordinate, 60 base-36 digits over 20 axes. The corpus is therefore
stored by the engine it describes, and a read here walks the same keys a read
elsewhere would.

The earlier tree, one JSON file per record with its key as its path, was moved once
by `corpus/assembly/migrate.sh`; nothing writes that shape any more.

`out` is replaceable: a take is published elsewhere and the record carries its
digest, so losing `out` costs the footage and not the evidence.

## What is live

| Activity | State | Where it is produced |
|---|---|---|
| demo | live | `demo/`, three packages, recorded by hand |
| bench | live | `bench/`, and its records are the measurement |
| trial | built, and not current | `trial/`, gated, waiting on a party to run it |
| verify | the engine's own gate | `verify/`, outside the corpus |

Measurement rides inside the demo surface today: the centre's Measurements page is
a projection of the bench records rather than a fourth activity. The two producers
are already separate in this tree, and a page that draws them together does not
make them one.

## The boundary

Three tests, and nothing here passes one by accident.

| Part | Holds | The test |
|---|---|---|
| `vol` | records in key order, and nothing else | every file is a record whose key is its path |
| `out` | what a run produced | losing it costs the footage, not the evidence |
| `land.sh`, `export.sh` | the only code in this directory | removing it stops the volume being written |

The engine is the subject and is none of the three. `crates/`, `verify/`, `docs/`,
and the gates describe and prove the thing being measured; `demo/`, `bench/`, and
`trial/` produce its evidence. They stay outside the corpus: a record's subject is
not also its container, and a producer is not the corpus it feeds.

## The words

| Word | What it names |
|---|---|
| spec space | what `ev` classifies: a declared space of points |
| corpus space | what this tree accumulates: the entries runs established |
| record | one entry, a fact in the format's terms |
| claim | the axis a record hangs on, and the sentence a page is held to |
| board | which projects stand on a floor, which is the drawing and not the corpus |
| projection | a selection of the corpus, rendered for one reader |

Two candidates were refused. `record` as the name of the space reads as read-only,
and the space will carry derived output. `oracle` is refused by
`ktema-evidence-0.1.md`, which will not let a partial record be read as an oracle.
So the space is `corpus` and its unit is `record`.

## What is landed

Seventeen benchmark records, across twelve revisions, under the key order. Two subjects
reach the export, `volume-sweep` and `peer-baselines`, and each states the shape its rows
take in `corpus/subjects.json`.

```text
corpus/vol/bench/661c1bf+/host/volume-sweep/2026-11-06T04:32:25Z.json
```

Each carries the run's own `claim`, built from the payload's numbers, and a
`content_hash` over the payload bytes as written, so a reader reproduces the digest
with `jq -j .payload <record> | shasum -a 256`. `class` is `partial`, because a
sweep over two sizes is a sample of sizes however exact each measurement is.
`bench/run.sh` lands its own report, so a run does not depend on someone
remembering.

The project list in Delta carries four subjects, generated from the export. Their
`evidence` is empty, which the format reads as an intent.

## The four states

A record is true of the revision it names. Whether it is still true of this
revision is a separate question, and it has four answers.

| State | Meaning |
|---|---|
| `current` | the record names this revision |
| `shape-current` | the record is older, and every part of the shape it depends on is unchanged |
| `stale` | a part it depends on has moved |
| `unknown` | the record declares no dependency |

`stale` needs two things that do not exist yet: the shape of every revision kept as
a record, so two revisions can be compared, and the part of the shape a subject
actually uses. `corpus/depends.json` now states which subject each claim rests on,
which is the second of the two at the claim level.

The shape today is six scalars, from `./run.sh --shape`.

```json
{ "revision": "303a25a+", "abi": 7, "format": "0.1", "entry_points": 33, "crates": 20, "tests": 259 }
```

`tests` is a count. A demo that depends on one test cannot be decided from a count,
so the shape needs a digest over the sorted test names before that dependency can
be checked.

## Freshness

CI can keep a number true. It cannot make a number fresh. A record that is `stale`
is marked and withheld; the automation's product is the marking, not the number.

Freshness comes from a machine that keeps running. The intended node is one edge
board that runs the engine, measures it, and serves the result.

### The node and its cycle

The cycle has two phases, and the corpus is what makes them safe.

| Phase | The board | The visitor |
|---|---|---|
| measurement | the engine and the comparison runs own the whole board | reads the last complete set from a static snapshot |
| serving | a finished bundle is written beside the previous one | reads the new set after the swap |

The swap is a symbolic link, so it is atomic and no visitor reads a half-written
set. Measurement uses the whole board rather than a partitioned part of it, so the
number is the board's own and no web traffic can contaminate it.

This works because a projection reads records, and a record names its own revision
and instant. A visitor during the measurement phase is not reading a stale page.
They are reading the previous set, which is what its keys say it is.

### What the node needs

The requirements follow from the cycle.

| | |
|---|---|
| one board with Linux and enough memory for the volume under test | |
| a storage split, the OS and the static bundle on one device and the ledger and the runs on another | |
| an SSD that holds its latency under sustained writes, since a consumer drive's cache collapse appears in the graph | |
| power that survives a dropped mains, and a way to power-cycle the board remotely | |
| an outbound tunnel, because a router should keep its inbound ports closed | |
| a static file server of a few megabytes, rather than an application server | |

Candidate boards range from a 64-core RISC-V box to an ARMv9 single board computer
to a robotics kit. The prices and specifications in the survey that produced them
are unverified, so they are not repeated here; the criteria above are what a
purchase is held to.

### What the board changes

Nothing in the key. It enters through `platform` and `target`, so a record from the
board and a record from this host sit in one space and are compared by the same
walk. The board is a substitution at the write end, and it is not built.

With the board absent, the flow still runs for what needs no device. A host bench
and a host demo are device-free, and their records land the moment they run. The
centre of that flow is the kletos and ktema pair: ktema writes, kletos carries, and
Delta draws.

## What is published

The corpus is the layer that can be published while the engine stays private.

| | |
|---|---|
| publishable | `vol`, `export`, the specs, this file |
| private | `crates/`, `verify/`, and the apparatus in `demo/`, `bench/`, `trial/` |

What a stranger can check without the source: that a payload is the bytes its digest
names, that the rows a page draws are the record's rows, and that a record's key is
its path. What they cannot check is that the run happened on that code. `revision`
names a commit in a tree they do not have, so a published corpus is a receipt that
is internally consistent, not a result they can reproduce.

The bridge from believing to checking is the trial: an artifact a party links and a
take they run on their own machine. Without it a published corpus is a claim with a
receipt; with it the receipt is payable.

Two disclosures are decisions rather than inheritances. The shape's `entry_points`
names the public API surface, so the count is publishable before the header is. A
provided set is never committed, so a party's run never stands beside ours.

## The page and the board

The static page and the corpus board are two renderings of one export, and neither is the source.
The page is what a quick reader or a phone opens: the argument, the charts, the tables. The
board is what a reviewer opens when they want to pick a run and read it. Both read
`corpus/export`, so a change to a record reaches them without a second edit.

That is what keeps the page's maintenance low. A page holds no number of its own: the charts
draw the rows the export wrote, the prose substitutes those same rows, and the documents are
the corpus's markdown rather than a copy kept beside the site.
`export/values.json` states the strings a document's placeholders ask for, computed by the
same assembly. A name the document asks for and the export does not state fails the export,
and a value no document asks for fails it too, so the two sides of a binding are compared
where the corpus is written rather than where a page is built. A build refuses a copy the
export moved past, and a run takes the export in before it serves. What remains authored is
the argument, and it changes when the argument changes.

A run is addressable: `subject/store/platform@created@revision` is the origin one run's
numbers are filed under. The board lists a subject's runs newest first and opens the one a
reader picks, so the history in the volume is reachable rather than retained.

## The one flow

A run is measured by a producer, exported once, and taken into the two renderers by one command.

| Step | Command |
|---|---|
| measure | `ktema ./run.sh --bench` |
| export and take into the site and the board | `ktema_www npm run corpus:flow` |
| take an export already written | `ktema_www npm run corpus:take` |
| serve the site and the board | `ktema_www ./run.sh` |

`export.sh` writes `export/digest`, one hash over the records, the values and the documents. The
site carries it in `pages.json`, and the board carries it in its own copy, so the center states
when the page it frames was built from another corpus. Each consumer refuses a copy that is not
the export: `demo.mjs check` for the site, and `corpus.mjs --check` for the board.

The site is the entrance and the one rendering of a page. The board lists what the site published
and forwards each entry to the page that states it, so a document's markup and style are the
site's alone and a change to either reaches a reader through one pipeline. The measurements are the
exception: a run's numbers are drawn from the records, so a measurement opens its figures on the
board.

A page carries one category, read from the document: a demonstration, a measurement, or a plan. The
site draws it as a tag beside the product and platform tags, the board's list states it, and the
board's own blackboards are the same split, so one field names one thing in both places.

What keeps the two in step is the list and the digest. The site publishes `pages.json` from the
same data its pages are built from, so a document added to the corpus is a page, a sitemap entry,
and a row in the board after one build. Both carry the export's digest, and the board states
when the site was built from another corpus.

## The observation problem

A record is one run, and a run holds many observations: a volume ladder is four, a
take is its markers, a classification is a space. Those points are not addressable
today. A payload is a list, so a projection can draw it and cannot ask for one.

The FIH tree is the answer, and it is the engine's own idea one layer up: a sparse
set of observed tuples, each addressed by the prefix of its constraint dimensions,
with a leaf that names the record and the observation inside it. A projection is a
selection over that prefix, and its cost is the walk rather than the scan.

The dimensions are declared rather than discovered: activity, subject, platform,
target, revision, and the workload's own axes, such as volume size. A dimension
added later is a new axis, and observations that predate it are absent there, which
is what an observer of a partial world can say honestly instead of inventing a
value.

The corpus is therefore two things at once. It observes, and it projects: the
observation is a record at a coordinate, and the projection is a selection of
coordinates drawn for one reader. Neither is a measurement, and both are answerable
from the volume alone.

## The first field PoC

This repository is Ktema Systems' first field PoC, and the flow is why. A customer
or a reviewer is asked to believe that an engine's cost does not follow its volume,
that a record survives a power cut, and that the artifact a team links is the
artifact that was measured. Each of those is a record with a key, a revision, and a
state, and Delta draws the set of them.

A proof of concept that only shows the engine would be a claim. One that shows the
engine, the run that measured it, and the state of that run at the revision on
screen is the product in its smallest form.

## What stays manual

Three things a machine does not produce today, and the interface each needs.

| | The interface |
|---|---|
| the footage of a take | a package records itself through `demo/_shared/run.sh` |
| the sentence a take proves | `demo/<package>/claim.txt`, authored once |
| the revision a take was made at | `demo/_shared/bundle.sh` derives it from the take's instant, and `parameters.revision_inferred` says so |

A human performs the take. Everything around it is read by the flow.

## What this does not cover

The dates of anything waiting on a board, a port, or a part, and the procurement of
the board itself. The relation that would let a cross-project analysis cite several
records, since `parent` is singular in version 0.1. The alignment of this corpus
with `ev`'s Facts and the nexus contract, which waits on all three trees.
