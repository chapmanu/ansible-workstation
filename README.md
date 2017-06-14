# Ansible Workstation
Playbooks to setup developer workstations and laptops.


## Installation

  1. Ensure Apple's command line tools are installed.
  2. Install Ansible.
  3. Clone this repository to your local drive.
  4. Run `ansible-playbook main.yml --ask-sudo-pass` to run all playbooks

### Running Select Playbooks

To only run select tagged playbooks, use the following command. The `--tags` flag allows you to run any number of tagged playbooks by name. Tag names can be found under `roles:` in `main.yml`.

    ansible-playbook main.yml -i inventory -K --tags "homebrew,github"

### Running Select Tasks

To only run select tasks in a playbook, use the following command:

	ansible-playbook [playbook.yml] --start-at-task="[task name]"

## Configuration
For Atom, you can customize packages to enable, install and disable using the Atom Package Manager tool `apm`. Add commands in `roles/homebrew/vars/main.yml` under `atom_packages`. If you wish to configure the Atom editor styles, create a CSS/Less file and give Ansible the path to the file in `roles/homebrew/vars/main.yml` under `atom_styling_path`.

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

The following locations contain variables that must be set manually:

	- default.config.yml
	- /roles/blogs-setup/vars/main.yml
	- /roles/signage-setup/vars/main.yml
	- /roles/inside-setup/vars/main.yml
	- /roles/homebrew/vars/main.yml

## Manual Steps

### Blogs

Complete the following manual steps after running the `blogs-setup` role.
	
	1. Run `ssh-copy-id chapmanblogs@dev-blogs.chapman.edu` and enter the password provided by a WIM team member.
	2. Run `ssh-copy-id chapmanblogs@blogs.chapman.edu` and enter the password provided by a WIM team member.
	3. Run `rake ensure_db_exists` to create the database if it doesn't exist and pull production data.

### Signage

After running `signage-setup` role, run `bundle exec cap production db:clone` to clone production data.

### Inside

After running `inside-setup` role, run `bundle exec cap production db:clone` to clone production data.
