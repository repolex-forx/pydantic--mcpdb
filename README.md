# Repolex Knowledge Graph of pydantic/mcpdb

RDF knowledge graph data for [pydantic/mcpdb](https://github.com/pydantic/mcpdb), parsed by [repolex](https://repolex.ai).

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
rlex download pydantic/mcpdb
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 6c9f90937217be9a5a0cc246c920c7ce01a220db
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 6c9f90937217be9a5a0cc246c920c7ce01a220db
│           └── chunk-001.nq.gz
├── blob
│   ├── 0140d3378c555550251ef588a8b8f1d633b43b19.nq.gz
│   ├── 17ef01415192d0bb8653548e759f4d16892cdf9f.nq.gz
│   ├── 47e420281fdd545d63da2dad20a6ec94e83b5844.nq.gz
│   ├── 488c6260c10f2e88fa1fae58a63fccec8d600cd1.nq.gz
│   ├── 72126650a4d6d711ee35a14ffa6451579641b740.nq.gz
│   ├── 8bc483289061d79a1011110223f99f03b3aee684.nq.gz
│   ├── f01884a7d2cac1fbeeaba50889384fff2c17e66e.nq.gz
│   ├── f65150ee83cc1b3e5368b21bfe6ccfd998c6d8c7.nq.gz
│   └── f8f3e0fd8c031219f968a6cc736f86aadbfd161f.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 6c9f90937217be9a5a0cc246c920c7ce01a220db.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 16 files
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

[pydantic/mcpdb](https://github.com/pydantic/mcpdb)

---
*Parsed on 2026-10-11 by [repolex](https://repolex.ai)*
