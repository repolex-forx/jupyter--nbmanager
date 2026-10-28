# Repolex Knowledge Graph of jupyter/nbmanager

RDF knowledge graph data for [jupyter/nbmanager](https://github.com/jupyter/nbmanager), parsed by [repolex](https://repolex.ai).

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
rlex download jupyter/nbmanager
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── dd26a71c0b625773dab582d47d713d574f2af84b
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── dd26a71c0b625773dab582d47d713d574f2af84b
│           └── chunk-001.nq.gz
├── blob
│   ├── 22364b27aa70fff1fc4f4004a0162c9bcaaa331d.nq.gz
│   ├── 2c61e28b3f2d0e1311b4d1f50cdc7d19b6ab0c9e.nq.gz
│   ├── 3af6f424f900d1b961f07b7777c1d7ea30ce9d40.nq.gz
│   ├── 405bcf84b89c4316681b32da5b5e95202f492d8a.nq.gz
│   ├── 4a3463e16fd838ac969b753b26c7251fe4bedd79.nq.gz
│   ├── 4a6cf6a037cec8e7ba7ce330d85ef47bf10252df.nq.gz
│   ├── 4dd6cbce03def095b3c41434a3d722390a8eec92.nq.gz
│   ├── 52c63cfebbce095888e63bf9a83203849e1c14e3.nq.gz
│   ├── 54d91ca6761fa37fa379350796c6ef5cd41269b9.nq.gz
│   ├── 585d57ad5ade4a4f5c0b4a7b554a9536d7f5e49c.nq.gz
│   ├── 67815fe451b618e5301d9ab35960a472f5f11ab0.nq.gz
│   ├── 761b1ac2c19a541e984e77262e96e2b4c6281f85.nq.gz
│   ├── 784c100d48cf364df3bc5deec77300b018328587.nq.gz
│   ├── 84909f27d8c206ca690a9a81dedf0e7bf272c437.nq.gz
│   ├── 850929d96fe262a08d2c780a2dbce412d3849134.nq.gz
│   ├── 91af0e12c3bd2ee2d5e883def89cc8c09afb939c.nq.gz
│   ├── 97923f442924d1a1f9516d6abb4d2c95ffaeb089.nq.gz
│   ├── 99993fe649e18906ca95147aabfb5e7e5d9253ce.nq.gz
│   ├── a4dabd06a75cfae44cfa3dd2604515c01fd732cf.nq.gz
│   ├── b3451fc4b583871164c2566ef1269cfa503f0a69.nq.gz
│   ├── b96ed5d17dc8cb1be220d3d3871a3a5ab83a0e50.nq.gz
│   ├── c68433b8be69ed3230070522fbc82366663b0c42.nq.gz
│   ├── c9b55f98d8dc788dc93bd019caf18a1a9afbe4b7.nq.gz
│   ├── d5d2286de6954741068cae71ac47961bb4e0c92a.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── ea7e010964601e84da57dee4f3c5bb5c39156b0c.nq.gz
│   ├── ed75207384f09a872a45560894987106d19b9642.nq.gz
│   └── f33f039f0e6e0122c81769fdef8e8ed29859f2b5.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── dd26a71c0b625773dab582d47d713d574f2af84b.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 36 files
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

[jupyter/nbmanager](https://github.com/jupyter/nbmanager)

---
*Parsed on 2026-10-28 by [repolex](https://repolex.ai)*
