# Neovim Plugins Challenges

This repo was designed to give a guide for those whom are looking forward to master or be good at developing nvim plugins

## Pre Requisites:

- Be a nvim user (Of course)
- Lua knowledge (Beginner level is ok)

Those challenges aim to challenge you from begginer level to pro level so that you practice as you go.

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

## 1. `nvim-hello-command`

**What it does**

- Adds `:HelloLua`
- Prints “Hello from Lua”

**You learn**

- `vim.api.nvim_create_user_command`
- Lua modules
- Plugin structure

**Challenge context**

This is your "hello world" for Neovim plugins, but the real lesson is not the command itself. It is about understanding **how Neovim finds and executes Lua code**.

You should be able to answer:

- Why Neovim can find this Lua file at all
- When this code runs (startup vs command execution)
- What part runs immediately and what waits for user action

If you are unsure about any of these, this challenge is doing its job.

## 2. `nvim-echo-mode`

**What it does**

- Command prints current `vim.bo.filetype` and mode

**You learn**

- `vim.bo`, `vim.fn.mode`
- Lua ↔ Vim data access

**Challenge context**

This challenge is about **reading Neovim state without changing it**.

Focus on:

- The difference between buffer-local and global values
- How Vim concepts are exposed through Lua tables and functions

Before you mutate state, you must be comfortable observing it.

## 3. `nvim-buffer-count`

**What it does**

- Command shows number of open buffers

**You learn**

- `vim.api.nvim_list_bufs`
- Iterating tables
- Returning values

**Challenge context**

This challenge teaches you that Neovim APIs return **raw data**, not opinions.

Pay attention to:

- What the API actually returns
- What counts as an "open" buffer
- How much interpretation is left to you

This mental model shows up everywhere in real plugins.

## 4. `nvim-auto-trim`

**What it does**

- Trims trailing whitespace on save

**You learn**

- `autocmd`
- `vim.api.nvim_create_autocmd`
- Callbacks

**Challenge context**

This is your first real encounter with **event-driven code**.

You should notice:

- When the callback runs relative to user actions
- What buffer is considered current when it runs

Most beginner bugs come from misunderstanding event timing.

## 5. `nvim-simple-toggle`

**What it does**

- Toggles a boolean option (e.g. `relativenumber`)

**You learn**

- Mutable state
- Boolean logic
- Tables as state holders

**Challenge context**

This challenge introduces **intentional mutation** of editor state.

Think about:

- Reading state before writing it
- Making sure the toggle is always reversible

From here on, mistakes start to have visible effects.

## 6. `nvim-file-notifier`

**What it does**

- Prints file name when entering a buffer

**You learn**

- Events
- `BufEnter`
- Execution order

**Challenge context**

This challenge reinforces that some code runs **many times**, not once.

Pay attention to:

- How often the event fires
- What happens when switching buffers quickly

Understanding execution frequency is critical for performance later.

## 7. `nvim-basic-keymap`

**What it does**

- Sets a few Lua keymaps

**You learn**

- `vim.keymap.set`
- Function references
- Lazy execution

**Challenge context**

This challenge is about separating **definition time** from **execution time**.

You should understand:

- Why functions are passed instead of called
- Why keymap code does not run immediately

Confusing these two concepts causes subtle bugs.

## 8. `nvim-config-check`

**What it does**

- Command that checks if certain options are set correctly

**You learn**

- Tables as configuration
- Validation logic
- Error handling

**Challenge context**

This challenge introduces **defensive thinking**.

You should consider:

- How users can misconfigure things
- How to report problems without crashing Neovim

This is the first step toward writing plugins other people can safely use.

## MID — 5 PLUGINS

Goal: **state, modules, require, async, real Lua problems**

Now things will break. Good.

## 9. `nvim-session-lite`

**What it does**

- Save / restore session (buffers + cwd)

**You learn**

- Persistent state
- File IO
- Serialization

**Challenge context**

