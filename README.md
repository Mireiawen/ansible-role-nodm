[![Build Status](https://travis-ci.com/Mireiawen/ansible-role-nodm.svg?branch=master)](https://travis-ci.com/Mireiawen/ansible-role-nodm) [![Ansible Galaxy](https://img.shields.io/badge/Ansible%20Galaxy-mireiawen.nodm-blueviolet)](https://galaxy.ansible.com/mireiawen/nodm)

# nodm

Installs the nodm display manager that automatically logs user in without interaction, usable for example in kiosk mode.

Note that the package is no longer maintained and as such may not be available in some of the latest distributions.

*Note* that this package does not set the used display manager. On some systems you can change it by changing the running service, on Debian -based systems you will need to run `dpkg-reconfigure nodm --priority high` and answer the questions.

## Requirements

EPEL repository is needed on Red Hat and CentOS and based distributions. You can use for example [Ansible Role: EPEL Repository](https://galaxy.ansible.com/geerlingguy/repo-epel)

## Role Variables
| Variable                | Type   | Default value       | Description                                              |
|-------------------------|--------|---------------------|----------------------------------------------------------|
| `nodm_package`          | string | `nodm`              | The name of the nodm package.                            |
| `nodm_state`            | string | `latest`            | The status of the nodm package.                          |
| `nodm_enabled`          | string | `true`              | Should the nodm be enabled in config.                    |
| `nodm_user`             | string | `root`              | The user to log in automatically.                        |
| `nodm_first_vt`         | int    | 7                   | First VT to try when looking for free VTs                |
| `nodm_xsession`         | string | `/etc/X11/Xsession` | X session.                                               |
| `nodm_options`          | string | empty               | Options for nodm itself.                                 |
| `nodm_x_options`        | string | `'-nolisten tcp'`   | Options for the X server.                                |
| `nodm_min_session_time` | int    | 60                  | Restart the X session if it runs less than this time.    |
| `nodm_x_timeout`        | int    | 300                 | Timeout to wait for X to be ready to accept connections. |

## Dependencies

None.

## Example Playbook

```
- hosts: "kiosks"
  roles:
  - "mireiawen.nodm"
```

## License
MIT, see `LICENSE`
