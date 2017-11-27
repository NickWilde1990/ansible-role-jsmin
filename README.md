Ansible Role: JSMin
=========

Build and install the [jsmin PHP Extension](https://github.com/sqmk/pecl-jsmin/) on any Ubuntu or (probably) Debian based system.
This extension provides a fast JavaScript minification function.

Requirements
------------

- Debian/Ubuntu
- Git. A role such as [geerlingguy.git](https://galaxy.ansible.com/geerlingguy/git/) can supply this.
- PHP
- PHP Development headers installed for any PHP version(s) you want to target.


Role Variables
--------------

    jsmin_php_version

The PHP version to target with this build/install. If not provided, will attempt to select your primary version.

    jsmin_clone_dest: ~/git/jsmin

The location that jsmin will be cloned to for building.

    jsmin_enable: true

Whether or not to enable the jsmin module after building & installing.

    jsmin_path_ini: /etc/php/{{ jsmin_php_version }}/mods-available/jsmin.ini

The ini path to use to create the jsmin.ini if enabling jsmin.

    jsmin_path_phpconfig: php-config{{ jsmin_php_version }}

The path to the php-config binary.

    jsmin_path_phpize: phpize{{ jsmin_php_version }}

The path to the phpize binary.

Example Playbook
----------------

To  install `jsmin` for just your primary PHP version:

    - hosts: all
      roles:
        -role: nickwilde1990.jsmin

To install `jsmin` for multiple PHP versions.

    - hosts: all
      tasks:
      - include_role:
        name: nickwilde1990.jsmin
      with_items:
        - 7.0
        - 7.1
      loop_control:
        loop_var: jsmin_php_version

License
-------

MIT

Author Information
------------------

Nick Wilde ([BriarMoon Design](https://design.briarmoon.ca))