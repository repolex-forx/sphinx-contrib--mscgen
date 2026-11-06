# Repolex Knowledge Graph of sphinx-contrib/mscgen

RDF knowledge graph data for [sphinx-contrib/mscgen](https://github.com/sphinx-contrib/mscgen), parsed by [repolex](https://repolex.ai).

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
rlex download sphinx-contrib/mscgen
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 4dfa974b8b89155649c3e737e753195ae46a8645
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 4dfa974b8b89155649c3e737e753195ae46a8645
│           └── chunk-001.nq.gz
├── blob
│   ├── 2d74c58f248790e34e482eb07e20ec6c753c9d2d.nq.gz
│   ├── 37467bdc4752a31da7763d7cf24051ab5a8a4307.nq.gz
│   ├── 38425ae4d4ee469ac9936f899bb95c83fbdbcb87.nq.gz
│   ├── 3d32872e8da8d781d528d5529b25a8094f0e486f.nq.gz
│   ├── 5b9be7ce1e07a7f33e4fc8d581da2b2b7237b063.nq.gz
│   ├── 5ff9a2af66ba65862cc41772fbfb815850aa4907.nq.gz
│   ├── 8adf48d92202dd74a7829b922b8baa7b4c99bb75.nq.gz
│   ├── 9ee0833a07f333f289e145bbbbd44d74f12573c3.nq.gz
│   ├── ae9a2295986927702683a241ff65c24cd5877f68.nq.gz
│   ├── b5a7dc29ef0f7f3593b1c61cfc5dfe8a17d3918c.nq.gz
│   ├── b824faf20e85c01ff186c0d6f179274cbc8b8f1c.nq.gz
│   ├── c1523749ff61aef4fbb79ec793512213e35f3db7.nq.gz
│   ├── f71e577883b1adf451fa6442745082cae4c481ed.nq.gz
│   └── f81eb06fb2bb9b48fd158d7778d51d97e8385dc6.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 4dfa974b8b89155649c3e737e753195ae46a8645.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 22 files
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

[sphinx-contrib/mscgen](https://github.com/sphinx-contrib/mscgen)

---
*Parsed on 2026-11-06 by [repolex](https://repolex.ai)*
