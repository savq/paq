# Paq

Paq is a Neovim package manager written in Lua.


## Features

- __Simple__: Easy to use and configure
- __Fast__:   Installs and updates packages concurrently using Neovim's event-loop
- __Small__:  Around 500 LOC


## Requirements

> **NOTE**
> Paq follows the [Neovim version available in Debian stable](https://packages.debian.org/stable/editors/neovim).
> If you are using a more recent version of neovim checkout the 'nightly' branch

- git
- [Neovim](https://github.com/neovim/neovim) ≥ 0.7


## Installation

Clone this repository.

For Unix-like systems:

```sh
git clone --depth=1 https://github.com/savq/paq-nvim.git \
    "${XDG_DATA_HOME:-$HOME/.local/share}"/nvim/site/pack/paqs/start/paq-nvim
```

For Windows (cmd.exe):

```
git clone https://github.com/savq/paq-nvim.git %LOCALAPPDATA%\nvim-data\site\pack\paqs\start\paq-nvim
```

For Windows (powershell):

```
git clone https://github.com/savq/paq-nvim.git "$env:LOCALAPPDATA\nvim-data\site\pack\paqs\start\paq-nvim"
```

To install Paq automatically or to install your plugins in `--headless` mode
see the documentation section `:h paq-bootstrapping`.


## Usage

In your init.lua, `require` the `"paq"` module with a list of packages, like:

```lua
require "paq" {
    "savq/paq-nvim", -- Let Paq manage itself

    "neovim/nvim-lspconfig",

    { "lervag/vimtex", opt = true }, -- Use braces when passing options

    { 'nvim-treesitter/nvim-treesitter', build = ':TSUpdate' },
}
```

Then, source your configuration (executing `:source $MYVIMRC`) and run `:PaqInstall`.


## Commands

- `PaqInstall`: Install all packages listed in your configuration.
- `PaqUpdate`: Update all packages already on your system (it won't implicitly install them).
- `PaqClean`: Remove all packages (in Paq's directory) that aren't listed on your configuration.
- `PaqSync`: Execute the three commands listed above.


## Options

| Option | Type     |                                                           |
|--------|----------|-----------------------------------------------------------|
| as     | string   | Name to use for the package locally                       |
| branch | string   | Branch of the repository                                  |
| build  | function | Lua function to run after install/update                  |
| build  | string   | Shell command to run after install/update                 |
| build  | string   | Prefixed with a ':' will run a vim command                |
| opt    | boolean  | Optional packages are not loaded on startup               |
| pin    | boolean  | Pinned packages are not updated                           |
| url    | string   | URL of the remote repository, useful for non-GitHub repos |

For more details on each option, refer to the
[documentation](https://github.com/savq/paq-nvim/tree/master/doc/paq-nvim.txt).


## Related projects

You can find a [comparison](https://github.com/savq/paq-nvim/wiki/Comparisons)
with other package managers in the [wiki](https://github.com/savq/paq-nvim/wiki).
