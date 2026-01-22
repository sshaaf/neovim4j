---
title: "Personal Neovim Setup"
type: docs
---

# My Personal Neovim Configuration
{{< button relref="/getting-started" >}}Get Started{{< /button >}}
{{< button href="https://github.com/sshaaf/neovim" >}}View on GitHub{{< /button >}}

This is my personal Neovim configuration optimized for **Java and Rust development**. It prioritizes speed, simplicity, and a superior terminal experience. You get the latest LSP, built-in debugging, testing support, and self-hosted AI assistance (via Ollama) pre-configured out of the box. No distractions and no unnecessary bloat—it simply works.

Feel free to use this as a reference or starting point for your own Neovim setup!

> A streamlined Neovim configuration optimized for Java and Rust development.

## Quick Install

```bash
# Clone as your Neovim configuration
git clone https://github.com/sshaaf/neovim.git ~/.config/nvim

# Start Neovim
nvim
```

Lazy.nvim will automatically install all plugins on first launch.

See [Installation Guide]({{< relref "/install" >}}) for detailed instructions.

## What's Included

**Language Support:**
- **Java** - jdtls LSP, debugging (DAP), testing support
- **Rust** - rust-analyzer via rustaceanvim, crates.nvim for Cargo.toml, codelldb debugger, neotest integration

**Core Features:**
- Full LSP integration with intelligent code completion
- Debug Adapter Protocol (DAP) for debugging
- nvim-cmp for intelligent completion
- Treesitter for advanced syntax highlighting
- Telescope for fuzzy finding
- nvim-tree for file exploration
- CodeCompanion.nvim for self-hosted AI assistance (Ollama)
- Test runners integrated with neotest

**Additional Support:**
- XML, JSON, TOML, RON (for configs)
- Markdown (for documentation)
- Lua (for Neovim config)

## Documentation

- [Getting Started]({{< relref "/getting-started" >}}) - Choose your learning path
- [Interactive Tutorial]({{< relref "/tutorial" >}}) - 10 hands-on Java lessons
- [Rust Development Guide]({{< relref "/rust-guide" >}}) - Rust-specific features and workflows
- [Installation Guide]({{< relref "/install" >}}) - Detailed setup instructions
- [Quick Reference]({{< relref "/quick-reference" >}}) - Keybinding reference


---
## Built With ❤️ for the Java and Rust communities.

This is my personal configuration, shared as a reference for others. Feel free to fork and customize it for your needs!

GitHub [repository](https://github.com/sshaaf/neovim)
