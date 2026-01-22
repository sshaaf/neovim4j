---
title: "Rust Development Guide"
weight: 6
bookToc: true
---

# Rust Development Guide

This guide covers Rust-specific features and workflows in this Neovim configuration.

## Overview

The Rust setup is based on [LazyVim's Rust extras](https://www.lazyvim.org/extras/lang/rust) and includes:

- **rustaceanvim** - Advanced Rust language support
- **crates.nvim** - Cargo.toml dependency management
- **rust-analyzer** - Powerful LSP for Rust
- **codelldb** - Debugger for Rust applications
- **neotest** - Test runner integration

## Getting Started with Rust

### Prerequisites

Make sure you have Rust installed:

```bash
# Install Rust via rustup
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

# Verify installation
rustc --version
cargo --version
```

### Creating a New Rust Project

```bash
# Create a new binary project
cargo new my-project
cd my-project

# Or create a library
cargo new --lib my-library
```

Then open the project in Neovim:

```bash
nvim .
```

## Rust-Specific Features

### rust-analyzer LSP

rust-analyzer provides advanced IDE features:

- **All cargo features enabled** - Full project analysis
- **Build scripts support** - Understands build.rs files
- **Clippy integration** - Linting on save
- **Procedural macros** - Expanded and analyzed
- **Smart file watching** - Excludes common directories (.git, target, etc.)

### Code Actions

Press `<Space>cR` to access Rust-specific code actions:

- Add missing derive traits
- Fill match arms
- Import items
- Generate documentation
- Convert to guarded return
- Inline variable/function
- And many more!

### Debuggables

Press `<Space>dr` to open the debuggables menu, which shows:

- **Binaries** - Main executables in your project
- **Tests** - Individual test functions
- **Examples** - Example programs

Select one to start debugging immediately with codelldb.

### Cargo.toml Support

When editing `Cargo.toml` files, **crates.nvim** provides:

#### Dependency Completion
Start typing a crate name under `[dependencies]`:

```toml
[dependencies]
serde = # <-- Completion will suggest latest version
```

#### Inline Documentation
Hover over a dependency to see:
- Crate description
- Latest version
- Documentation link
- Repository link

#### Version Checking
Get inline diagnostics for:
- Outdated dependencies
- Incompatible versions
- Available updates

### Running Tests

Rust tests integrate with neotest via the rustaceanvim adapter:

```bash
# Run all tests
:!cargo test

# Run specific test
:!cargo test test_name

# Run tests in a specific module
:!cargo test module_name
```

You can also use the debuggables menu (`<Space>dr`) to run/debug individual tests.

## Common Workflows

### Adding a Dependency

1. Open `Cargo.toml`
2. Navigate to `[dependencies]` section
3. Start typing the crate name
4. Use completion (`<C-Space>`) to select
5. Save the file
6. Run `:!cargo build` to download

### Implementing a Trait

1. Place cursor on type that needs trait
2. Press `<Space>cR` for code actions
3. Select "Implement missing members"
4. Stubs will be generated automatically

### Running and Debugging

1. Press `<Space>dr` to open debuggables
2. Select your binary or test
3. Debugger starts with breakpoints active
4. Use standard debug keybindings:
   - `<Space>dc` - Continue
   - `<Space>dn` - Step over
   - `<Space>di` - Step into
   - `<Space>do` - Step out

### Exploring Documentation

1. Place cursor on any item (function, type, etc.)
2. Press `K` to show inline documentation
3. Press `gd` to jump to definition
4. Press `gr` to find all references

### Refactoring

1. Place cursor on symbol to rename
2. Press `<Space>rn`
3. Type new name
4. Press Enter
5. All references update across the project

## Rust-Specific Settings

The rust-analyzer is configured with:

```lua
cargo = {
  allFeatures = true,           -- Enable all features
  buildScripts = { enable = true }, -- Support build.rs
}
checkOnSave = {
  command = 'clippy',           -- Use clippy for linting
  extraArgs = { '--no-deps' },  -- Only check your code
}
procMacro = {
  enable = true,                -- Expand procedural macros
}
```

These settings provide comprehensive project analysis while keeping performance optimal.

## Tips and Tricks

### Quick Build

Set up a keybinding to build quickly:

```vim
:!cargo build
```

Or run it in the background with ToggleTerm.

### Clippy Linting

Get instant feedback from clippy:

```bash
# Manual run
:!cargo clippy

# Or it runs automatically on save via LSP
```

### Format on Save

rust-analyzer automatically formats code using `rustfmt` when you save.

### Expand Macros

Use `<Space>cR` and select "Expand macro recursively" to see what procedural macros generate.

### View Cargo Tree

Check your dependency tree:

```bash
:!cargo tree
```

## Troubleshooting

### rust-analyzer Not Working

1. Check it's installed: `:Mason` and verify rust_analyzer is installed
2. Check LSP status: `:LspInfo`
3. Restart LSP: `<Space>rs`
4. Full restart: Close Neovim and reopen

### Slow Performance

If rust-analyzer is slow on large projects:

1. Disable some features in your settings
2. Use `cargo check` instead of `cargo build`
3. Add workspace folders to exclude in settings

### Debugging Not Starting

1. Verify codelldb is installed: `:Mason`
2. Check DAP configuration: `:lua print(vim.inspect(require('dap').configurations.rust))`
3. Make sure you're running debug build (not release)

## Resources

- [Rust Book](https://doc.rust-lang.org/book/) - Official Rust guide
- [Rust by Example](https://doc.rust-lang.org/rust-by-example/) - Learn by examples
- [rust-analyzer Manual](https://rust-analyzer.github.io/manual.html) - LSP documentation
- [rustaceanvim Docs](https://github.com/mrcjkb/rustaceanvim) - Plugin documentation
- [crates.nvim Docs](https://github.com/saecki/crates.nvim) - Cargo.toml helper docs

---

For general keybindings, see [Quick Reference]({{< relref "/quick-reference" >}})
