# 学习日志

## Module 1

学习博客: <https://blog.csdn.net/lijj0304/article/details/151830067?sharetype=blogdetail&sharerId=151830067>

### About sui&Mov

Sui 使用面向对象的模型，每个资产都是与钱包相关联的独立对象，允许交易并行处理。Sui 的执行性能很高，区分了资产转移和智能合约调用，还具备很高的可拓展性。Sui 智能合约常用 Move 语言开发，具有类似 OOP 的概念，直观好上手；move 底层是 rust 构建，性能高。

### 环境配置安装

```shell
# MacOS
brew install sui
# 其他系统参考: https://docs.sui.io/guides/developer/getting-started/sui-install

# 连接到 SUI
sui client

# 加入自己的地址
sui keytool import <INPUT_STRING> <KEY_SCHEME> [DERIVATION_PATH]
sui client addresses 

# 切换环境和地址
sui client switch --env <ALIAS>
sui client switch --address <ALIAS>
```

### 领取 gas
Testnet faucet: <https://faucet.sui.io/>

### 铸造自己的 NFT

```shell
cd junjun_nft
sui move build
sui client publish # 发布包，要记住 packageid
sui client call --package <package_id> --module testnet_nft --function mintnft --args <nft_name> <nft_description> <image_url>
# 调用 package 构建一个自己 Github 头像的 NFT:
sui client call --package 0x52e57073c336e4b367005fe4e1a40113c9259ac5d4f90d4c6b48e0458d770234 --module testnet_nft --function mintnft --args "JJLi0427" "Github:JJLi0427 NFT" "https://raw.githubusercontent.com/JJLi0427/SUI_Learn/main/assets/doare_nft.jpeg"
```