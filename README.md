# git-typstdiff

Lightweight tool to generate a Typst-formatted diff between two Git revisions of a `.typ` file, with insertions underlined in blue and deletions struck through in red.

## Features

* Compares any two Git revisions (tags, branches, commits) of a Typst file
* Highlights additions with `#insert[…]` (blue underline)
* Marks deletions with `#delete[…]` (red strikethrough)
* Supports a single-file workflow for simplicity
* No external dependencies beyond Python 3.6+, Git, and Typst

## Installation

Install the package from GitHub using **uv**:

```bash
uv tool install git+https://github.com/Yuan-Ru-Lin/git-typstdiff.git
```

## Usage

Run directly once installed:

```bash
git-typstdiff <rev1> <rev2> path/to/file.typ -o diff.typ
```

Then compile the resulting diff:

```bash
typst compile diff.typ
```

## Caveats

- **Limited `table` support:** This tool performs a simple line-based diff and does **not** produce proper in-table cell diffs. Tables (`#table`) will be treated as plain text and can display incorrectly if cells shift or wrap.
- **Single-file only:** Nested `#include` directives aren’t supported in this version—stick to a monolithic `.typ` file.
