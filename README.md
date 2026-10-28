# Repolex Knowledge Graph of explosion/prodigy-lunr

RDF knowledge graph data for [explosion/prodigy-lunr](https://github.com/explosion/prodigy-lunr), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download explosion/prodigy-lunr
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── d5bcb91d5bf0b4de5e381d64782b45e9aaff965b
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── d5bcb91d5bf0b4de5e381d64782b45e9aaff965b
│           └── chunk-001.nq.gz
├── blob
│   ├── 03ec3c1e3770ea0de1cd44f547f6bef5e761b120.nq.gz
│   ├── 2f141c115ddc6ac05b35e183d45ba5039d3d283f.nq.gz
│   ├── 5ed8c6f4568a1f94f496142140870a219dfe73c2.nq.gz
│   ├── 62e3ec1c11fe9386591b5a45847b78b41a3612a6.nq.gz
│   ├── 6589b30b436ad4a79f275f44864a7b23be4fcb88.nq.gz
│   ├── 6b117db5b442e2f0acbdca62f2ab47d7dcc69a0b.nq.gz
│   ├── 6dbd43fbd7f530f3f0c554c63605be7e3d220485.nq.gz
│   ├── 8902e65b1416db7bcc43a9a6ea656998d0b368c5.nq.gz
│   ├── 91167cd9cc235e2625eb55c89408a1568324c4ed.nq.gz
│   ├── 992361b341ded499e60b9e07beebf864bc7c1a84.nq.gz
│   ├── 9c2926ee0a1f5ce0b1d521a9cfe2e53e885833f1.nq.gz
│   ├── 9fdec95f74f17f641d77fbb88dd55eea3a387ed4.nq.gz
│   ├── a6d5e3f118d970d21287fef6dd327c8c50b787b8.nq.gz
│   ├── aefb2e0a1d7d9c6e87c6b8517c46cabce5e01daf.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   └── f98a3831327e9986d0ad8099152d7b7c5d454f74.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── d5bcb91d5bf0b4de5e381d64782b45e9aaff965b.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 23 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[explosion/prodigy-lunr](https://github.com/explosion/prodigy-lunr)

---
*Parsed on 2026-10-28 by [repolex](https://repolex.ai)*
