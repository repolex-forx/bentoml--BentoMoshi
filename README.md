# Repolex Knowledge Graph of bentoml/BentoMoshi

RDF knowledge graph data for [bentoml/BentoMoshi](https://github.com/bentoml/BentoMoshi), parsed by [repolex](https://repolex.ai).

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
rlex download bentoml/BentoMoshi
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 1e7c91fb81f3b8086c81c341147e886c4ef174a1
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 1e7c91fb81f3b8086c81c341147e886c4ef174a1
│           └── chunk-001.nq.gz
├── blob
│   ├── 231bcb00f2e3fc427b6e701bc421da36c597a0f9.nq.gz
│   ├── 2c0733315e415bfb5e5b353f9996ecd964d395b2.nq.gz
│   ├── 38d3016770909763d0f0191db9ff73349bfcc7ad.nq.gz
│   ├── 57861841ae23acd4c7ae08243de36c992ce94488.nq.gz
│   ├── 7134f8cefc6f4204697b22c9a3f0dd49fce362da.nq.gz
│   ├── 815f7427d52f9c032091ce5814de3597257aba06.nq.gz
│   ├── b12a76c932e370385b2e775dfabc5b053ff190af.nq.gz
│   ├── b83bc5fdc1bab07b8e3f23c3d4301ef1ef62ab37.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── e8b3624b9dfe4904abfe95cfd404a1238eab1285.nq.gz
│   └── fb06e1eae0ba02124673b6233d580f5e01985c90.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 1e7c91fb81f3b8086c81c341147e886c4ef174a1.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 18 files
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

[bentoml/BentoMoshi](https://github.com/bentoml/BentoMoshi)

---
*Parsed on 2026-11-08 by [repolex](https://repolex.ai)*
