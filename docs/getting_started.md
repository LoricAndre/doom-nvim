# Getting Started

## Install

This is what you will have installed by the end of this section:

- Git 2.23+
- Neovim 0.5.0+ (Neovim 0.4.x not supported, see [faq](./faq.md#why-does-doom-nvim-only-support-neovim-05) to know why)
- GNU Find
- **Optional**: ripgrep 11.0+
- **Optional**: fd 7.3.0+ (known as `fd-find` on Debian, Ubuntu & derivates),
  improves performance for many file indexing commands
- **Optional**: node & npm, required to use LanguageServerProtocols (LSP) and the plugins using LSP, like the symbols-outline plugin.

These packages ought to be available through the package managers of your OS;
i.e. pacman/aptitude/rpm/etc on the various Linux distributions.

### Neovim & dependencies

#### On Linux

Neovim 0.5.0 was recently released as a stable version.
You can check what version your repository has by looking at [this site.](https://repology.org/project/neovim/versions)
If Neovim 0.5.0 is still not available in your repository, you can install it by doing one of the following:

1. Using the Doom Nvim install script to download a Neovim Nightly AppImage from releases
   (see how by executing the installer with <kbd>bash -s -- -h</kbd>).

2. Using extra repositories according to your distribution (PPA/COPR/AUR/etc).

3. Using a Neovim version manager like [nvenv](https://github.com/NTBBloodbath/nvenv).

##### Ubuntu

You can get nightly builds of git master from the
[Neovim Unstable PPA](https://launchpad.net/~neovim-ppa/+archive/ubuntu/unstable).

```sh
add-apt-repository ppa:neovim-ppa/unstable
apt-get update
```

##### Fedora

Nightly builds can be installed by using the
[agriffis/neovim-nightly](https://copr.fedorainfracloud.org/coprs/agriffis/neovim-nightly/)
COPR repository.

```sh
dnf copr enable agriffis/neovim-nightly
dnf update
```

##### Arch

Neovim Nightly builds can be installed using the PKGBUILD
[`neovim-nightly-bin`](https://aur.archlinux.org/packages/neovim-nightly-bin),
available on the [AUR](https://wiki.archlinux.org/index.php/Arch_User_Repository).

#### On MacOS

You can download a prebuilt binary from the [Neovim](https://github.com/neovim/neovim/releases/tag/nightly) releases page.

1. Download: `curl -LO https://github.com/neovim/neovim/releases/download/v0.5.0/nvim-macos.tar.gz`
2. Extract: `tar xzvf nvim-macos.tar.gz`
3. Run: `./nvim-osx64/bin/nvim`

You may wish to add it to your PATH using something like:
`export PATH="$HOME/nvim-osx64/bin:$PATH"`

Neovim nightly can also be downloaded with [homebrew](https://brew.sh/):

`brew install --HEAD neovim` will download the source and build it locally on your machine.

If you already have Neovim v0.4 installed you may need to unlink it.

```
brew unlink neovim
brew install neovim --HEAD
nvim --version
```

MacPorts currently only has Neovim v0.4.4



#### On Windows

##### [Chocolatey](https://community.chocolatey.org/)

```
choco install neovim --pre
```

##### [Scoop](https://scoop.sh/)

```
scoop bucket add versions
scoop install neovim-nightly
```

##### Manual

You can also download a prebuilt binary from the [Neovim](https://github.com/neovim/neovim/releases) releases page.

### External dependencies

#### On Linux

##### Ubuntu

```sh
# Required dependencies
apt-get install git ripgrep

# (Optional) Improves performance for many file indexing commands
apt-get install fd-find

# (Optional) Required by some Language Server Protocols
apt-get install nodejs npm
```

##### Fedora

```sh
# Required dependencies
dnf install git ripgrep

# (Optional) Improves performance for many file indexing commands
dnf install fd-find # is 'fd' in Fedora <28

# (Optional) Required by some Language Server Protocols
dnf install nodejs
```

##### Arch

```sh
# Required dependencies
pacman -S git ripgrep

# (Optional) Improves performance for many file indexing commands
pacman -S fd

# (Optional) Required by some Language Server Protocols
pacman -S nodejs npm
```

#### On MacOS

Dependencies can be installed using [homebrew](https://brew.sh/) 

```sh
# Required dependencies
# git is already installed as part of MacOS
brew install ripgrep ctags

# (Optional) Required by Language Server Protocols
brew install node

```

#### On Windows

If you use Windows, please help by posting the steps to install the external
dependencies here!

### Doom Nvim

With Neovim v0.5.0 and Doom's dependencies installed, next is to install
Doom Nvim itself:

> **NOTES:**
>
> 1. If you have not installed Neovim 0.5.0 yet, please run the following command
>    before installing Doom Nvim, it will install Neovim 0.5.0 and Doom Nvim.
> 2. If you want to know all the commands of the installer, run the installer with
>    <kbd>bash -s -- -h</kbd> instead of just <kbd>bash</kbd>.

```sh
# Check if you have all the dependencies listed above
curl -sLf https://raw.githubusercontent.com/NTBBloodbath/doom-nvim/main/install.sh | bash -s -- -c
```

```sh
# If you do not have Neovim 0.5.0 but you have all the dependencies listed above
curl -sLf https://raw.githubusercontent.com/NTBBloodbath/doom-nvim/main/install.sh | bash -s -- -n
```

```sh
# If you already have Neovim 0.5.0 and all the dependencies listed above
curl -sLf https://raw.githubusercontent.com/NTBBloodbath/doom-nvim/main/install.sh | bash
```

The installation script will set up everything for you and will work you through
the first-time setup of Doom Nvim.

#### Using cheovim

If you're using cheovim as your Neovim configurations manager you can use the
recipe listed in cheovim documentation:

```lua
doom_nvim = { "~/.config/doom-nvim", {
        plugins = "packer",
        preconfigure = "doom-nvim"
    }
}
```

## Update & Rollback

### Update Doom Nvim

To update Doom Nvim, you have two options, run `:DoomUpdate` inside Neovim or
run the installation script with <kbd>bash -s -- -u</kbd>.

### Rollback

#### Previous Configurations

To uninstall Doom Nvim and go back to your previous setup, simply run the
installation script with <kbd>bash -s -- -x</kbd>. It will uninstall Doom Nvim
and restore the backup of your previous setup.

#### Rolling Back Doom

Did the update screwed up your setup because of a bug or a breaking change and you want to rollback?
Then you're lucky. Just run `:DoomRollback` in Neovim and Doom will rollback itself to
a previous release (for main branch) or a previous commit (for development branch).

> **IMPORTANT**: remember to report the issues before just rolling back. In that
> way we can work on fixing them and make doom better!

## Configuration

You can configure Doom Nvim by tweaking the `doomrc.lua`, `doom_config.lua` and
the `plugins.lua` files located in your Doom Nvim root directory
(`$HOME/.config/doom-nvim/` by default).

### doomrc.lua

This file handles all the Doom Nvim modules, its structure is really simple and
easy to understand.

This one will look like that:

```lua
local doom = {
	ui = {
		'dashboard',      -- Start screen
		-- 'doom-themes', -- Additional doom emacs' colorschemes
		'statusline',     -- Statusline
		'tabline',        -- Tabline, shows your buffers list at top
		-- 'zen',         -- Distraction free environment
		'which-key',      -- Keybindings popup menu like Emacs' guide-key
		-- 'indentlines', -- Show indent lines
	},
	doom = {
		-- 'neorg',    -- Life Organization Tool
		-- 'runner',   -- Open a REPL for the current language or run the current file
		-- 'compiler', -- Compile (and run) your code with just pressing three keys!
	},
	editor = {
		'auto-session',    -- A small automated session manager for Neovim
		-- 'terminal',     -- Terminal for Neovim (NOTE: needed for runner and compiler)
		'explorer',        -- Tree explorer
		'symbols',         -- LSP symbols and tags
		-- 'minimap',      -- Code minimap, requires github.com/wfxr/code-minimap
		'gitsigns',        -- Git signs
		'telescope',       -- Highly extendable fuzzy finderover lists
		-- 'restclient',   -- A fast Neovim http client
		'formatter',       -- File formatting
		'autopairs',       -- Autopairs
		-- 'editorconfig', -- EditorConfig support for Neovim
		'kommentary',      -- Comments plugin
		'lsp',             -- Language Server Protocols
		'snippets',        -- LSP snippets
	},
	langs = {
		-- To enable the language server for a language justadd the +lsp flag
		-- at the end, e.g. 'rust +lsp'. This will install the rust TreeSitter
		-- parser and rust-analyzer
		--
		-- 'html',        -- HTML support
		-- 'css',         -- CSS support
		-- 'javascript',  -- JavaScript support
		-- 'typescript',  -- TypeScript support
		-- 'bash',        -- The terminal gods language
		-- 'python +lsp', -- Python support + lsp
		-- 'ruby',        -- Look ma, I love the gems!
		'lua',            -- Support for our gods language
		-- 'elixir',      -- Build scalable and maintainablesoftware
		-- 'haskell',     -- Because Functional programming is fun, isn't it?

		-- 'rust +lsp',   -- Let's get rusty!
		-- 'go',          -- Hello, gopher
		-- 'cpp',         -- C++ support
		-- 'java',        -- Java support

		-- 'config',      -- Configuration files (JSON, YAML, TOML)
		-- 'dockerfile',  -- Do you like containers, right?
	},
	utilities = {
		-- 'suda',            -- Write and read files without sudo permissions
		-- 'lazygit',         -- LazyGit integration for Neovim, requires LazyGit
		-- 'neogit',          -- Magit for Neovim
		-- 'colorizer',       -- Fastets colorizer for Neovim
		'range-highlight',    -- hightlights ranges you haveentered in commandline
	},
}

return doom
```

And as the `doomrc.lua` file self-documentation says, you will only need to uncomment
or comment the plugins names in order to enable or disable them. e.g. to enable the `terminal`
plugin you will only need to uncomment the `-- 'terminal',` line and restart Neovim.
Doom will automatically handle your changes and install the `terminal` plugin for you.

> **NOTE**: for more information please refer to [modules].

### doom_config.lua

This file handles all the Doom Nvim configurations, including the ability to easily
create new custom mappings and global Neovim variables.

All the options are self-documented on it so you can easily modify them and know
exactly what you are doing.

This is its structure:

```lua
local doom = {
    -- Here lies all the Doom Nvim configurations
}

local nvim = {
    -- Here lies all the custom Neovim configurations
}

return {
    doom = doom,
    nvim = nvim,
}
```

### plugins.lua

This file handles your custom plugins, in other words, it handles all the extra
plugins you need that are not covered by Doom Nvim.

If you are familiar with [packer.nvim] then you can see this file as a wrapper
for its `use` function.

This one just contains a `return {}` statement. Your plugins should be declared
inside the returned table, e.g. if you want to install `markdown-preview.nvim`:

```lua
return {
    {
        'iamcco/markdown-preview.nvim',
        run = 'cd app && yarn install',
        event = 'BufRead',
    },
}
```

And as with the `doomrc.lua` file, Doom Nvim will automatically handle your changes
and install or uninstall the plugins declared on here.

> **NOTE**: all the valid options for declaring plugins can be found in
> [specifying plugins](https://github.com/wbthomason/packer.nvim#specifying-plugins).

### Modules

Doom Nvim consists of around 5 modules. A Doom Nvim Module is a bundle of plugins,
configuration and commands, organized into a unit that can be toggled easily by
tweaking your `doomrc.lua` (found in `$HOME/.config/doom-nvim`).

Please see [Plugin Management](#plugin-management) for more information.

### Plugin Management

Doom Nvim uses a declarative and use-package inspired package manager called
[packer.nvim](https://github.com/wbthomason/packer.nvim).

Modules and plugins are declared in `lua/doom/modules/init.lua` file, located
in your Doom Nvim root directory. Read on to learn how to use this system to install
your own plugins.

> **WARNING:** Do not install plugins directly in `lua/doom/modules/init.lua`. Instead,
> use your `doomrc.lua` and `plugins.lua` files to modify them.

### Configuring Doom

#### Configuring settings

You can change Doom's default settings by tweaking your `doom_config.lua` file,
please see <kbd>:h doom_nvim_options</kbd> to know how to.

#### Configuring plugins

Do you want to change some configurations of some modules?

Go to `lua/doom/modules/config` directory and you will find the configurations
for the plugins.

Otherwise if you want to configure a plugin declared in your `plugins.lua` you
can use the packer's `config` field, e.g.

```lua
{
    'TimUntersberger/neogit',
    config = function()
        require('neogit').setup()
    end,
}
```

##### Configuring LSP

[Language Server Protocols](https://microsoft.github.io/language-server-protocol/) is installed as a plugin.

To easily install language servers and without having to do it system-wide or having to
manually configure servers, Doom Nvim makes use of [kabouzeid/nvim-lspinstall](https://github.com/kabouzeid/nvim-lspinstall).

To enable the language server for a certain programming language and automatically
install it, just append a `+lsp` flag at the end of the language field in your `doomrc.lua`,
e.g. for enabling Rust support in Doom and install `rust-analyzer`:

```lua
local doom = {
    langs = {
        'rust +lsp', -- Let's get rusty!
    }
}
```

> **NOTE**: You can see a list of currently supported languages at [bundled installers](https://github.com/kabouzeid/nvim-lspinstall#bundled-installers).

### Binding keys

You can modify the default keybindings by modifying the following files:

- `lua/doom/core/keybindings/init.lua` - General and SPC keybindings
- `lua/doom/modules/config` - lua plugins keybindings

You can also define your own keybindings in your `doom_config.lua` with the `nvim.mappings` field.

## Migrating to 3.0.0

As this is a major version, there are many improvements and breaking changes.
This section is made to help you migrate to this version without dying in the
attempt.

But first let's see what's new:

### Changes for end users

- Raw speed, never go slow again.
  Reduced average startuptime from 400ms to 40ms (tested with old hardware),
  special thanks to [vhyrro]!
- New and better doom-one colorscheme written in pure Lua. Because the
  colorscheme matters.
- Fragmented configuration file (`doomrc`) so it will be more easy to customize
  Doom. See [New configurations](#new-configurations).
- Easily add new Neovim settings by using your `doom_config.lua` file.
  Extensibility is a feature that you cannot miss, and what better than being
  able to extend Doom as much as you want?
- New logging system powered by [vlog]. A faster and smaller logging system
  because complexity is not always the best choice.
- Easily enable and disable plugins. Now toggling the doom default plugins is easier
  than before, just comment or uncomment it in your `doomrc.lua`!
- Better custom plugins management. Now the custom plugins are being directly
  handled by packer as it should be, no more nonsense wrappers around it.
- Better updating mechanism. Forget these annoying merging issues and save the
  current state of your Doom Nvim installation in case that you need to rollback
  your Doom Nvim version because of the demons!
- Added a `DoomRollback` command. Something went wrong after updating? No worries,
  just rollback to a previous version (stable branch) or a previous commit
  (development branch) and be piece of mind!
- Built-in plugins. Because we should have some utilities to make our lives
  easier, isn't this how it should be? See [modules/doom] for more information.
- A lot of bug fixes.

### Changes for contributors

- Better documentation. Added docs for each doom lua module because
  documentation is the core of all projects.
- Restructured source code. Now the doom nvim source code is much cleaner and
  easier to understand.
- Added selene linter CI for incoming pull requests and stylua CI for pushes.
  Let's get a consistent way to maintain Doom Nvim source!

Now that we know what's new we will surely want to update, isn't it?

Due to the new raw speed we highly recommend that you do a fresh installation so
everything will be work as it should. **Make sure to backup your doomrc changes
so you can apply your changes to the new `doom_config.lua` configuration file**.

We don't recommend using the `:DoomUpdate` command for this task because of the
huge changes that doom nvim gotten. This command will only end in a really
bad status for this release due to git merging issues.

With that being said, you can run the following command snippet:

> **IMPORTANT:**
>
> 1. Make sure to read everything it does before executing it.
>
> 2. If you are using cheovim just remove and clone the doom-nvim repository again.

```sh
cp $HOME/.config/doom-nvim/doomrc $HOME/.config/doomrc.bak \
    && rm -rf $HOME/.config/doom-nvim $HOME/.local/share/nvim/site/pack/packer \
    && unlink $HOME/.config/nvim \
    && curl -sLf https://raw.githubusercontent.com/NTBBloodbath/doom-nvim/main/install.sh | bash -s -- -d
```

This snippet will do the following tasks for you:

1. Create a copy of your doomrc so you can use a diff tool later with the
   actual breaking changes to doomrc structure.
2. Remove the doom-nvim configuration directory and all plugins (including packer).
3. Remove the residual symlink that doom-nvim have created before during the
   installation (**omit that step if you're using cheovim**).
4. Clone doom-nvim source to where it belongs again by using the installer
   (installing the development branch because this version is not released yet).

Then you'll only need to start Neovim and start using it as usual!

#### New configurations

Since version 3.0.0 the doomrc has been fragmented into some files, but why?

This was done to benefit both contributors and end users as follows:

- Improve understanding. One file that handles everything doesn't seem like a
  good thing on a large scale.
- Easier to maintain. Divided by function, the new files make the code more
  readable and easy to modify.

And now, how can I start using the new configuration files?

I'm going to explain you in a short way because the new configuration files has
a rich documentation inside them.

- `doomrc.lua`, this file handles the Doom Nvim modules, in other words, which
  plugins are being installed and loaded and which plugins are not.
- `doom_config.lua`, this file handles the user configurations for doom nvim,
  e.g. if mouse is enabled or not. This one also handles user-defined Neovim
  configurations like global variables and mappings.
- `plugins.lua`, this file handles the user-defined plugins, it is the
  replacement for the `custom_plugins` field in the old doomrc.

> Are you having issues with the 3.0.0 version? Don't hesitate to [report them]
> so we can fix them and make doom more stable because that's the way to improve software.

[vlog]: https://github.com/tjdevries/vlog.nvim
[packer.nvim]: https://github.com/wbthomason/packer.nvim
[vhyrro]: https://github.com/vhyrro
[modules]: ./modules.md
[modules/doom]: https://github.com/NTBBloodbath/doom-nvim/tree/develop/lua/doom/modules/doom
[report them]: https://github.com/NTBBloodbath/doom-nvim/issues/new
