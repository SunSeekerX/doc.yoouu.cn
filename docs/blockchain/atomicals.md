# Atomicals

文档：https://docs.atomicals.xyz/

公共节点：https://docs.atomicals.xyz/reference-and-tools/electrumx-api-and-public-endpoints

自建全节点索引同步状态：http://localhost:8080/proxy/health

rpc 运行命令：https://github.com/Next-DAO/atomicals-electrumx-proxy-docker/blob/main/README.zh-CN.md

pepe看板：[https://geniidata.com/user/0xmatsu/bitcoin-atomicals-protocol-analytics](https://geniidata.com/user/0xmatsu/bitcoin-atomicals-protocol-analytics)

批量查询：https://www.cpbox.io/atomicals/#/

## 公共节点备选

```
目前几个公有节点备选：
Official： https://ep.atomicals.xyz/proxy
NextDao： https://ep.nextdao.xyz/proxy
Consync： https://ep.consync.xyz/proxy
http://Wizz.Cash： https://ep.atomicalswallet.com/proxy
Atomical Market： https://ep.atomicalmarket.com/proxy
```

## 私有节点搭建

https://geekx.top/crypto/btc/Atomicals.html

## Atomical Market

https://atomicalmarket.com/

## 挖矿工具

[https://github.com/atomicals/atomicals-js.git](https://github.com/atomicals/atomicals-js.git)

### 使用

```shell
# 拉取项目
git clone https://github.com/atomicals/atomicals-js.git
# 进入项目
cd atomicals-js/
# 装包
yarn
# 构建工具
yarn run build
# 然后就可以使用 yarn run cli --help 了，没有 wallet.json 就先初始化钱包
yarn cli wallet-init
# 打钱到 funding 地址就可以开挖
yarn cli mint-dft electron
```

### 更新脚本

```shell
# 拉取新的代码，在项目目录下执行
git pull
# 安装依赖
yarn
# 构建新版本的工具
yarn build
```

### 脚本命令

```shell
npm run cli balances
# 挖 electron --satsbyte=52 是设置 gas 的
yarn cli mint-dft electron --satsbyte=52
```

### nvm

https://github.com/nvm-sh/nvm?tab=readme-ov-file#install--update-script

```shell
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.5/install.sh | bash
# or
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.5/install.sh | bash

# 安装 nodejs
# 查看 lts 版本
nvm ls-remote --lts
# 安装 v20 版本
nvm install v20.10.0
# 设置命令行默认 nodejs 版本
nvm alias default v20.10.0
```

### centos 遇到得问题

```
[root@VM-0-13-centos ~]# node -v
node: /lib64/libm.so.6: version `GLIBC_2.27' not found (required by node)
node: /lib64/libstdc++.so.6: version `GLIBCXX_3.4.20' not found (required by node)
node: /lib64/libstdc++.so.6: version `CXXABI_1.3.9' not found (required by node)
node: /lib64/libstdc++.so.6: version `GLIBCXX_3.4.21' not found (required by node)
node: /lib64/libc.so.6: version `GLIBC_2.28' not found (required by node)
node: /lib64/libc.so.6: version `GLIBC_2.25' not found (required by node)
```

~~解决，升级 **glibc 和 libstdc++ 版本**~~

```shell
# 更新现有包
sudo yum update
```

装低版本的 nodejs 用 16 版本

## 挖 dmint

## 挖 electron

### atomicals-js 命令

```shell
# 挖 electron --satsbyte=52 是设置 gas 的
yarn cli mint-dft electron --satsbyte=52
```

### dune 数据看板

https://dune.com/satsx/electron

### x 信息

- 教程

  https://twitter.com/codefish14/status/1728773220382515403

- 查询顺序方法

  https://twitter.com/qingshan857/status/1729175868487110994

  面板：[https://geniidata.com/user/qingshan857/atom-electron](https://geniidata.com/user/qingshan857/atom-electron)

- 挖⛏️electron的福报细则来了🔥🔥🔥

  https://twitter.com/atomicals_cn/status/1729170033040130066?s=46

- 在线铭刻

  https://satsx.io/inscribe/atomicals

  https://atomicalmarket.com/inscribe?ticker=electron

- 交易市场截至 2023-11-28 03:07:22 一张 60$ 左右

  https://satsx.io/marketplace/atomicals/ft/history?ctypes=FT&page=1

  https://bitatom.io/
