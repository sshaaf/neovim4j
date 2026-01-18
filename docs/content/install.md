---
title: "Installation"
weight: 1
bookToc: true
---

# How to Install

## Prerequisites

Before starting, ensure you have the following installed:

### Required
- [Neovim](https://neovim.io/doc/install/) v0.11+ (earlier versions may work but are untested)
- [Git](https://git-scm.com/) - for plugin management
- JDK 11 or later - [SDKMan](https://sdkman.io/install/) is recommended for Java installation
- [ripgrep (rg)](https://github.com/BurntSushi/ripgrep) - for Telescope file searching
- [fd](https://github.com/sharkdp/fd) - for Telescope extended file finding capabilities
- A [Nerd Font](https://www.nerdfonts.com/) installed and configured in your terminal

## First Time Setup

1. Clone this configuration to your Neovim config directory:
```bash
git clone <your-repo-url> ~/.config/nvim
```

2. Open Neovim for the first time:
```bash
nvim
```

3. Lazy.nvim will automatically:
   - Install all plugins
   - Install the Java language server (jdtls) via Mason
   
   Wait for all installations to complete (you'll see progress notifications).

4. Verify installation by running:
```vim
:checkhealth
```

All checks should pass except for optional warnings (which can be ignored).
