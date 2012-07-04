PyPi HAProxy buildout
=====================

This buildout is meant to build, configure and deploy a HAProxy load balancer
that provides failover for PyPi (the Python Package Index).

It is not meant for production use but merely for easy testing and development
of the HAProxy configuration, which then can be deployed to a HAProxy installed
with the systems package manager.


Usage
-----

No ``buildout.cfg`` file is supplied und should never be added to the
repository. Instead either create a symbolic link to an appropriate
configuration file (e.g. ``development.cfg``) or extend a configuration if you 
intend to make some customizations for your personal usage only.

Example::

 ln -s development.cfg buildout.cfg


Supervisor
----------

The development buildout will configure a supervisor that will launch a HAProxy
instance with verbose and debug mode enabled. Use ``bin/supervisord`` to initially
launch the supervisor and HAProxy with it, ``bin/supervisorctl`` to control the
supervisor or HAProxy instance and finally ``bin/supervisorctl shutdown`` to
shut down the supervisor and all processes it spawned.

Supervisor is configured to monitor memory usage of all processes and HTTP
responses of Zope instances.


Contributors
------------

- Lukas Graf [lukasg], Author
