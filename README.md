# Neovim Plugins Challenges

This repo was designed to give a guide from does whom are looking forward to master or be good at developing nvim plugins

## Pre Requisites:

- Be a nvim user (Of course)
- Lua knowledge (Beginner level is ok)

Those challenges aim to challenge you from begginer level to pro level so that you practice as you go.

## Philosophy

I ([Uanela](https://github.com/uanela)) learned lua on a very very short time and grasped everything (kind of), what I mean is that I learned everything that there was to learn when you learn a new programming language but only learning (reading, watch tutorials or wather) is not enough to start going out there trying to build the next BIG `nvim` plugin in the world or maybe

try to contribute to one of the biggest nvim plugins in the world. If knowing this guess what, I did it, I started contributing on [nvim-tree](https://github.com/nvim-tree/nvim-tree.lua) thanks to [Alex Courtis](https://github.com/alex-courtis) I had my first merge (A very simple refactor[nvim-tree #3222](https://github.com/nvim-tree/nvim-tree.lua/pull/3222)) and got more tasks to keep going on. I got started with my second

task but reality then hit me so HARD that I couldn't ignore the pain, I thought I was doing great (which I was slightly) but then things kind of fell apart, on my second PR [nvim-tree #3233](https://github.com/nvim-tree/nvim-tree.lua/pull/3233) I did good job which was appreciated by the maintainers but need to do somes changes because

some parts of the refactor (Yes the second PR was a refactor too) didn't go very well and were throwing some errors. Even after [Alex Courtis](https://github.com/alex-courtis) guide me on what I should work I was still struggling a little big with the task needing to keep going around reading some articles (which is ok on any level of carrer), nowadays checking with AI also (which many will not admit)

But I noticed something I was searching for really really basic things which I should know from the beggining but I didn't, you know why??? because I've never ever before developed some real useful using lua related to nvim, which caused to struggle to basic things (not at all because I am contributing to world class tree on nvim-tree) but for me I felt that were

basics. Because I looked to other langauges I use and I became like I can write marvelous things in other languages with my eyes closed, but I am struggling here so I decided to do what I did on the past with `JavaScript` even after beging able to use it for many thing I decided to create a bar level for myself in which I kept going higher and higher.

I created something for just like what you see on this repo, a collection of challenges devided into tree major levels Beginner, Mid, Pro. So that I could measure my own knowledge with confidence and pratice more, which ended up being one of the best things I did for mastering JavaScript/TypeScript (Check my Github profile by yourself [Uanela Como](https://github.com/uanela)).

## How To Take The Challenges

Notice that the challenges are devided into 3 major levels:

1. `Beginner` - very basic 8 plugins
2. `Mid` - not basic and not pro level 5 plugins
3. `Pro` - kind hard 3 plugis

Each level aims to challenge yourself according to your knowledge base not only this but this set of challenge can serve you as a way to measure your own knowledge, for example if you passed the begginer phase you can put on your head and say to everyone that you no longer a simple begginer `nvim` plugin creator with more confidence.

You can even jump some challenges but I highly recommend to go through all of them no matter what level o mastering you are, for example on beginner level just created 5 plugins, mid 3, pro 1 and so on.

So fill free to enjoy yourself, do not forget to share this repo to whoever might need and also leave star on it.

## How To do This Correctly (Important)

For **each plugin**:

1. No copying from other plugins
2. Write README
3. Break it once on purpose
4. Refactor at least once

If you don’t refactor, you didn’t learn.

# CHALLENGES

## BEGINNER — 8 PLUGINS (VERY BASIC)

Goal: **Lua basics + Neovim API + tables + execution**

These should feel “too easy” at first. That’s intentional.

## 1. `hello-command.nvim`

**What it does**

- Adds `:HelloLua`
- Prints “Hello from Lua”

**You learn**

- `vim.api.nvim_create_user_command`
- Lua modules
- Plugin structure

## 2. `echo-mode.nvim`

**What it does**

- Command prints current `vim.bo.filetype` and mode

**You learn**

- `vim.bo`, `vim.fn.mode`
- Lua ↔ Vim data access

## 3. `buffer-count.nvim`

**What it does**

- Command shows number of open buffers

**You learn**

- `vim.api.nvim_list_bufs`
- Iterating tables
- Returning values

## 4. `auto-trim.nvim`

**What it does**

- Trims trailing whitespace on save

**You learn**

- `autocmd`
- `vim.api.nvim_create_autocmd`
- Callbacks

## 5. `simple-toggle.nvim`

**What it does**

- Toggles a boolean option (e.g. `relativenumber`)

**You learn**

- Mutable state
- Boolean logic
- Tables as state holders

## 6. `file-notifier.nvim`

**What it does**

- Prints file name when entering a buffer

**You learn**

- Events
- `BufEnter`
- Execution order

## 7. `basic-keymap.nvim`

**What it does**

- Sets a few Lua keymaps

**You learn**

- `vim.keymap.set`
- Function references
- Lazy execution

## 8. `config-check.nvim`

**What it does**

- Command that checks if certain options are set correctly

**You learn**

- Tables as configuration
- Validation logic
- Error handling

## MID — 5 PLUGINS

Goal: **state, modules, require, async, real Lua problems**

Now things will break. Good.

## 9. `session-lite.nvim`

**What it does**

- Save / restore session (buffers + cwd)

**You learn**

- Persistent state
- File IO
- Serialization

## 10. `project-root.nvim`

**What it does**

- Detect project root (`.git`, `package.json`)

**You learn**

- Filesystem traversal
- `vim.loop.fs_stat`
- Caching results

## 11. `command-history.nvim`

**What it does**

- Tracks last N commands and shows them

**You learn**

- Ring buffers
- Table mutation
- Performance considerations

## 12. `async-grep.nvim`

**What it does**

- Async grep using ripgrep
- Show results in a scratch buffer

**You learn**

- `vim.loop`
- Async callbacks
- Race conditions

## 13. `plugin-manager-lite.nvim`

**What it does**

- Minimal plugin loader (clone + source)

**You learn**

- Execution order
- `require` pitfalls
- Dynamic loading

This is where Lua _really_ clicks.

# PRO — 3 PLUGINS

Goal: **architecture, performance, mastery**

These are hard. No shortcuts.

## 14. `stateful-ui.nvim`

**What it does**

- Floating window UI
- Maintains internal state
- Updates dynamically

**You learn**

- Table identity
- UI lifecycle
- Separation of concerns

## 15. `lsp-helper.nvim`

**What it does**

- Wraps LSP calls
- Caches responses
- Adds helper commands

**You learn**

- Async APIs
- Callback composition
- Error handling

## 16. `plugin-framework.nvim`

**What it does**

- Framework to build other plugins
- Hook system
- Config validation

**You learn**

- Metatables
- Public vs private APIs
- Real Lua architecture

This is **actual Lua mastery**.

You’ll _feel dumb_ during Mid. That’s expected.
