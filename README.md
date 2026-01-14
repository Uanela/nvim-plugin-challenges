# Neovim Plugins Challenges


# 🟢 BEGINNER — 8 PLUGINS (VERY BASIC)

Goal: **Lua basics + Neovim API + tables + execution**

These should feel “too easy” at first. That’s intentional.


## 1. `hello-command.nvim`

**What it does**

* Adds `:HelloLua`
* Prints “Hello from Lua”

**You learn**

* `vim.api.nvim_create_user_command`
* Lua modules
* Plugin structure

## 2. `echo-mode.nvim`

**What it does**

* Command prints current `vim.bo.filetype` and mode

**You learn**

* `vim.bo`, `vim.fn.mode`
* Lua ↔ Vim data access


## 3. `buffer-count.nvim`

**What it does**

* Command shows number of open buffers

**You learn**

* `vim.api.nvim_list_bufs`
* Iterating tables
* Returning values


## 4.`auto-trim.nvim`

**What it does**

* Trims trailing whitespace on save

**You learn**

* `autocmd`
* `vim.api.nvim_create_autocmd`
* Callbacks

---

## 5️⃣ `simple-toggle.nvim`

**What it does**

* Toggles a boolean option (e.g. `relativenumber`)

**You learn**

* Mutable state
* Boolean logic
* Tables as state holders

---

## 6️⃣ `file-notifier.nvim`

**What it does**

* Prints file name when entering a buffer

**You learn**

* Events
* `BufEnter`
* Execution order

---

## 7️⃣ `basic-keymap.nvim`

**What it does**

* Sets a few Lua keymaps

**You learn**

* `vim.keymap.set`
* Function references
* Lazy execution

---

## 8️⃣ `config-check.nvim`

**What it does**

* Command that checks if certain options are set correctly

**You learn**

* Tables as configuration
* Validation logic
* Error handling

---

# 🟡 MID — 5 PLUGINS

Goal: **state, modules, require, async, real Lua problems**

Now things will break. Good.

---

## 9️⃣ `session-lite.nvim`

**What it does**

* Save / restore session (buffers + cwd)

**You learn**

* Persistent state
* File IO
* Serialization

---

## 🔟 `project-root.nvim`

**What it does**

* Detect project root (`.git`, `package.json`)

**You learn**

* Filesystem traversal
* `vim.loop.fs_stat`
* Caching results

---

## 1️⃣1️⃣ `command-history.nvim`

**What it does**

* Tracks last N commands and shows them

**You learn**

* Ring buffers
* Table mutation
* Performance considerations

---

## 1️⃣2️⃣ `async-grep.nvim`

**What it does**

* Async grep using ripgrep
* Show results in a scratch buffer

**You learn**

* `vim.loop`
* Async callbacks
* Race conditions

---

## 1️⃣3️⃣ `plugin-manager-lite.nvim`

**What it does**

* Minimal plugin loader (clone + source)

**You learn**

* Execution order
* `require` pitfalls
* Dynamic loading

This is where Lua *really* clicks.

---

# 🔴 PRO — 3 PLUGINS

Goal: **architecture, performance, mastery**

These are hard. No shortcuts.

---

## 1️⃣4️⃣ `stateful-ui.nvim`

**What it does**

* Floating window UI
* Maintains internal state
* Updates dynamically

**You learn**

* Table identity
* UI lifecycle
* Separation of concerns

---

## 1️⃣5️⃣ `lsp-helper.nvim`

**What it does**

* Wraps LSP calls
* Caches responses
* Adds helper commands

**You learn**

* Async APIs
* Callback composition
* Error handling

---

## 1️⃣6️⃣ `plugin-framework.nvim`

**What it does**

* Framework to build other plugins
* Hook system
* Config validation

**You learn**

* Metatables
* Public vs private APIs
* Real Lua architecture

This is **actual Lua mastery**.

---

# HOW TO DO THIS CORRECTLY (IMPORTANT)

For **each plugin**:

1. No copying from other plugins
2. Write README
3. Break it once on purpose
4. Refactor at least once

If you don’t refactor, you didn’t learn.

---

# TIMELINE (REALISTIC)

* Beginner: **2–3 weeks**
* Mid: **1–2 months**
* Pro: **2–3 months**

You’ll *feel dumb* during Mid. That’s expected.
