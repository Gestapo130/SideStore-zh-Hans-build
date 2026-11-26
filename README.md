# SideStore 简体中文构建

此构建基于官方 SideStore `0.7.0-alpha` 源码提交：
`6032424a0e56c1c319762e786099bdd9186a238b`。

将 `localization.patch` 放在 GitHub 仓库根目录，将 `build-chinese.yml`
放在 `.github/workflows/build-chinese.yml`，然后在仓库的 Actions 页选择
“Build SideStore in Simplified Chinese”，点击 “Run workflow”。

流程使用 GitHub 的 macOS 26，优先选择官方 alpha 构建使用的 Xcode 26.2；
如果该版本已从 runner 移除，则选择当前预装的稳定版 Xcode，实际版本记入
`BUILD-INFO.txt`。流程沿用对应官方 alpha 构建的
`make build`、`make fakesign`、`make ipa`，包括内置 SideBackup 和小组件的
entitlements 保留步骤。无需 Mac、Apple 开发者会员或仓库 Secrets。

成功后下载 `SideStore-0.7.0-zh-Hans-IPA` artifact，解压取得 IPA。
该文件仍需通过兼容的侧载工具用自己的 Apple ID 签名安装，不能直接点击
安装。免费 Apple ID 的有效期和续签要求保持不变。

流程还会保存包含子模块的完整修改后应用源码、翻译补丁、构建出处、SHA-256
以及日志。IPA 与源码下载有效期为 30 天，日志为 14 天；下载到本地即可长期保存。

首次构建会下载 Swift Package 与预编译依赖，耗时取决于 GitHub 排队、网络与
runner 状态。工作流设置了 90 分钟超时，实际完成时间需要以运行结果为准。
这是一份非官方中文构建，基于 alpha 版；安装体验仍需在 iPhone 上验证。
以后更新至官方英文版本时，官方程序文件会覆盖本次中文修改。

SideStore 上游源码及相关修改依照仓库中的 AGPLv3 许可提供；原始 LICENSE
随完整源码归档保留。
