# Ansible Workstation
Playbooks to setup developer workstations and laptops.


## Installation

  1. Ensure Apple's command line tools are installed.
  2. Install Ansible.
  3. Clone this repository to your local drive.
  4. Run `ansible-playbook main.yml --ask-sudo-pass` to run all playbooks

### Running Select Playbooks

To only run select tagged playbooks, use the following command. The `--tags` flag allows you to run any number of tagged playbooks by name.

    ansible-playbook main.yml -i inventory -K --tags "homebrew,github"

## Configuration
For Atom, you can customize packages to enable, install and disable using the Atom Package Manager tool `apm`. Add commands in `roles/homebrew/vars/main.yml` under `atom_packages`. If you wish to configure the Atom editor styles, create a CSS/Less file and give Ansible the path to the file in `roles/homebrew/vars/main.yml` under `atom_styling_path`.

## Versions