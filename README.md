# Dotfiles
To set up the dotfiles in a new machine, you can run the following one-liner to install chezmoi and apply a the dotfiles of a repo with:

    sh -c "$(curl -fsLS get.chezmoi.io)" -- init --apply $GITHUB_USERNAME

in this case:

    GITHUB_USERNAME=https://github.com/gallardorafael/dotfiles

# Ansible

In order to setup a new machine with this configuration, you need to install Ansible and run the playbook. To install Ansible, you can use pipx:

    sudo apt install pipx

And then install Ansible:

    pipx install ansible-core


Once Ansible is installed, you can run the playbook by:

    ansible-playbook ansible/setup_local_env.yaml --ask-become-pass

