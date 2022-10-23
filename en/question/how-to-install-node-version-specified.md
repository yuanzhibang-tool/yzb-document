> If you need to use multiple versions, please use `nvm` for multi-version `node` management

### Windows

_Direct installation:_

1. Go to `node`<a href="https://nodejs.org/zh-cn/download/" target="_blank">official website download page</a> to download the specified version of `windows` of `node` install package
2. In the installation options, choose to automatically add `PATH`

_use nvm:_

1. Go to the nvm-windows official website to download the installation package`https://github.com/coreybutler/nvm-windows/releases`
2. Use `nvm install` to install the specified version of `node`
3. Use `nvm use` to set the version of `node` to use

```shell
# list node versions
nvm list-remote
# Install node 16.9.1
nvm install 16.9.1
# switch to node 16.9.1
nvm use 16.9.1
```

### macOS

_Direct installation:_

1. Go to `node`<a href="https://nodejs.org/zh-cn/download/" target="_blank">official website download page</a> to download the specified version of `node` for `macOS` ` install package
2. Just install

_brew install_

!> The source repository of brew uses `github` source, please <a href="https://su.yuanzhibang.com/2Cp" target="_blank">click</a> to accelerate `github`

1. `brew` installation, installed and ignored, <a href="https://brew.sh/" target="_blank">brew official website</a>
2. Install `node` using `brew` `brew install node@16`

```shell
# install brew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
# install node 16
brew install node@16
```

_nvm install_

1. `brew` install `nvm`
2. Use `nvm install` to install the specified version of `node`
3. Use `nvm use` to set the version of `node` to use

```shell
brew install nvm
# list node versions
nvm list-remote
# Install node 16.9.1
nvm install 16.9.1
# switch to node 16.9.1
nvm use 16.9.1
```

### Linux

_shell install_

1. Install the `node` source
2. Installation

```shell
curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -
apt-get install -y nodejs # For other systems, please use the corresponding Android command
```

_nvm install_

1. Install `nvm`
2. Use `nvm install` to install the specified version of `node`
3. Use `nvm use` to set the version of `node` to use

```shell
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
# list node versions
nvm list-remote
# Install node 16.9.1
nvm install 16.9.1
# switch to node 16.9.1
nvm use 16.9.1
```
