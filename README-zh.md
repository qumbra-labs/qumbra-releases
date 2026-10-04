# Qumbra 发布

> [English](README.md)

这里发布 Qumbra 各钱包的签名安装包。仓库里**没有源码**，只放各钱包的发布产物，每个文件旁边都附有校验值。

每个产品用自己的 tag：

| 产品 | tag 格式 | 文件 |
|---|---|---|
| Qumbra Wallet for Mac | `macos-vX.Y.Z` | `QumbraWalletMac-X.Y.Z.dmg`、`.zip`，以及各自的 `.sha256` |

其他钱包（浏览器扩展、桌面版、iOS、Android）公开发布时，也会发在这里。

**测试网。** 目前的版本连接的是 Qumbra 测试网，里面的币和资产都是**测试币**，没有价值。

## 校验下载

1. **校验值。** 在同时放着安装包和 `.sha256` 文件的目录里运行：

   ```sh
   shasum -a 256 -c QumbraWalletMac-X.Y.Z.dmg.sha256
   ```

   必须输出 `OK`。发布说明里也会写出 SHA-256。

2. **签名与公证（macOS）。** 安装包用 Apple 团队 `CMV44JGUS3` 的 Developer ID 证书签名，经 Apple 公证并装订了公证票据。挂载 DMG 后运行：

   ```sh
   spctl -a -vv "/Volumes/Qumbra Wallet for Mac X.Y.Z/Qumbra Wallet for Mac.app"
   ```

   结果必须是 `accepted` 和 `source=Notarized Developer ID`，并且 `origin=` 那一行要以 `(CMV44JGUS3)` 结尾。两项检查有任何一项不通过，都不要运行这个安装包。

## 每个版本会写明什么

每个版本都写明构建所用的源码版本、工具链、Apple 公证提交编号，以及每个文件的 SHA-256。开源许可证声明打包在 App 里面，macOS 版在 **设置 → 关于 → 开源许可证**。
