# Rust Repository Structure Plan

## Repository Naming Convention

Following the established ecosystem pattern (`python-`, `nodejs-`, `go-`), all Rust repositories will use the `rust-` prefix.

---

## Tier 1 Repositories (High Priority)

### 1. rust-ai-client

**Source**: `vintage-game-generator/crates/vintage_ai_client`
**Crates.io Name**: `ai-client-rs`
**Lines of Code**: ~5,400

```
rust-ai-client/
├── .github/
│   ├── workflows/
│   │   ├── ci.yml
│   │   └── release.yml
│   ├── dependabot.yml
│   └── CODEOWNERS
├── .cursor/
│   └── rules/
│       └── rust.mdc
├── src/
│   ├── lib.rs
│   ├── providers/
│   │   ├── mod.rs
│   │   ├── openai.rs
│   │   ├── anthropic.rs
│   │   └── common.rs
│   ├── cache/
│   │   ├── mod.rs
│   │   ├── memory.rs
│   │   └── disk.rs
│   ├── tokens.rs
│   ├── embeddings.rs
│   └── consistency.rs
├── examples/
│   ├── basic_completion.rs
│   ├── streaming.rs
│   ├── cached_requests.rs
│   └── embeddings.rs
├── tests/
│   ├── integration_tests.rs
│   └── mock_provider.rs
├── Cargo.toml
├── README.md
├── CHANGELOG.md
└── LICENSE
```

**Features**:
```toml
[features]
default = ["openai", "cache"]
openai = ["async-openai"]
anthropic = ["anthropic"]
cache = ["sled"]
all-providers = ["openai", "anthropic"]
```

---

### 2. rust-bevy-ai

**Source**: `cosmic-cults/game-ai`
**Crates.io Name**: `bevy-ai-toolkit`
**Lines of Code**: ~4,400

```
rust-bevy-ai/
├── .github/
│   └── workflows/
│       └── ci.yml
├── src/
│   ├── lib.rs
│   ├── state_machine/
│   │   ├── mod.rs
│   │   ├── states.rs
│   │   └── transitions.rs
│   ├── behavior_tree/
│   │   ├── mod.rs
│   │   ├── nodes.rs
│   │   ├── blackboard.rs
│   │   └── builder.rs
│   ├── utility_ai/
│   │   ├── mod.rs
│   │   ├── actions.rs
│   │   └── scoring.rs
│   ├── decision/
│   │   ├── mod.rs
│   │   └── goals.rs
│   ├── targeting/
│   │   ├── mod.rs
│   │   ├── selector.rs
│   │   └── prediction.rs
│   └── prelude.rs
├── examples/
│   ├── simple_fsm.rs
│   ├── behavior_tree.rs
│   ├── utility_ai.rs
│   └── combined.rs
├── Cargo.toml
├── README.md
└── LICENSE
```

**Features**:
```toml
[features]
default = ["state-machine", "behavior-tree"]
state-machine = []
behavior-tree = []
utility-ai = []
targeting = []
full = ["state-machine", "behavior-tree", "utility-ai", "targeting"]

[dependencies]
bevy = { version = "0.16", default-features = false }
```

---

### 3. rust-bevy-combat

**Source**: `cosmic-cults/game-combat`
**Crates.io Name**: `bevy-combat`
**Lines of Code**: ~1,500

```
rust-bevy-combat/
├── src/
│   ├── lib.rs
│   ├── damage/
│   │   ├── mod.rs
│   │   ├── types.rs
│   │   └── calculation.rs
│   ├── effects/
│   │   ├── mod.rs
│   │   ├── stacking.rs
│   │   └── duration.rs
│   ├── xp/
│   │   ├── mod.rs
│   │   └── leveling.rs
│   ├── states.rs
│   └── plugin.rs
├── examples/
│   ├── basic_combat.rs
│   └── rpg_combat.rs
├── Cargo.toml
└── README.md
```

---

## Tier 2 Repositories (Medium Priority)

### 4. rust-bevy-fog-of-war

**Source**: `cosmic-cults/game-world` (fog.rs)
**Crates.io Name**: `bevy-fog-of-war`

```
rust-bevy-fog-of-war/
├── src/
│   ├── lib.rs
│   ├── visibility.rs
│   ├── rendering.rs
│   ├── exploration.rs
│   └── plugin.rs
├── assets/
│   └── shaders/
│       └── fog.wgsl
├── examples/
│   └── basic_fog.rs
├── Cargo.toml
└── README.md
```

### 5. rust-bevy-units

**Source**: `cosmic-cults/game-units`
**Crates.io Name**: `bevy-units`

```
rust-bevy-units/
├── src/
│   ├── lib.rs
│   ├── spawning.rs
│   ├── formations.rs
│   ├── selection.rs
│   ├── leadership.rs
│   └── plugin.rs
├── examples/
│   └── rts_units.rs
├── Cargo.toml
└── README.md
```

### 6. rust-game-blending

**Source**: `vintage-game-generator/crates/vintage_blending_core`
**Crates.io Name**: `game-blending`

