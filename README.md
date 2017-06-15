# Ansible Workstation
Playbooks to setup developer workstations and laptops.


## Installation

  1. Ensure Apple's command line tools are installed (`xcode-select --install`).
  2. [Install Ansible](http://docs.ansible.com/intro_installation.html).
  3. Clone this repository to your local drive.
  4. Edit the variables in `default.config.yml`. For details, see [Variables](#variables).
  5. Run `ansible-playbook mac-desktop.yml --ask-sudo-pass` to run all playbooks.

### Running Select Playbooks

To only run select tagged playbooks, use the following command. The `--tags` flag allows you to run any number of tagged playbooks by name. Tag names can be found under `roles:` in `mac-desktop.yml`.

    ansible-playbook mac-desktop.yml -i inventory -K --tags "rails"

## Versions

After running the Homebrew role, versions of installed packages can be checked using `brew info [package name]`. For homebrew casks, the command is `brew cask info [cask name]`.

- Homebrew 1.2.3
- Elasticsearch 2.4
- PHP 7.0
- Ruby 2.1.10, 2.2.1
- Rbenv 1.1.0
- Redis 3.2.9
- PostgreSQL 9.6.3
- MySQL 5.7.18
- PHPUnit 6.1.4
- PhantomJS 2.1.1
- Chromedriver 2.30
- GraphicsMagick 1.3
- Atom 1.17
- Java 8

## Variables

The `default.config.yml` file has variables that must be customized before running the playbook. There are additional variables in `/roles/homebrew/vars/main.yml` that can be changed if you want to install Homebrew in a custom directory instead of the default.

For Atom, you can customize packages to enable, install and disable using the Atom Package Manager tool `apm`. Add commands in `default.config.yml` under `atom_packages`. If you wish to configure the Atom editor styles, create a CSS/Less file and give Ansible the path to the file in `default.config.yml` under `atom_styling_path`.

## Manual Steps

- Although the `sudo` password is entered at the start of the script, there are some points when the script is running that it may pause and ask for the user's password again if it times out for some reason.
- When running the `github` role, it will likely prompt the user for a Github username and password in order to clone the private repositories, `chapmanu/blogs` and `chapmanu/inside`.
- All SSH keys being used must be manually copied to remote servers and any other services that use them.
