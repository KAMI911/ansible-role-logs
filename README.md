# Ansible Role: Configure default log rotations

Configure default log rotations using compression.

[![Build Status](https://travis-ci.org/KAMI911/ansible-role-logs.svg?branch=master)](https://travis-ci.org/KAMI911/ansible-role-logs)

## Table of Contents

1. [Requirements][Requirements]
2. [Installation][Installation]
3. [Role Variables][Role Variables]
4. [Dependencies][Dependencies]
5. [Example Playbook][Example Playbook]
6. [Licensing][Licensing]
7. [Author Information][Author Information]
8. [Support][Support]
9. [Contributing][Contributing]
10. [Donation][Donation]

## Requirements

None.

## Installation

    ansible-galaxy install kami911.logs

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

### Installation releted options

    logs_syslog_name: 'syslog'



    logs_syslog_rotate_days: 200



    logs_syslog_rotate_minsize: 20K

Log files are rotated when they grow bigger than size bytes, but not before the additionally
specified time interval (daily, weekly, monthly, or yearly). The related size option is
 similar except that it is mutually exclusive with the time interval options, and it causes
log files to be rotated without regard for the last rotation time. When minsize is used,
both the size and timestamp of a log file are considered.

    logs_syslog_compress_cmd: '/usr/bin/xz'

Location is the compressor program. Default is xz so the dafault value is '/usr/bin/xz'.
You can also use for example: '/usr/bin/gzip'.

    logs_syslog_compress_options: '-9e'

Options for compression program. For xz the default is '-9e' that means maximum compression.
For gzip íou can use for example: '-9'.

    logs_syslog_compress_ext: .xz

File extension for logrotate specification. xz is '.xz', and gzip is 'gz'.

    logs_syslog_logs:
      - '/var/log/cron'
      - '/var/log/maillog'
      - '/var/log/messages'
      - '/var/log/secure'
      - '/var/log/spooler'

Log files taht is included in syslog log rotations.

    logs_package_manager_name: 'yum'



    logs_package_manager_rotate_days: 200



    logs_package_manager_rotate_minsize: 20K



    logs_package_manager_compress_cmd: '{{ logs_syslog_compress_cmd }}'

Location is the compressor program. Default is xz so the dafault value is '/usr/bin/xz'.
You can also use for example: '/usr/bin/gzip'.

    logs_package_manager_compress_options: '{{ logs_syslog_compress_options }}'

Options for compression program. For xz the default is '-9e' that means maximum compression.
For gzip íou can use for example: '-9'.

    logs_package_manager_compress_ext: '{{ logs_syslog_compress_ext }}'

File extension for logrotate specification. xz is '.xz', and gzip is 'gz'.

    logs_package_manager_logs:
      - '/var/log/yum.log'

Log files taht is included in package manager log rotations.

    logs_logrotate_d_dir: '/etc/logrotate.d'

## Dependencies

None.

## Example Playbook

    - hosts: all
      roles:
        - logs

## Licensing

The Logs Ansible Role application and documantations are licensed under the terms of
the MIT / BSD, you will find a copy of this license in the
[LICENSE](LICENSE) file included in the source package.

## Author Information

This role was created in 2020 by Kálmán Szalai - KAMI

## Support

If you have any question, do not hesitate and drop me a line.
If you found a bug, or have a feature request, you can [fill an issue](https://github.com/KAMI911/ansible-role-logs/issues).

### Using as a submudule of an AWX playbook

#### Add as a submodule

```
git submodule add --force git@github.com:KAMI911/ansible-role-logs.git roles/logs
```

#### Update as sumodule

Update only this submodule

```
git submodule update --remote roles/logs/
```

Update all submodules:

```
git submodule foreach git pull origin master
```

## Contributing

There are many ways to contribute to ansible-role-logs -- whether it be sending patches,
testing, reporting bugs, or reviewing and updating the documentation. Every
contribution is appreciated!

Please continue reading in the [contributing chapter](CONTRIBUTING.md).

### Fork me on Github

https://github.com/KAMI911/ansible-role-logs

Add a new remote `upstream` with this repository as value.

```
git remote add upstream https://github.com/KAMI911/ansible-role-logs.git
```

You can pull updates to your fork's master branch:

```
git fetch --all
git pull upstream HEAD
```

## Donation

If you find this useful, please consider a donation:

[![paypal](https://www.paypalobjects.com/en_US/i/btn/btn_donateCC_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=RLQZ58B26XSLA)

<!-- TOC URLs -->
[Requirements]: #requirements
[Installation]: #installation
[Role Variables]: #role_variables
[Dependencies]: #dependencies
[Example Playbook]: #example_playbook
[Licensing]: #licensing
[Author Information]: #author_information
[Support]: #support
[Contributing]: #contributing
[Donation]: #donation
