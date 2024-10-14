# ansible-pyenv

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Ansible role to install and configure [pyenv](https://github.com/yyuu/pyenv) on Linux Systems.

## Requirements

None

## Role Variables

Here is the list of all variables and their default values:

* ``pyenv_env: "user"`` (should be either `"user"` or `"system"`)
* ``pyenv_path: "{% if pyenv_env == 'user' %}{{ ansible_env.HOME }}/pyenv{% else %}/usr/local/pyenv{% endif %}"``
* ``pyenv_owner: "{{ ansible_env.USER }}"``
* ``pyenv_python_versions: ["3.4.1"]``
* ``pyenv_virtualenvs: [{ venv_name: "latest", py_version: "3.4.1" }]``
* ``pyenv_global: "3.4.1"``
* ``pyenv_update_git_install: no``
* ``pyenv_enable_autocompletion: no``
* ``pyenv_setting_path: "{% if pyenv_env == 'user' %}~/.bashrc{% else %}/etc/profile.d/pyenv.sh{% endif %}"``

## Dependencies

None

## Example Playbook

```yaml
    - hosts: servers
      roles:
        - role: jeffreyjs.pyenv
          pyenv_path: "{{ lookup('ansible.builtin.env', 'HOME') }}/pyenv"
          pyenv_owner: "{{ lookup('ansible.builtin.env', 'USER') }}"
          pyenv_global: "3.11.10"
          pyenv_update_git_install: no
          pyenv_enable_autocompletion: no
          pyenv_python_versions:
            - "3.11.10"
            - "3.10.15"
            - "3.9.20"
          pyenv_virtualenvs:
            - venv_name: "latest_v3"
              py_version: "3.12.7"
```

## License

MIT / BSD

## Author Information

[Jeffrey Swindel](https://github.com/jeffreyjs)
