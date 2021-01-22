# Ansible role for HedgeDoc

Ansible role for installing and configuring HedgeDoc without Docker

## Requirements

* Node.js (for example with [geerlingguy.nodejs](https://github.com/geerlingguy/ansible-role-nodejs))
* Yarn package manager (for example with [ocha.yarn](https://github.com/ocha/ansible-role-yarn))

## Role Variables

### General (required)
| Variable Name | Function | example value |
| ------------- | -------- | ------- |
| `hedgedoc_domain` | Main domain of HedgeDoc | `hedgedoc.example.org` |
| `hedgedoc_session_secret` | Cookie session secret used to sign the session cookie | `ThisIsSecret!Do_not_useMe` |

### Database (required)
| Variable Name | Function | default | comment |
| ------------- | -------- | ------- | ------- |
| `hedgedoc_db_dialect` | Dialect of the database | `postgres` | one of `mysql`, `postgres`, `sqlite` and `mssql` |
| `hedgedoc_db_host` | Host the database is running on | `localhost` | |
| `hedgedoc_db_username` | Username of the database | `hedgedoc` | |
| `hedgedoc_db_password` | Password of the database user |  | |
| `hedgedoc_db_port` | Port of the database server | `localhost` | |
| `hedgedoc_db_storage` | Path to the sqlite file | | (only required and used when using sqlite) |

### General (optional)
| Variable Name | Function | default | comment |
| ------------- | -------- | ------- | ------- |
| `hedgedoc_version` | Version of HedgeDoc that will be installed | `1.7.2` | |
| `hedgedoc_source` | Path to pre-compiled HedgeDoc archive | `https://github.com/hedgedoc/hedgedoc/releases/download/{{ hedgedoc_version }}/hedgedoc-{{ hedgedoc_version }}.tar.gz` | |
| `hedgedoc_base_path` | Base path of HedgeDoc installation | `/opt/hedgedoc` | |
| `hedgedoc_user` | Linux user that will be used/created for HedgeDoc | `hedgedoc` | |
| `hedgedoc_group` | Linux main group for the user specified in `hedgedoc_user` | `hedgedoc` | |
| `hedgedoc_port` | Port HedgeDoc will listen on | `3000` | |
| `hedgedoc_allowed_origins` | Domain name whitelist | `[ "{{ hedgedoc_domain }}" ]` | |
| `hedgedoc_upload_type` | Where to upload images | `filesystem` | |
| `hedgedoc_loglevel` | Kinds of log HedgeDoc will output to stdout | `warn` | one of `debug`, `verbose`, `info`, `warn` and `error` |
| `hedgedoc_additional_config` | Plain text block added to the configuration file | | |

### Security (optional)
| Variable Name | Function | default | comment |
| ------------- | -------- | ------- | ------- |
| `hedgedoc_hsts_enable` | Enable [HSTS](https://en.wikipedia.org/wiki/HTTP_Strict_Transport_Security) | `true` | |
| `hedgedoc_csp_enable` | Enable [CSP](https://en.wikipedia.org/wiki/Content_Security_Policy) | `true` | |

### Login and privileges (optional)
| Variable Name | Function | default | comment |
| ------------- | -------- | ------- | ------- |
| `hedgedoc_allow_email_login` | Enable Login with E-Mail | `true` | |
| `hedgedoc_allow_email_register` | Enable Registration (on web-interface) with E-Mail | `true` | |
| `hedgedoc_allow_free_url` | Allow creating notes by accessing a non-existent note url | `true` | |
| `hedgedoc_allow_anonymous` | Allow anonymous (not logged in) access | `true` | |
| `hedgedoc_allow_anonymous_edits` | Allow users to set note permission to `freely` to allow not logged in users editing notes | `true` | |

## Dependencies
This role does not have any dependencies.

## License

MIT
