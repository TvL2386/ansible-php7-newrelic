# Ansible tvl2386.php7-newrelic role

> `tvl2386.php7-newrelic` is an [Ansible](http://www.ansible.com) role, forked from [franklinkim.php5-newrelic](https://github.com/weareinteractive/ansible-php5-newrelic) v1.2.2 which:
>
> * installs newrelic php agent
> * configures newrelic php agent

## Installation

Using `ansible-galaxy`:

```shell
$ ansible-galaxy install tvl2386.php7-newrelic
```

Using `requirements.yml`:

```yaml
- src: tvl2386.php7-newrelic
```

Using `git`:

```shell
$ git clone https://github.com/tvl2386/ansible-php7-newrelic.git tvl2386.php7-newrelic
```

## Dependencies

* Ansible >= 2.0

## Variables

Here is a list of all the default variables for this role, which are also available in `defaults/main.yml`.

```yaml
---
# newrelic_license_key: yourkey

# Sets the name of the file to send log messages to.
php7_newrelic_logfile: /var/log/newrelic/php_agent.log
# Sets the level of detail to include in the log file.
php7_newrelic_loglevel: info
# Sets the name of the file to send daemon log messages to.
php7_newrelic_daemon_logfile: /var/log/newrelic/newrelic-daemon.log
# Sets the level of detail to include in the daemon log.
php7_newrelic_daemon_loglevel: info
# Enables high security for all applications.
php7_newrelic_high_security: no
# Sets the name of the application that metrics will be reported into.
php7_newrelic_appname: myapp
# Sets the desination location of the newrelic.ini file
php7_newrelic_config_dest: /etc/php7/mods-available
# Sets wether apache, in this case, should be restarted
php7_newrelic_php_daemon_notify: no
php7_newrelic_php_daemon_notify_handler: restart apache

```


## Usage

This is an example playbook:

```yaml
---

- hosts: all
  roles:
    - geerlingguy.apache
    - geerlingguy.php
    - franklinkim.newrelic
    - tvl2386.php7-newrelic
  vars:
    newrelic_license_key: ab2fa361cd4d0d373833cad619d7bcc424d27c16
    php7_newrelic_appname: "My App"
    php7_newrelic_php_daemon_notify: yes
    php7_newrelic_php_daemon_notify_handler: restart apache

```


## Contributing
In lieu of a formal style guide, take care to maintain the existing coding style. Add unit tests and examples for any new or changed functionality.

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

## License
Copyright (c) TvL2386 under the MIT license.
