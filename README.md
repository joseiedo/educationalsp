# `educationalsp`
A Language Server built for the educational purpose of understanding **WHAT** LSP is and **HOW** it works.
This LSP was tested with Neovim, but would likely work inside VS Code.

[Lesson By TJ DeVries](https://www.youtube.com/watch?v=YsdlcQoHqPY)

## Quick setup on neovim
1. Build the project with `go build main.go`
2. Setup the binary to the lsp consig in you nvim config

```lua
local client = vim.lsp.start_client {
  name = 'educationalsp',
  cmd = { '<path-to-project-binary>' },
}

if not client then
  vim.notify 'Something wrong with the client setup'
  return
end

vim.api.nvim_create_autocmd('FileType', {
  pattern = 'markdown',
  callback = function()
    vim.lsp.buf_attach_client(0, client)
  end,
})
```
