# ansible-ssh-config

[![Ansible Galaxy](http://img.shields.io/badge/galaxy-whiskerlabs.ssh--config-660198.svg)](https://galaxy.ansible.com/list#/roles/6647)

An Ansible role for installing a system-wide SSH configuration.

This role installs a templatized `/etc/ssh/ssh_config` file based
according to values defined in `defaults/main.yml`.

## Installation

To install from Ansible Galaxy:

    $ ansible-galaxy install whiskerlabs.ssh-config

Or alternatively, add the path to a local copy of this repository to
`roles_path` within your project's `ansible.cfg` file:

    roles_path = /path/to/role_dir

where `/path/to/role_dir` is a parent directory of
`armsible-ssh-config`.

Consult
[Ansible documentation](http://docs.ansible.com/intro_configuration.html)
for more info on how to configure `roles_path` in an Ansible
configuration file.

## Usage

`ssh_config` sections are defined via the `ssh_config_host_configs`
role variable. This variable must be a list of dictionaries containing
key:value pairs corresponding to `ssh_config` options.

Example:

    ssh_config_host_configs:
      - host: "*"
        HashKnownHosts: "yes"
        GSSAPIAuthentication: "yes"
        GSSAPIDelegateCredentials: "no"
      - host: example.com
        ServerAliveInterval: 300
        ServerAliveCountMax: 2

`ssh_config_host_configs` defaults to an empty list, and thus an empty
`ssh_config` is installed unless the variable is populated.

## Requirements

`armsible-ssh-config` has no role dependencies and should work with
BBBs running any version of Linux.

## Role Variables

See documentation in `defaults/main.yml`.

## License

Copyright 2015 Whisker Labs

Licensed under the MIT License. See `LICENSE` for details.
