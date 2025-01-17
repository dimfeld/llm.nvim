# llm.nvim

A neovim plugin for no frills LLM-assisted programming.


https://github.com/melbaldove/llm.nvim/assets18225174/9bdc2fa1-ade4-48f2-87ce-3019fc323262


### Installation

Before using the plugin, set the `GROQ_API_KEY` and/or the `OPENAI_API_KEY` env vars with your api keys.

lazy.nvim
```lua
{
    "melbaldove/llm.nvim",
    dependencies = { "nvim-neotest/nvim-nio" }
}
```

### Usage

**`prompt()`**

Triggers the LLM assistant. You can pass an optional `replace` flag to replace the current selection with the LLM's response. The prompt is either the visually selected text or the file content up to the cursor if no selection is made.

**`create_llm_md()`**

Creates a new `llm.md` file in the current working directory, where you can write questions or prompts for the LLM.

**Example Bindings**
```lua
vim.keymap.set("n", "<leader>m", function() require("llm").create_llm_md() end)

-- keybinds for prompting with groq
vim.keymap.set("n", "<leader>,", function() require("llm").prompt({ replace = false, service = "groq" }) end)
vim.keymap.set("v", "<leader>,", function() require("llm").prompt({ replace = false, service = "groq" }) end)
vim.keymap.set("v", "<leader>.", function() require("llm").prompt({ replace = true, service = "groq" }) end)

-- keybinds for prompting with openai
vim.keymap.set("n", "<leader>g,", function() require("llm").prompt({ replace = false, service = "openai" }) end)
vim.keymap.set("v", "<leader>g,", function() require("llm").prompt({ replace = false, service = "openai" }) end)
vim.keymap.set("v", "<leader>g.", function() require("llm").prompt({ replace = true, service = "openai" }) end)
```

### Roadmap
- [ollama](https://github.com/ollama/ollama) support

### Credits

- Special thanks to [yacine](https://twitter.com/i/broadcasts/1kvJpvRPjNaKE) and his ask.md vscode plugin for inspiration!
