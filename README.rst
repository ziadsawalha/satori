
================================
Satori - Configuration Discovery
================================

Satori provides configuration discovery for existing infrastructure. It is
a `related OpenStack project`_.

The charter for the project is to focus narrowly on discovering pre-existing
infrastructure and installed or running software. For example, given a URL and
some credentials, discover which resources (load balancer and servers) the URL
is hosted on and what software is running on those servers.

Configuration discovery output could be used for:

* Configuration analysis (ex. compared against a library of best practices)
* Configuration monitoring (ex. has the configuration changed?)
* Troubleshooting
* Heat Template generation
* Solum Application creation/import
* Creation of Chef recipes/cookbooks, Puppet modules, Ansible playbooks, setup
  scripts, etc..

Getting Started
===============

Run::

   $ pip install satori
   $ satori foo.com
   Address:
     foo.com resolves to IPv4 address 4.4.4.4

Allow for deeper discovery by setting OpenStack tenant environment variables::

   $ export OS_USERNAME=yourname
   $ export OS_PASSWORD=yadayadayada
   $ export OS_TENANT_NAME=myproject
   $ export OS_AUTH_URL=http://...
   $ satori foo.com
   Address:
       www.foo.com resolves to IPv4 address 4.4.4.4
   Host:
       4.4.4.4 (www.foo.com) is hosted on a Nova Instance
       Instance Information:
           URI: https://nova.api.somecloud.com/v2/111222/servers/d9119040-f767-
                4141-95a4-d4dbf452363a
           Name: sampleserver01.foo.com
           ID: d9119040-f767-4141-95a4-d4dbf452363a
       ip-addresses:
           public:
               ::ffff:404:404
               4.4.4.4
           private:
               10.1.1.156

Documentation
=============

Additional documentation is located in the `doc` directory and is hosted at
http://satori.readthedocs.org/.

Start Hacking
=============

We recommend using a virtualenv to install the client. This description
uses the `install virtualenv`_ script to create the virtualenv::

   $ python tools/install_venv.py
   $ source .venv/bin/activate
   $ python setup.py develop

Unit tests can be ran simply by running::

   $ run_tests.sh


Links
=====
- `OpenStack  Wiki`_
- `Launchpad Project`_

.. _OpenStack Wiki: https://wiki.openstack.org/Satori
.. _Launchpad Project: https://launchpad.net/satori
.. _OpenStack tenant environment variables: http://docs.openstack.org/developer/python-novaclient/shell.html
.. _related OpenStack project: https://wiki.openstack.org/wiki/ProjectTypes
.. _install virtualenv: https://github.com/rackerlabs/satori/blob/master/tools/install_venv.py
