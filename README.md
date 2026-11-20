# Multimedia Ordered Dictionary

An ordered dictionary built on a hand-written binary search tree in Java. Each key maps to a list of multimedia items (text, audio, image, HTML). A command-line app supports lookups, ordered traversal (`next`/`prev`), and insertion and removal.

## Design highlights
- **Leaf-sentinel BST:** only internal nodes hold data. Every empty position is a real leaf node, so insertion turns a leaf into an internal node in place and the root never needs a special case.
- **Height-bounded operations:** `get`, `put`, `remove`, `successor`, `predecessor`, `smallest` and `largest` all run in O(h) time and walk the tree directly. They never copy it into another collection.
- **Successor and predecessor of absent keys:** neighbours are found in one root-to-leaf pass, so `get` on a missing key can report the nearest keys on both sides.
- **Two-child removal:** the node takes its in-order successor's data, and the successor node is then unlinked.

## Layout
| Path | Contents |
|---|---|
| `src/` | `MultimediaItem`, `Data`, `BSTNode`, `BSTOrderedDictionary`, `Query` |
| `support/` | Stand-in versions of the media players, `StringReader`, the exceptions and the ADT interface, written so the project compiles and runs on its own. |
| `data/` | Example dictionary input (`sample-input.txt`) and the media files it refers to |
| `docs/PRD.md` | Roadmap for expanding the project |

## Run
```bash
./run.sh                       # uses data/sample-input.txt
./run.sh path/to/input.txt
```
Commands: `get k`, `add k c t`, `remove k`, `delete k t`, `next k d`, `prev k d`, `first`, `last`, `size`, `end`.

## Origin
This started as a data structures course assignment (Western University, CS 2210). Tag `v1.0-assignment` marks the submitted version.

Author: Seon Sivasathan
