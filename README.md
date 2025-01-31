[![golangci-lint-status](https://github.com/mrjosh/helm-ls/actions/workflows/golangci-lint.yml/badge.svg)](https://github.com/mrjosh/helm-ls/actions/workflows/golangci-lint.yml)
[![Release](https://github.com/mrjosh/helm-ls/actions/workflows/go-artifacts.yml/badge.svg)](https://github.com/mrjosh/helm-ls/releases/latest)
![License](https://img.shields.io/github/license/mrjosh/helm-ls)

<pre align="center">
  /\  /\___| |_ __ ___   / / ___ 
 / /_/ / _ \ | '_ ` _ \ / / / __|
/ __  /  __/ | | | | | / /__\__ \
\/ /_/ \___|_|_| |_| |_\____/___/
</pre>

## ⚠️ This project is still in early development. ⚠️

## Helm Language Server Protocol
helm-ls is [helm](https://github.com/helm/helm) language server protocol [LSP](https://microsoft.github.io/language-server-protocol/).

## Getting Started
### Vim Helm Plugin
You'll need [vim-helm](https://github.com/towolf/vim-helm) plugin installed before using helm_ls, Try to install it vim:
```lua
Plug 'towolf/vim-helm'
```

### Download
* Download the latest helm_ls executable file from [here](https://github.com/mrjosh/helm-ls/releases/latest) and move it to your binaries directory 

* You can download it with curl, replace the {os} and {arch} variables
```bash
curl -L https://github.com/mrjosh/helm-ls/releases/download/master/helm_ls_{os}_{arch} --output /usr/local/bin/helm_ls
```

### Make it executable
```bash
chmod +x /usr/local/bin/helm_ls
```

## nvim-lspconfig setup
```lua
local configs = require('lspconfig.configs')
local lspconfig = require('lspconfig')
local util = require('lspconfig.util')

if not configs.helm_ls then
  configs.helm_ls = {
    default_config = {
      cmd = {"helm_ls", "serve"},
      filetypes = {'helm'},
      root_dir = function(fname)
        return util.root_pattern('Chart.yaml')(fname)
      end,
    },
  }
end

lspconfig.helm_ls.setup {
  filetypes = {"helm"},
  cmd = {"helm_ls", "serve"},
}
```

[![asciicast](https://asciinema.org/a/485522.svg)](https://asciinema.org/a/485522)

## Contributing
Thank you for considering contributing to HelmLs project!

## License
The HelmLs is open-source software licensed under the MIT license.
