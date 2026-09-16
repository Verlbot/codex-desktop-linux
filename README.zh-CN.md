# ChatGPT Community for Linux — 已退役

[English](README.md) | 简体中文

**Verlbot/codex-desktop-linux 分支已于 2026 年 9 月 16 日退役。**
OpenAI 已提供第一方 Linux 桌面应用。下载、支持的发行版及安装步骤请参阅
[官方 Linux 安装指南](https://learn.chatgpt.com/docs/linux/linux-app)。

此分支不再提供构建、更新、修复或技术支持。GitHub Actions 已禁用，全部八个
工作流定义已移出活动工作流目录。源代码、标签及历史记录保留供参考。
本公告仅适用于此分支，不代表独立维护的上游仓库。

## 迁移与卸载

现有安装**不会自动迁移**至官方应用。

1. 退出 ChatGPT Community（旧版可能名为 ChatGPT Desktop 或 Codex）及官方应用。
   两者共用上游 Codex 用户配置，不要同时运行。
2. 如已安装社区版更新服务，请停止并禁用它：

   ```bash
   systemctl --user disable --now codex-update-manager.service
   ```

   若提示服务不存在，则无需禁用。
3. 使用原安装时的包管理器移除 `codex-desktop`：

   ```bash
   sudo apt remove codex-desktop       # Debian / Ubuntu
   sudo dnf remove codex-desktop       # Fedora
   sudo zypper remove codex-desktop    # openSUSE
   sudo pacman -R codex-desktop        # Arch / Manjaro
   ```

   仅执行适用于当前发行版的一条命令。AppImage 用户删除本地 AppImage 文件；
   Nix 用户从 profile、Home Manager 或 NixOS 配置移除软件包并重新构建；
   仅从仓库运行的用户可在退出应用后删除生成的 `codex-app/` 目录。
4. 保留共用的 Codex 用户配置及 `~/.codex`，包括配置、插件和项目状态。
   迁移时不要删除这些数据。
5. 按照[官方 Linux 指南](https://learn.chatgpt.com/docs/linux/linux-app)
   安装并启动第一方应用。社区专属功能不再受支持。

## 历史参考

[原使用及功能文档](LEGACY.zh-CN.md)、[贡献指南](CONTRIBUTING.md) 以及
`docs/` 和 `linux-features/` 中的文档仅描述已退役的分支。
其中的构建和更新命令仅供历史参考，不再是安装建议。
[已退役的工作流定义](docs/retired-workflows/README.md) 保留在
`.github/workflows/` 之外，作为不会自动执行的参考和测试数据。