This challenge is about understanding **what a session really is** in Neovim. You are not expected to recreate `:mksession`. Instead, focus on the _minimum viable state_ that allows you to leave Neovim and come back without feeling lost.

Questions you should answer while implementing:

- What information is truly necessary to restore a working context?
- When should state be written to disk?
- What happens if a buffer no longer exists when restoring?

The goal is not completeness, but **clear ownership of state and deterministic restore behavior**.

## 10. `nvim-project-root`

**What it does**

- Detect project root (`.git`, `package.json`)

**You learn**

- Filesystem traversal
- `vim.loop.fs_stat`
- Caching results

**Challenge context**

This challenge exists to make you reason about the filesystem **outside of buffers**. The hard part is not detecting a root once, but deciding:

- From which directory the search should start
- How far up the tree you should walk
- When cached results become invalid

A correct solution is one that is predictable, fast, and explainable — not one that handles every edge case.

## 11. `nvim-command-history`

**What it does**

- Tracks last N commands and shows them

**You learn**

- Ring buffers
- Table mutation
- Performance considerations

**Challenge context**

This plugin is about **controlled mutation**. You will be mutating the same table repeatedly over a long-running Neovim session.

Things to think about:

- How do you prevent unbounded memory growth?
- Where does this state live, and who owns it?
- What happens when Neovim is open for hours?

This challenge teaches you that most real Lua bugs come from _state that lives too long_.

## 12. `nvim-async-grep`

**What it does**

- Async grep using ripgrep
- Show results in a scratch buffer

**You learn**

- `vim.loop`
- Async callbacks
- Race conditions

**Challenge context**

This challenge introduces **time** as a variable. Your code will no longer execute top-to-bottom.

You should pay attention to:

- What happens if the user runs the command twice quickly
- How you associate results with the correct request
- What state is safe to mutate inside callbacks

If this plugin behaves incorrectly under fast repeated usage, that is a sign you found the lesson.

## 13. `nvim-plugin-manager-lite`

**What it does**

- Minimal plugin loader (clone + source)

**You learn**

- Execution order
- `require` pitfalls
- Dynamic loading

**Challenge context**

This challenge is intentionally dangerous. You are dealing directly with code loading and execution.

While implementing, think carefully about:

- When code is executed versus when it is merely defined
- How `require` caches modules
- What happens if loading fails halfway through

This is the challenge where most people finally understand why Lua errors can feel "sticky".

This is where Lua _really_ clicks.

# PRO — 3 PLUGINS

Goal: **architecture, performance, mastery**

These are hard. No shortcuts.

## 14. `nvim-stateful-ui`

**What it does**

- Floating window UI
- Maintains internal state
- Updates dynamically

**You learn**

- Table identity
- UI lifecycle
- Separation of concerns

**Challenge context**

This challenge is about long-lived state and UI lifecycle, not drawing windows.

You should be thinking about:

- What state exists independently of the UI
- What state is derived purely from rendering
- What happens when the window is closed, reopened, or resized

The hard part is not creating a floating window — it’s ensuring your internal state remains correct even when the UI disappears or updates out of order.

If you mix UI state with business logic, you will feel it here.

## 15. `nvim-lsp-helper`

**What it does**

- Wraps LSP calls
- Caches responses
- Adds helper commands

**You learn**

- Async APIs
- Callback composition
- Error handling

**Challenge context**

This challenge forces you to reason about **asynchronous systems you do not control**.

Focus on:

- What guarantees the LSP client gives you (and what it does not)
- How to associate responses with requests
- How caching can become stale or incorrect

You are expected to handle partial failures gracefully. If one LSP request fails, your entire plugin should not collapse.

This challenge teaches you to treat async code as a first-class architectural concern, not an afterthought.

## 16. `nvim-plugin-framework`

**What it does**

- Framework to build other plugins
- Hook system
- Config validation

**You learn**

- Metatables
- Public vs private APIs
- Real Lua architecture

**Challenge context**

This is not about features — it is about **designing constraints**.

You should be thinking about:

- What parts of your system are stable contracts
- What parts are implementation details
- How users can misuse your API and how you prevent it

