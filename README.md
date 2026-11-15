# Kirara_Server_Studio

<p align="center">
  <img src="Assets/Kirara_Server_Studio-logo.png" width="100" alt="Kirara Server Studio">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Version-1.7.1-blue" alt="Version">
  <img src="https://img.shields.io/badge/Platform-Windows%2010%2B-0078D4" alt="Platform">
  <img src="https://img.shields.io/badge/.NET-10-512BD4" alt=".NET">
  <img src="https://img.shields.io/badge/License-All%20Rights%20Reserved-lightgrey" alt="License">
</p>

<p align="center"><a href="README.en.md">English</a> | 简体中文</p>

**Kirara_Server 的 Windows 客户端。** 把 Kirara_Server 上的媒体库、云盘、直播、邮箱、远程桌面、OpenVPN、游戏服务器等服务收进同一个窗口：用「实例」区分账号和用途，链接一次令牌，之后打开即自动登录。

---

## 功能一览

| 能力 | 说明 |
| --- | --- |
| **实例化管理** | 按账号或用途创建多个实例，互不干扰；支持重命名、收藏、颜色标签，也能导出成 `.kirara` 文件分享给别人。 |
| **20+ 内置方案** | 媒体、云盘、直播、邮箱、笔记、社区、远程桌面、OpenVPN、虚拟化与软路由、游戏服务器、证书签发等；第三方程序也可以作为方案导入。 |
| **自动登录** | 令牌加密保存在本机，进入实例后自动完成各站点登录；服务端重启或网络抖动时退避重试，不会误判成令牌失效。 |
| **令牌管理器** | 集中管理账户与凭据，支持扫码导出到手机：动态二维码每 15 秒刷新，只有令牌所属账户能导入。 |
| **应用商店** | 一键安装或升级 FreeRDP、OpenVPN、WebView2 等运行时；网页下载统一进下载管理器，支持暂停、继续与停止。 |
| **通知与社区** | 实时通知、议题评论、收藏与催更，与手机端同步；通知支持图片、视频卡片。 |
| **云同步** | 「实例 + 令牌」可备份到云端并在别的机器恢复；本机设置和通知已读状态不参与同步，恢复时也不会被覆盖。 |
| **桌面体验** | Fluent 2 界面、明暗模式与 48 色主题、开机自启、外部文件直接拖进页面。 |

## 系统要求

| 项目 | 要求 |
| --- | --- |
| 操作系统 | Windows 10 1809（10.0.17763）及以上，建议 Windows 11 |
| 架构 | x64 |
| 内存 | 建议 16 GB |
| 显卡 | 建议 NVIDIA GeForce RTX 2060 及以上，并保持驱动为最新（用于画面 AI 超分与 HDR） |
| 运行时 | .NET 10，安装包已内置 |
| 权限 | 日常使用不需要管理员；安装、升级、卸载安装包本身需要 |

## 下载与安装

1. 在仓库 **Releases** 页下载最新安装包 `Kirara_Server_Studio_Setup_x64_vX.X.X.exe`。
2. 运行安装向导。WebView2 为必需组件；OpenVPN、FreeRDP 为可选组件，默认不勾选，之后可在应用内「应用商店」补装。
3. 首次启动登录 Kirara_Server 通行证，阅读并同意《Kirara Server Studio 软件许可协议》。
4. 升级由内置更新程序完成。落后多个版本时，更新弹窗会逐版本列出说明；其中标记为重要更新的版本必须安装后才能继续使用。

## 快速开始

```
① 新建实例  →  ② 选择方案  →  ③ 链接令牌
```

1. **新建实例**：左侧栏「创建新用户实例」或「创建新服务实例」，命名即可；首次使用也可以直接套用「快速开始」里的模板。
2. **选择方案**：勾选要用的服务，可以多选。
3. **链接令牌**：先在「令牌管理器」里创建对应账户的令牌，再回到方案页链接。部署完成后，各页面会自动登录。

