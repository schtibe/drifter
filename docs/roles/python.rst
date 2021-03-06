************
Python Roles
************

Python
======

Install Pip and Virtualenv along with dev dependencies. Dependencies to
build the Pillow package are also installed.

Both Python 2 and Python are always installed, for example to facilitate
tests on multiple python version, the parameter below only change the
behavior of python related roles.

Parameters
----------

-  **python\_version**: Either version 2 or 3, defaults to "2"

Virtualenv
==========

Create a python virtual environment and install application requirements
via pip. The environment will also get `pip-tools <https://github.com/jazzband/pip-tools>`_ installed.

The virtual environment is automatically activated upon box login.

-  **pip\_requirements** : filename of the requirements file, defaults to
   "requirements/dev.txt"
-  **env\_root** : directory where the virtual environment must be
   created, defaults to "~/ENV"
-  **pip\_requirements\_dir** : name of the requirements directory that contain the `.in` files. If set, Drifter will
   run ``pip-compile`` on these files upon provisioning.
-  **pip\_version** : the version of pip to install in the virtual environment. Defaults to 9.0.1.
-  **setuptools\_version** : the version of setuptools to install in the virtual environment. Defaults to 28.8.0.
-  **pip_tools\_version** : the version of pip-tools to install in the virtual environment. Defaults to 1.8.2.

Django
======

Uses the ``virtualenv`` role to create and install a virtual environment
for Django.

Configure database access via environment variable and then run
migrations (compatible with all Django version since 1.6).

You need to include either to ``mysql`` or ``postgresql`` roles before
this one.

This role depends on the Virtualenv and NGinx roles. The NGinx role is
configured to use the "django-site.js" site template on the port "8000".

Parameters
----------

-  **django\_root** : root directory of the Django project, default to
   the "root\_directory" variable defined in parameters.yml
-  **django\_version** : django version, the django version actually
   installed is decided via the requirements, this is only to determine
   how to perform migrations, default to "1.8"

Flask
=====

Uses the ``virtualenv`` role to create and install a virtual environment
for Flask.
