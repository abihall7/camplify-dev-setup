# camplify-dev-setup

Configures and installs required software for a dev team setup.

## Ansible

Ansible is an open-source automation tool that simplifies the deployment, configuration, and management of IT infrastructure. It allows system administrators to automate repetitive tasks, such as software installation, system configuration, and application deployment, using a simple and human-readable language. Ansible also provides features for role-based access control, task delegation, and reporting, making it a popular choice for managing complex IT environments.

The use case here is for the local dev machine setup which is completed by the cloning of this repo and running locally, rather than configuration to the managed hosts via SSH or WinRM.

## Installation

1. Ensure Apple's command line tools are installed (xcode-select --install to launch the installer).
2. [Install Ansible](https://docs.ansible.com/ansible/latest/installation_guide/index.html):

    1. Run the following command to add Python 3 to your $PATH: `export PATH="$HOME/Library/Python/3.9/bin:/opt/homebrew/bin:$PATH"`
    2. Upgrade Pip: sudo `pip3 install --upgrade pip`
    3. Install Ansible: `pip3 install ansible`

3. Clone this repository
4. Run `ansible-galaxy install -r requirements.yml` inside this directory to install required Ansible roles.
5. Run `ansible-playbook main.yml --ask-become-pass` inside this directory. Enter your macOS account password when prompted for the 'BECOME' password.

### Running a specific set of tagged tasks

You can filter which part of the provisioning process to run by specifying a set of tags using `ansible-playbook`'s `--tags` flag. The tags available are `dotfiles`, `homebrew`, `mas`, `extra-packages` and `osx`.

    ansible-playbook main.yml -K --tags "dotfiles,homebrew"

