# Ansible Sealion Role

[![Build Status](https://travis-ci.org/weareinteractive/ansible-sealion.png?branch=master)](https://travis-ci.org/weareinteractive/ansible-sealion)
[![Stories in Ready](https://badge.waffle.io/weareinteractive/ansible-sealion.svg?label=ready&title=Ready)](http://waffle.io/weareinteractive/ansible-sealion)

> `sealion` is an [ansible](http://www.ansible.com) role which: 
> 
> * installs sealion
> * configures service

## Installation

Using `ansible-galaxy`:

```
$ ansible-galaxy install franklinkim.sealion
```

Using `arm` ([Ansible Role Manager](https://github.com/mirskytech/ansible-role-manager/)):

```
$ arm install franklinkim.sealion
```

Using `git`:

```
$ git clone https://github.com/weareinteractive/ansible-sealion.git
```

## Variables

Here is a list of all the default variables for this role, which are also available in `defaults/main.yml`.

```
# ports to listen to
apache2_ports: [80]
# ssl ports to listen to
apache2_ssl_ports: [443]
# addresses to listen to (2.2  only)
apache2_listen_addresses: ['*']
# enabled/disabled modules
apache2_modules: []
# enabled/disabled confs
apache2_confs: []
# enabled/disabled sites
apache2_sites: []
# remove the default host
apache2_remove_default: no
# start on boot
apache2_service_enabled: yes
# current state: started, stopped
apache2_service_state: started
# set to one of:  Full | OS | Minimal | Minor | Major | Prod
apache2_server_tokens: Prod
# set to one of:  On | Off | EMail
apache2_server_signiture: 'Off'
# set to one of:  On | Off | extended
apache2_trace_enable: 'Off'
```

Module and confs might be defined through:

```
# sealion key
sealion_key:
# sealion version
sealion_version: 3.0.10
# start on boot
apache2_service_enabled: yes
# current state: started, stopped
apache2_service_state: started
```

## Handlers

These are the handlers that are defined in `handlers/main.yml`.

* `restart sealion` 

These can be included into your site definitions.

## Example playbook

```
- host: all
  roles:
    - franklinkim.sealion
  vars:
    sealion_key: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
```

## Testing

```
$ git clone https://github.com/weareinteractive/ansible-apache2.git
$ cd ansible-apache2
$ vagrant up
```

## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests and examples for any new or changed functionality.

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

## License
Copyright (c) We Are Interactive under the MIT license.
