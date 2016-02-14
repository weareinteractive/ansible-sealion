# Ansible weareinteractive.sealion role

[![Build Status](https://img.shields.io/travis/weareinteractive/ansible-sealion.svg)](https://travis-ci.org/weareinteractive/ansible-sealion)
[![Galaxy](http://img.shields.io/badge/galaxy-weareinteractive.sealion-blue.svg)](https://galaxy.ansible.com/weareinteractive/sealion)
[![GitHub Tags](https://img.shields.io/github/tag/weareinteractive/ansible-sealion.svg)](https://github.com/weareinteractive/ansible-sealion)
[![GitHub Stars](https://img.shields.io/github/stars/weareinteractive/ansible-sealion.svg)](https://github.com/weareinteractive/ansible-sealion)

> `weareinteractive.sealion` is an [Ansible](http://www.ansible.com) role which:
>
> * installs sealion
> * configures service

**Note:**

> Since Ansible Galaxy supports [organization](https://www.ansible.com/blog/ansible-galaxy-2-release) now, this role has moved from `franklinkim.sealion` to `weareinteractive.sealion`!

## Installation

Using `ansible-galaxy`:

```shell
$ ansible-galaxy install weareinteractive.sealion
```

Using `requirements.yml`:

```yaml
- src: weareinteractive.sealion
```

Using `git`:

```shell
$ git clone https://github.com/weareinteractive/ansible-sealion.git weareinteractive.sealion
```

## Dependencies

* Ansible >= 2.0

## Variables

Here is a list of all the default variables for this role, which are also available in `defaults/main.yml`.

```yaml
---

# sealion key
sealion_key:
# sealion version
sealion_version: 3.0.10
# start on boot
sealion_service_enabled: yes
# current state: started, stopped
sealion_service_state: started
```

## Handlers

These are the handlers that are defined in `handlers/main.yml`.

```yaml
---

- name: restart sealion
  service:
    name: sealion
    state: restarted
  when: sealion_service_state != 'stopped'

```


## Usage

This is an example playbook:

```yaml
---

- hosts: all
  roles:
    - franklinkim.sealion
  vars:
    sealion_service_state: stopped
    sealion_service_enabled: no
    sealion_key: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx

```

## Testing

```shell
$ git clone https://github.com/weareinteractive/ansible-sealion.git
$ cd ansible-sealion
$ vagrant up
```

## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests and examples for any new or changed functionality.

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

*Note: To update the `README.md` file please install and run `ansible-role`:*

```shell
$ gem install ansible-role
$ ansible-role docgen
```

## License
Copyright (c) We Are Interactive under the MIT license.
