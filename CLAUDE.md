# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Neovim configuration based on kickstart.nvim - a starting point for Neovim that is small, single-file, and completely documented. The configuration uses Lua and the lazy.nvim plugin manager.

## Key Commands

### Formatting and Linting
- **Lua formatting**: `stylua .` - Format all Lua files using StyLua (configured in `.stylua.toml`)
- **Check formatting**: The GitHub Actions workflow runs `stylua --check .` on pull requests
- **Manual linting**: Use `:Lazy` to check plugin status and health

### Plugin Management
- **View plugin status**: `:Lazy` - Opens the lazy.nvim interface
- **Update plugins**: `:Lazy update` - Update all installed plugins
- **Install new plugins**: `:Lazy install` - Install any new plugins added to config

### LSP and Development
- **LSP server management**: `:Mason` - Manage LSP servers, formatters, and linters
- **Check health**: `:checkhealth` - Run Neovim health checks
- **Format buffer**: `<leader>f` - Format current buffer using conform.nvim

## Architecture

### Core Structure
- **`init.lua`**: Main configuration file containing all plugin specifications and setup
- **`lua/kickstart/`**: Optional modular plugins (autopairs, debug, lint, etc.)
- **`lua/custom/`**: Directory for user-specific customizations

### Plugin Management
- Uses **lazy.nvim** as the plugin manager with lazy loading
- Plugins are configured directly in `init.lua` using table specifications
- Plugin dependencies are automatically managed

### Key Components
- **LSP**: Configured via `nvim-lspconfig` with Mason for server management
- **Completion**: Uses `blink.cmp` with LuaSnip for snippets
- **Fuzzy Finding**: Telescope with fzf-native for fast searching
- **Formatting**: conform.nvim with format-on-save capability
- **Syntax Highlighting**: nvim-treesitter with auto-install
- **Colorscheme**: Material.nvim with "deep ocean" style

### File Organization
- Main config in single `init.lua` file (kickstart philosophy)
- Optional modular plugins in `lua/kickstart/plugins/`
- Custom plugins can be added to `lua/custom/plugins/`
- Plugin specifications use lazy.nvim's declarative format

### Key Features
- Leader key set to space (`<leader>` = `<space>`)
- Material "deep ocean" colorscheme
- Custom cursor behavior preventing block reversion
- LSP with auto-completion and formatting
- Git integration via gitsigns
- Telescope for fuzzy finding
- Which-key for keymap discovery

## Development Workflow

1. Make changes to configuration files
2. Run `:source %` to reload configuration or restart Neovim
3. Use `:Lazy` to check plugin status
4. Format code with `stylua .` before committing
5. Test configuration health with `:checkhealth`