```
rust-game-blending/
├── src/
│   ├── lib.rs
│   ├── types.rs
│   ├── graph.rs
│   ├── similarity.rs
│   └── metadata.rs
├── examples/
│   └── game_similarity.rs
├── Cargo.toml
└── README.md
```

---

## Tier 3 Repositories (Complete Applications)

### 7. rust-cosmic-dominion

**Source**: `cosmic-cults` (complete game)

```
rust-cosmic-dominion/
├── crates/
│   ├── game-core/
│   ├── game-ai/
│   ├── game-combat/
│   ├── game-world/
│   ├── game-units/
│   └── game-frontend/
├── assets/
├── client/
├── Cargo.toml
└── README.md
```

### 8. rust-vintage-rpg-generator

**Source**: `vintage-game-generator` (complete app)

```
rust-vintage-rpg-generator/
├── crates/
│   ├── ai-client/
│   ├── blending-core/
│   ├── build-tools/
│   └── generator/
├── assets/
├── Cargo.toml
└── README.md
```

---

## Standard Configuration Files

### Cargo.toml Template

```toml
[package]
name = "crate-name"
version = "0.1.0"
edition = "2021"
authors = ["Jon Bogaty <jon@jonbogaty.com>"]
license = "MIT OR Apache-2.0"
description = "Short description"
repository = "https://github.com/jbcom/rust-crate-name"
documentation = "https://docs.rs/crate-name"
readme = "README.md"
keywords = ["keyword1", "keyword2"]
categories = ["category"]

[badges]
maintenance = { status = "actively-developed" }

[dependencies]
# ...

[dev-dependencies]
# ...

[features]
default = []
```

### GitHub Actions CI Template

```yaml
name: CI

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

env:
  CARGO_TERM_COLOR: always

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: dtolnay/rust-toolchain@stable
      - uses: Swatinem/rust-cache@v2
      - run: cargo test --all-features

  clippy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: dtolnay/rust-toolchain@stable
        with:
          components: clippy
      - uses: Swatinem/rust-cache@v2
      - run: cargo clippy --all-targets --all-features -- -D warnings

  fmt:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: dtolnay/rust-toolchain@stable
        with:
          components: rustfmt
      - run: cargo fmt --all -- --check

  docs:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: dtolnay/rust-toolchain@stable
      - uses: Swatinem/rust-cache@v2
      - run: cargo doc --no-deps --all-features
        env:
          RUSTDOCFLAGS: -D warnings
```

### README Template

```markdown
# crate-name

[![Crates.io](https://img.shields.io/crates/v/crate-name.svg)](https://crates.io/crates/crate-name)
[![Documentation](https://docs.rs/crate-name/badge.svg)](https://docs.rs/crate-name)
[![CI](https://github.com/jbcom/rust-crate-name/workflows/CI/badge.svg)](https://github.com/jbcom/rust-crate-name/actions)
[![License](https://img.shields.io/crates/l/crate-name.svg)](LICENSE)

Short description of what this crate does.

## Features

- Feature 1
- Feature 2
- Feature 3

## Installation

Add to your `Cargo.toml`:

\`\`\`toml
[dependencies]
crate-name = "0.1"
\`\`\`

## Quick Start

\`\`\`rust
use crate_name::prelude::*;

fn main() {
    // Example code
}
\`\`\`

## Examples

See the [examples](examples/) directory.

## License

Licensed under either of:

- Apache License, Version 2.0 ([LICENSE-APACHE](LICENSE-APACHE) or http://www.apache.org/licenses/LICENSE-2.0)
- MIT license ([LICENSE-MIT](LICENSE-MIT) or http://opensource.org/licenses/MIT)

at your option.
```

---

## Repository Creation Commands

```bash
# Create repositories in jbcom org
gh repo create jbcom/rust-ai-client --private --description "Multi-provider AI abstraction for Rust"
gh repo create jbcom/rust-bevy-ai --private --description "AI toolkit for Bevy game engine"
gh repo create jbcom/rust-bevy-combat --private --description "Combat systems for Bevy games"
gh repo create jbcom/rust-bevy-fog-of-war --private --description "Fog of war for Bevy strategy games"
gh repo create jbcom/rust-bevy-units --private --description "Unit management for Bevy RTS games"
gh repo create jbcom/rust-game-blending --private --description "Game similarity and blending algorithms"
gh repo create jbcom/rust-cosmic-dominion --private --description "Lovecraftian 4X RTS game in Rust"
gh repo create jbcom/rust-vintage-rpg-generator --private --description "AI-powered retro RPG generator"
```

---

## Publishing Checklist

For each crate before publishing to crates.io:

1. [ ] All tests pass (`cargo test --all-features`)
2. [ ] Clippy clean (`cargo clippy -- -D warnings`)
3. [ ] Format clean (`cargo fmt -- --check`)
4. [ ] Documentation complete (`cargo doc --no-deps`)
5. [ ] README has examples
6. [ ] CHANGELOG updated
7. [ ] Version is correct
8. [ ] License files present
9. [ ] CI passing
10. [ ] `cargo publish --dry-run` succeeds