之后打开实例就能直达，不用再手动登录。手机端 [Kirara_Media](https://gitee.com/kiraramoe/kirara_media) 可以在「设置 → 令牌管理器 → 扫码导入」里扫描桌面端二维码，把令牌带过去。

## 常用操作

- **关闭实例**：实例标签行内的「关闭实例」，忙或未启动时按钮自动灰化。
- **云同步**：左侧栏搜索框旁的云朵按钮，或令牌管理器里的云朵按钮。
- **插件**：左侧导航最上方的「应用商店」，安装、升级、卸载 FreeRDP / OpenVPN / WebView2。
- **通知**：右下角角标展开，分「信息流 / 服务项 / 日志」三个标签页。
- **数据与外观**：「设置中心」里管理缓存、本地数据、云端数据与主题。

## 常见问题

<details>
<summary><b>安装或连接 VPN 需要管理员权限吗？</b></summary>

日常使用不需要。应用以普通用户权限运行（`asInvoker`），OpenVPN 所需的 TAP / Wintun 虚拟网卡由安装时注册的 `KiraraVpnHelper` 服务（LocalSystem）创建，连接 VPN 不会弹 UAC。只有安装、升级、卸载安装包本身需要管理员权限。
</details>

<details>
<summary><b>手机扫码导入令牌失败？</b></summary>

桌面端和手机必须登录同一个 Kirara 账户，令牌只能导入到它所属的账户。二维码约每 15 秒刷新一次，提示「二维码已过期」时等图案刷新后立刻重扫，并保持桌面端扫码窗口打开。
</details>

<details>
<summary><b>云同步会上传我的设置和通知吗？</b></summary>

不会。同步范围只有「实例 + 令牌」，主题、软件行为、左侧栏等偏好以及通知中心的已读状态都不参与；从云端恢复时，包里即使带有这些字段也会被忽略。云端已存的数据可在「设置中心 → 数据管理 → 清空云端数据」删除。
</details>

<details>
<summary><b>数据存在哪里？想彻底重来怎么办？</b></summary>

数据在 `%APPDATA%\Kirara\` 下，按账号隔离存放，令牌等敏感字段均已加密，请不要把目录直接拷给别人。设置中心 → 数据管理提供「清空缓存」与「清空本地数据」；后者会删除账户数据、本地缓存、登录页记住的账号和开机自启项，不可撤销，建议先导出实例与令牌。
</details>

<details>
<summary><b>提示插件未安装或版本过旧？</b></summary>

打开「应用商店」，搜索对应插件一键安装或升级，商店会自动探测本机状态。Debug 构建只复用已装的组件，不安装也不卸载；需要安装请使用正式版。
</details>

<details>
<summary><b>断网时还能用吗？</b></summary>

可以。方案页使用本地缓存，认证、评论等远程服务会降级到本地数据作为兜底；恢复联网后自动回到在线同步与实时推送。
</details>

## 相关文档

- [技术栈文档](docs/技术栈文档.md)
- [软件许可协议](docs/软件许可协议.md)
- 手机端：[Kirara_Media](https://gitee.com/kiraramoe/kirara_media)

## 许可证

本软件为闭源专有软件，保留所有权利（All Rights Reserved）。使用前须阅读并同意《Kirara Server Studio 软件许可协议》：软件内展示的版本为权威文本（与 [docs/软件许可协议.md](docs/软件许可协议.md) 逐字一致），英文译本见 [LICENSE](LICENSE)，也可直接阅读 [docs/软件许可协议.en.md](docs/软件许可协议.en.md)。

未经授权，禁止对本软件进行反编译、分发、修改或再发布。软件使用的第三方开源组件版权归其各自作者所有。

## 致谢

- [LiteDB](https://github.com/litedb-org/LiteDB)
- [OpenVPN](https://github.com/OpenVPN)
- [FreeRDP](https://github.com/FreeRDP)
- [QRCoder](https://github.com/codebude/QRCoder)

---

<p align="center">Made with ❤ by SenVenth</p>
