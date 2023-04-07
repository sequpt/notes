# rust

Programming language

- Website: <https://www.rust-lang.org>
- Doc:     <https://www.rust-lang.org/learn>
- Source:  <https://github.com/rust-lang>

## Installation

<https://www.rust-lang.org/tools/install>

```text
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source ~/.profile
```

## Update

```text
rustup update
```

## Usage

### Cargo

```text
cargo new <path>                              # Create new cargo project at <path>
cargo init                                    # Create new cargo project in current directory
cargo init <path>                             # Same as `cargo new <path>`
cargo add <dependency>                        # Add dependency to Cargo.toml
cargo add <dependency@version>                # Add dependency with a version constraint
cargo add <dependency> --features="<feature>" # Add dependency and activate features
cargo build                                   # Build current project
cargo run                                     # Run current project
RUST_LOG=debug cargo run                      # Run current project with debug log level
```
