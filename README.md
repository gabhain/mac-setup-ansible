# macOS Automation Playbook

This Ansible playbook automates the setup and configuration of a macOS environment.

## Features

- **Homebrew Management**: Installs Homebrew itself, Taps, Formulae, and Casks.
- **Mac App Store (MAS)**: Installs App Store apps using the `mas` CLI.
- **macOS System Settings**: Configures Finder, Dock, and other system defaults.
- **Dotfiles & Shell**: Symlinks `.zshrc` and `.gitconfig` from the repo, installs Oh My Zsh, and configures plugins.
- **RCM**: Automatically runs `rcup` to manage your dotfiles.
- **Development Ecosystems**:
  - **VS Code**: Installs all your favorite extensions.
  - **Rust/Cargo**: Installs Rustup and specific Cargo packages.
  - **Python**: Manages `pipx` packages and updates global `pip3` packages.
  - **Node.js**: Installs global `npm` packages.
  - **PHP**: Updates global `composer` packages.
  - **PowerShell**: Updates all installed PowerShell modules.
  - **TLDR**: Automatically updates the `tldr` cache.
- **Application Configurations**:
  - **Go**: Installs Go and configures GOPATH and GOBIN in Zsh.
  - **Neofetch & Fastfetch**: Backs up and restores your custom system-info display themes.
  - **iTerm2**: Backs up and restores your iTerm2 preferences (plist).
  - **Topgrade**: Backs up and restores your cross-platform update manager configuration.

## Prerequisites

- **Homebrew**: If not already installed, the playbook will attempt to install it.
- **Ansible**: Must be installed on your machine (`brew install ansible`).
- **Mac App Store**: You must be signed into the App Store for `mas` to install apps.

## Usage

1. **Clone the repository**:
   ```bash
   git clone https://github.com/yourusername/mac-setup-ansible.git
   cd mac-setup-ansible
   ```

2. **Customize your configuration**:
   Edit `group_vars/all.yml` and `group_vars/apps_extra.yml` to adjust the lists of apps, tools, and system settings.

3. **Run the playbook**:
   ```bash
   ansible-playbook main.yml --ask-become-pass
   ```
   *(The `--ask-become-pass` flag is required for tasks that need sudo privileges.)*

## Customization

You can modify the following in `group_vars/`:
- `homebrew_taps`: Homebrew repositories to tap.
- `homebrew_installed_packages`: CLI tools to install.
- `homebrew_cask_apps`: GUI applications to install via Homebrew Cask.
- `mas_installed_apps`: App Store applications to install (requires ID).
- `macos_defaults`: Key-value pairs for `defaults write` settings.
- `vscode_extensions`: List of VS Code extensions to install.
- `pipx_packages`: List of pipx packages.
- `npm_global_packages`: List of global npm packages.
- `cargo_packages`: List of cargo packages.

## License
MIT