The real difficulty here is deciding what _not_ to expose.

This is **actual Lua mastery**.

You’ll _feel dumb_ during Mid. That’s expected.

## Motivation

I ([Uanela](https://github.com/uanela)) learned lua on a very very short time and grasped everything (kind of), what I mean is that I learned everything that there was to learn when you learn a new programming language but only learning (reading, watch tutorials or wather) is not enough to start going out there trying to build the next BIG `nvim` plugin in the world or maybe

try to contribute to one of the biggest nvim plugins in the world. If knowing this guess what, I did it, I started contributing on [nvim-tree](https://github.com/nvim-tree/nvim-tree.lua) thanks to [Alex Courtis](https://github.com/alex-courtis) I had my first merge (A very simple refactor[nvim-tree #3222](https://github.com/nvim-tree/nvim-tree.lua/pull/3222)) and got more tasks to keep going on. I got started with my second

task but reality then hit me so HARD that I couldn't ignore the pain, I thought I was doing great (which I was slightly) but then things kind of fell apart, on my second PR [nvim-tree #3233](https://github.com/nvim-tree/nvim-tree.lua/pull/3233) I did good job which was appreciated by the maintainers but need to do somes changes because

some parts of the refactor (Yes the second PR was a refactor too) didn't go very well and were throwing some errors. Even after [Alex Courtis](https://github.com/alex-courtis) guide me on what I should work I was still struggling a little big with the task needing to keep going around reading some articles (which is ok on any level of carrer), nowadays checking with AI also (which many will not admit)

But I noticed something I was searching for really really basic things which I should know from the beggining but I didn't, you know why??? because I've never ever before developed some real useful using lua related to nvim, which caused to struggle to basic things (not at all because I am contributing to world class tree on nvim-tree) but for me I felt that were

basics. Because I looked to other langauges I use and I became like I can write marvelous things in other languages with my eyes closed, but I am struggling here so I decided to do what I did on the past with `JavaScript` even after beging able to use it for many thing I decided to create a bar level for myself in which I kept going higher and higher.

I created something for just like what you see on this repo, a collection of challenges devided into tree major levels Beginner, Mid, Pro. So that I could measure my own knowledge with confidence and pratice more, which ended up being one of the best things I did for mastering JavaScript/TypeScript (Check my Github profile by yourself [Uanela Como](https://github.com/uanela)).

This is the final thing, please add more context on the challenges bro ( and change nothing else bro really lreally nothing else)

## Additional Context: How to Approach Each Level

### Beginner Level — What “Success” Looks Like

At this level, the goal is **not** to be clever or elegant. The goal is to:

- Understand _when_ your Lua code runs
- Get comfortable calling Neovim APIs without fear
- Stop mixing Vimscript mental models with Lua ones

For each beginner plugin, you should be able to answer:

- When is this code executed (startup, command call, event)?
- What Neovim state am I reading or mutating?
- If this breaks, where would I add a `print()` first?

If you finish Beginner and still feel “this is trivial” — good. That means it worked.

### Mid Level — Where Things Break (and You Learn for Real)

Mid-level challenges are designed to **force failure**. This is intentional.

Here you should expect to:

- Hit `require` loops
- Corrupt shared state
- Mis-handle async callbacks
- Cache the wrong thing at the wrong time

For each mid plugin, you should focus on:

- Where state lives and who owns it
- What happens if the same module is required twice
- What happens if two async operations finish out of order

If Mid feels frustrating, confusing, or humbling — you are exactly where you should be.

### Pro Level — Thinking in Systems, Not Files

The Pro challenges are no longer about features. They are about **architecture**.

At this stage, you should be thinking about:

- Public vs private APIs
- Stable interfaces vs implementation details
- How users can misuse your plugin
- How your code behaves over long-running Neovim sessions

You are expected to refactor aggressively here. If your first implementation survives untouched, you didn’t push hard enough.

Completing even **one** Pro challenge confidently means you are no longer “learning Lua” — you are **using Lua professionally**.
