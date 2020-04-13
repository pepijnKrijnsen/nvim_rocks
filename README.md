# nvim_rocks 🤘

Install [luarock](https://luarocks.org/) packages for Neovim's built in Lua interpreter.

## Installation

We use [hererock](https://github.com/luarocks/hererocks) to set up a luajit local enviroment.

```vim
    Plug 'theHamsta/nvim_rocks', {'do': 'pip3 install --user hererocks && hererocks . -j2.1.0-beta3 -r3.0.0'}
```

I am currently using the latest nightly of Neovim.

## Usage

```lua
local nvim_rocks = require'nvim_rocks'

print(vim.inspect(nvim_rocks))

print(vim.inspect(nvim_rocks.list()))

-- Force installation of rock
nvim_rocks.ensure_installed('30log')

-- Ensure that certain rocks are installed
nvim_rocks.ensure_installed('lua-cjson')
nvim_rocks.ensure_installed({'lua-cjson', 'stdlib'})
nvim_rocks.ensure_installed('stdlib')

-- require stuff from binary rock
local cjson = require "cjson"
local cjson2 = cjson.new()
local cjson_safe = require "cjson.safe"

print(vim.inspect(cjson_safe))

-- List installed rocks with version numbers
print(vim.inspect(nvim_rocks.list()))

-- List installed rocks as strings
local simple = true
print(vim.inspect(nvim_rocks.list(simple)))

-- Remove rock
nvim_rocks.remove('lua-cjson')
```
