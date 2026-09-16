# ChatGPT Community for Linux — retired

English | [简体中文](README.zh-CN.md)

The **Verlbot/codex-desktop-linux fork is retired as of September 16, 2026**.
OpenAI now provides a first-party Linux desktop app. Use the
[official Linux installation guide](https://learn.chatgpt.com/docs/linux/linux-app)
for downloads, supported distributions, and installation instructions.

This fork no longer provides builds, updates, fixes, or support. GitHub Actions
are disabled and all eight workflow definitions have been removed from the
active workflow directory. Source, tags, and history are retained for reference.
This notice applies to this fork, not to the independently managed upstream repository.

## Migrate / uninstall

Existing installations do **not** automatically migrate to the official app.

1. Close ChatGPT Community (older builds may be named ChatGPT Desktop or Codex)
   and the official app. Do not run both together: they share the upstream Codex profile.
2. If installed, stop and disable the Community updater:

   ```bash
   systemctl --user disable --now codex-update-manager.service
   ```

   A missing service means there is no service to disable.
3. Remove `codex-desktop` using the package manager that installed it:

   ```bash
   sudo apt remove codex-desktop       # Debian / Ubuntu
   sudo dnf remove codex-desktop       # Fedora
   sudo zypper remove codex-desktop    # openSUSE
   sudo pacman -R codex-desktop        # Arch / Manjaro
   ```

   Run only the command for your distribution. For AppImage, delete the local
   AppImage. For Nix, remove the package from your profile, Home Manager, or
   NixOS configuration and rebuild. For a repository-only installation, remove
   its generated `codex-app/` directory after closing the app.
4. Preserve your shared Codex user profile and `~/.codex`, including configuration,
   plugins, and project state. Do not delete them as part of this migration.
5. Follow the [official Linux guide](https://learn.chatgpt.com/docs/linux/linux-app)
   to install and launch the first-party app. Community-only features are unsupported.

## Historical reference

[Previous usage and feature documentation](LEGACY.md), [contribution guidance](CONTRIBUTING.md),
and the documents under `docs/` and `linux-features/` describe the retired fork.
Their build and update commands are historical, not installation recommendations.
The [retired workflow definitions](docs/retired-workflows/README.md) are inert
reference fixtures outside `.github/workflows/`.
