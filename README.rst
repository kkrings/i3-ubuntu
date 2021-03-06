Ansible roles
=============

This repository contains a collection of Ansible_ roles for configuring my
personal hosts.

Installation
------------

First, Ansible is installed inside its own virtual Python environment via the
virtualenvwrapper_ script::

    sudo aptitude install virtualenvwrapper
    source /usr/share/virtualenvwrapper/virtualenvwrapper.sh
    mkvirtualenv --python=/usr/bin/python3 -i ansible py3-ansible

Now, the project is installed via::

    sudo aptitude install git
    git clone https://github.com/kkrings/ansible-roles.git roles

Example: Ubuntu with custom desktop environment
-----------------------------------------------

Starting point is a Ubuntu 18.04 `minimal iso image`_. An exemplary Ansible
playbook, `desktop.yml`, for installing my custom desktop environment looks
like::

    ---
    - name: Install my custom desktop environment
      hosts: `put a hostname here`
      roles:
          - desktop
          - prezto
          - neovim
          - pass

The environment is installed and configured from inside the ``py3-ansible``
environment via::

    ansible-playbook -i `path to hosts file` --ask-become-pass --vault-id @prompt desktop.yml

After a reboot, you should end up in a graphical LightDM session.

The custom desktop environment consists of:

* Window manager: i3_
* Display manager: LigthDM
* Terminal emulator: LXTerminal
* Shell: Zsh
* Editor: Neovim_
* Web browser: Chromium_
* Document viewer: zathura_
* Password manager: pass_

The shell is configured based on the Prezto_ configuration framework. Whenever
possible, the gruvbox_ dark color scheme and the Hack_ font are used for
applications in the terminal. The Numix theme and the DejaVu Sans font are used
for GTK+ applications. The i3_ window manager is styled by using colors from
the Numix theme.

.. External links
.. _Ansible:
    https://www.ansible.com/

.. _minimal iso image:
    https://help.ubuntu.com/community/Installation/MinimalCD/

.. _i3:
    https://i3wm.org/

.. _Chromium:
    https://www.chromium.org/Home/

.. _zathura:
    https://pwmt.org/projects/zathura/

.. _Neovim:
    https://neovim.io/

.. _pass:
    https://www.passwordstore.org/

.. _Prezto:
    https://github.com/sorin-ionescu/prezto/

.. _gruvbox:
    https://github.com/morhetz/gruvbox/

.. _Hack:
    https://sourcefoundry.org/hack/

.. _virtualenvwrapper:
    http://virtualenvwrapper.readthedocs.io/en/latest/
