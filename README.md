ruby-mac
=========

[![Galaxy Role][badge-role]][link-galaxy]
[![MIT Licensed][badge-license]][link-license]

An ansible role to install RVM and Ruby on MacOS.

Requirements
------------

RVM uses GPG for [signing](https://rvm.io/rvm/security).
`gnupg` is required to verify the RVM installation. It can be easily installed via homebrew:

`brew install gpg`

Role Variables
--------------

### Defaults
    ruby_version: 2.6.5
The version of Ruby that will be installed via RVM.

    make_default_ruby: true
Set this variable to make the newly installed Ruby your system default.
**Note**: After running a playbook with this role, it's recommended to restart your terminal session.

    ruby_gems
The list of Ruby gems that will be installed on your Mac.
**Note**: Since Ruby was installed with RVM, $GEM_HOME is set to your user home folder, i.e. `/Users/martianplatypus/.rvm/gems/ruby-2.6.5`. The whole Ruby installation including gems will be done under the current user $HOME path.


### Variables
    rvm_installer_script: "{{ ansible_env.HOME }}/install-rvm.sh"
Path to Rvm installer script

    gpg_path: "/usr/local/bin/gpg"
Path to gpg binary.

    gpg_keyserver: "hkp://pool.sks-keyservers.net"
GPG key server used to import the keys

    gpg_key_1: 409B6B1796C275462A1703113804BB82D39DC0E3
    gpg_key_2: 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
RVM maintainers keys:
* `gpg_key_1` -> mpapis
* `gpg_key_2` -> pkuczynski

Dependencies
------------

None.

Example Playbook
----------------

- hosts: localhost
  roles:
     - role: ansible-role-ruby-mac

[badge-role]: https://img.shields.io/ansible/role/47589.svg?style=flat-square
[badge-license]: https://img.shields.io/github/license/martianplatypus/ansible-role-ruby-mac
[badge-travis]: https://img.shields.io/travis/com/martianplatypus/ansible-role-ruby-mac
[link-galaxy]: https://galaxy.ansible.com/martianplatypus/ruby_mac/
[link-license]: https://github.com/martianplatypus/ansible-role-ruby-mac/blob/master/LICENSE
[link-travis]: https://travis-ci.com/github/martianplatypus/ansible-role-ruby-mac/
