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

## 常用操作指令

### 查詢專案使用之 Python 版本

```sh
pyenv version
```

### 建置專案使用之虛擬環境

```sh
python -m venv .venv
source .venv/bin/activate
```

### 安裝專案使用之 Python 套件

```sh
pip install -r requirements.txt
```

### 製作專案之 Python 套件清單

```sh
rm requirements.txt
pip freeze > requirements.txt
```

### 使用指令執行 pylint

```sh
pylint <source_code>
```

【實例】：

```sh
pylint pg001.py
```

或

```sh
pylint --rcfile=<pylint_configuration> <source_code>
```

【實例】：

```sh
pylint --rcfile=./pyproject.toml pg001.py
```

## Linter 設定檔

### pylint

pylint 之設定檔，檔名可以是以下任何一種：

1.  pylintrc
2.  .pylintrc
3.  pylint.json
4.  pyproject.toml

### mypy

1.  ./mypy.ini
2.  ./.mypy.ini
3.  ./pyproject.toml
4.  ./setup.cfg
5.  $XDG_CONFIG_HOME/mypy/config
6.  ~/.config/mypy/config
7.  ~/.mypy.ini
