> 如果您需要使用到多版本,請使用 `nvm` 進行多版本 `node` 管理

### Windows

_直接安裝:_

1. 去`node`<a href="https://nodejs.org/zh-cn/download/" target="_blank">官方網站下載頁面</a> 下載指定版本的 `windows` 的 `node` 安裝包
2. 安裝選項中選擇自動添加 `PATH`

_使用 nvm:_

1. 去 nvm-windows 官網下載安裝包`https://github.com/coreybutler/nvm-windows/releases`
2. 使用`nvm install`安裝指定版本的`node`
3. 使用`nvm use` 設置使用的`node`版本

```shell
# 列出node版本
nvm list-remote
# 安裝16.9.1版本的 node
nvm install 16.9.1
# 切換到16.9.1版本的 node
nvm use 16.9.1
```

### macOS

_直接安裝:_

1. 去`node`<a href="https://nodejs.org/zh-cn/download/" target="_blank">官方網站下載頁面</a> 下載指定版本的 `macOS ` 的 `node` 安裝包
2. 安裝即可

_brew 安裝_

1. `brew` 安裝,已安裝清忽略,<a href="https://brew.sh/" target="_blank">brew 官網</a>
2. 使用`brew`安裝`node` `brew install node@16`

```shell
# 安裝brew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
# 安裝node 16
brew install node@16
```

_nvm 安裝_

1. `brew` 安裝 `nvm`
2. 使用`nvm install`安裝指定版本的`node`
3. 使用`nvm use` 設置使用的`node`版本

```shell
brew install nvm
# 列出node版本
nvm list-remote
# 安裝16.9.1版本的 node
nvm install 16.9.1
# 切換到16.9.1版本的 node
nvm use 16.9.1
```

### Linux

_shell 安裝_

1. 安裝`node`源
2. 安裝

```shell
curl -sL https://deb.nodesource.com/setup_16.x | sudo -E bash -
apt-get install -y nodejs # 其他系統請使用對應的安卓命令
```

_nvm 安裝_

1. 安裝`nvm`
2. 使用`nvm install`安裝指定版本的`node`
3. 使用`nvm use` 設置使用的`node`版本

```shell
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
# 列出node版本
nvm list-remote
# 安裝16.9.1版本的 node
nvm install 16.9.1
# 切換到16.9.1版本的 node
nvm use 16.9.1
```
