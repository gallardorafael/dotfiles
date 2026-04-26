# Dotfiles
To set up the dotfiles in a new machine, you can run the following one-liner to install chezmoi and apply a the dotfiles of a repo with:

    sh -c "$(curl -fsLS get.chezmoi.io)" -- init --apply $GITHUB_USERNAME

in this case:

    GITHUB_USERNAME=https://github.com/gallardorafael/dotfiles

# Ansible

## Linux (PopOS / Ubuntu)

In order to setup a new machine with this configuration, you need to install Ansible and run the playbook. To install Ansible, you can use pipx:

    sudo apt install pipx

And then install Ansible:

    pipx install ansible-core

Once Ansible is installed, you can run the playbook by:

    ansible-playbook <ansible path>/linux_ansible/setup_local_env.yaml --ask-become-pass

---

## macOS (Apple Silicon M4)

The `mac_ansible/` playbook is tailored for a MacBook Pro with Apple Silicon (M4). It uses **Homebrew** as the primary package manager and avoids all `apt`/PPA/snap/AppImage mechanics.

### Prerequisites

1. **Xcode Command Line Tools** — required before Homebrew can be installed:

       xcode-select --install

2. **pipx** — used to install Ansible in an isolated environment. Once Homebrew is available (the playbook installs it, but you need it to bootstrap Ansible first):

       brew install pipx
       pipx ensurepath

3. **Ansible** and the Homebrew collection:

       pipx install ansible-core
       ansible-galaxy collection install community.general

### Running the playbook

    ansible-playbook <ansible path>/mac_ansible/setup_local_env.yaml --ask-become-pass

