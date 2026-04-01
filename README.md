# edge-toolkit docs

## mise

This repository uses [`mise`](https://mise.jdx.dev/) for tool management and task definition.

After installing `mise`, run `mise run check` to check the repository contents.

It currently exits with an error due to a bug in `harper-cli`.

## Spelling and grammar

The following Rust utilities used for spelling and grammar.

- [`typos-cli`](https://github.com/crate-ci/typos)
- [`cargo-spellcheck`](https://github.com/drahnr/cargo-spellcheck)
- [`harper-cli`](https://github.com/Automattic/harper/tree/master/harper-cli)

Configuration for `cargo-spellcheck` can be found here `.config/spellcheck.toml`.

- `cargo spellcheck check` runs both nlprules and hunspell
- `cargo spellcheck check --checkers nlprules` runs nlprules
- `cargo spellcheck check --checkers hunspell` runs hunspell

Both cargo-spellcheck and `harper-cli` are configured to use `.config/lingo.dic`
as their extra words dictionary file.
Add any false positive findings and new words to this file.
