# Ansible role [wordpress](https://galaxy.ansible.com/ui/standalone/roles/buluma/wordpress/documentation)

Install WordPress with webserver (Nginx or Apache2)

|GitHub|Version|Issues|Pull Requests|Downloads|
|------|-------|------|-------------|---------|
|[![github](https://github.com/buluma/ansible-role-wordpress/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-wordpress/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-wordpress.svg)](https://github.com/buluma/ansible-role-wordpress/releases/)|[![Issues](https://img.shields.io/github/issues/buluma/ansible-role-wordpress.svg)](https://github.com/buluma/ansible-role-wordpress/issues/)|[![PullRequests](https://img.shields.io/github/issues-pr-closed-raw/buluma/ansible-role-wordpress.svg)](https://github.com/buluma/ansible-role-wordpress/pulls/)|[![Ansible Role](https://img.shields.io/ansible/role/d/buluma/wordpress)](https://galaxy.ansible.com/ui/standalone/roles/buluma/wordpress/documentation)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/buluma/ansible-role-wordpress/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- hosts: all
  vars:
    ansible_python_interpreter: /usr/bin/python3
    wp_version: 6.0.1
    wp_mysql_db: 'database_name_here'
    wp_mysql_user: 'username_here'
    wp_mysql_password: 'password_here'
    wp_webserver: nginx
    wp_sitename: localhost
    wp_admin_email: 'admin@example.com'
    wp_install_dir: "/var/www/{{ wp_sitename }}"
  roles:
    - buluma.wordpress
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/buluma/ansible-role-wordpress/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: Prepare
  hosts: all
  become: yes
  gather_facts: no

  roles:
    - role: buluma.bootstrap
    - role: buluma.core_dependencies
    - role: buluma.mysql
```

Also see a [full explanation and example](https://buluma.github.io/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/buluma/ansible-role-wordpress/blob/master/defaults/main.yml):

```yaml
---
wp_version: 6.0.1
wp_install_dir: '/var/www/html'
wp_db_name: "{{ wp_mysql_db }}"
wp_db_user: "{{ wp_mysql_user }}"
wp_db_password: "{{ wp_mysql_password }}"
wp_db_host: 'localhost'
wp_db_charset: 'utf8'
wp_db_collate: ''
wp_table_prefix: 'wp_'
wp_debug: false
wp_admin_email: 'admin@example.com'
wp_webserver: nginx
site_name: "{{ wp_sitename }}"
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-wordpress/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | Version |
|-------------|--------|--------|
|[buluma.bootstrap](https://galaxy.ansible.com/buluma/bootstrap)|[![Ansible Molecule](https://github.com/buluma/ansible-role-bootstrap/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-bootstrap/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-bootstrap.svg)](https://github.com/shadowwalker/ansible-role-bootstrap)|
|[buluma.core_dependencies](https://galaxy.ansible.com/buluma/core_dependencies)|[![Ansible Molecule](https://github.com/buluma/ansible-role-core_dependencies/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-core_dependencies/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-core_dependencies.svg)](https://github.com/shadowwalker/ansible-role-core_dependencies)|
|[buluma.mysql](https://galaxy.ansible.com/buluma/mysql)|[![Ansible Molecule](https://github.com/buluma/ansible-role-mysql/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-mysql/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-mysql.svg)](https://github.com/shadowwalker/ansible-role-mysql)|

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:

![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-wordpress/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|[Ubuntu](https://hub.docker.com/repository/docker/buluma/ubuntu/general)|all|
|[Debian](https://hub.docker.com/repository/docker/buluma/debian/general)|stretch, buster, bullseye|

The minimum version of Ansible required is 2.12, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/buluma/ansible-role-wordpress/issues)

## [Changelog](#changelog)

[Role History](https://github.com/buluma/ansible-role-wordpress/blob/master/CHANGELOG.md)

## [License](#license)

[Apache-2.0](https://github.com/buluma/ansible-role-wordpress/blob/master/LICENSE)

## [Author Information](#author-information)

[Shadow Walker](https://buluma.github.io/)

