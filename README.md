# PyQt5 專案指引

## 專案摘要

專案目標：

1.  製作 PyQt5 專案之模版；
2.  驗證 AlanJui/nvimX 專案 Neovim 設定檔之可用性。

## nvimX LSP 設計架構

Language Server 要能正常運作，需經：（1）安裝；（2）設定，共兩個步驟。目前我的 nvim 架構設計為：

1.  Language Server 的安裝，透過 Neovim 插件：mason-lspconfig.nvim ，依設定檔的描述進行自動安裝。請參考： `~/.config/nvim/lua/plugins/lsp/mason.lua`

2.  至於 Language Server 的設定，則依然使用 nvim-lspconfig 插件完成；而不是使用 mason-lspconfig.nvim，進行設定的相關工作。正也因為這樣的做法，就算已透過 mason-lspconfig.nvim 完成了 pylsp Language Server 的安裝，但因沒有後續的 pylsp Language Server 設定，所以即便替打開了 File Type 為 python 的檔案，卻不見 pylsp Language Server 正常運作，這也算是正常的結果。
    請參考： `~/.config/nvim/lua/plugins/lsp/lspconfig.lua`
