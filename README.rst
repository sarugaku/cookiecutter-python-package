========================================
Cookiecutter Template for Python Project
========================================


Usage
=====

::

    cookiecutter https://github.com/sarugaku/cookiecutter-python-package


Features
========

Pipfile for dependency management
---------------------------------

We recommend using Pipenv_ to work with the Pipfile.

Run this inside the project after generation::

    pipenv install --dev

All dependencies (including the in-development package itself) are already
listed in the generated Pipfile.


Towncrier_ for changelog management
-----------------------------------

When you make a change, add a fragment inside the ``news`` directory. They will
be used to generate a changelog when you release.

See Towncrier’s project page for more information.


Invoke_ for automation
----------------------

Add tasks in ``tasks`` directory, and you can run them with ``pipenv run inv``.
A task in already present to automate the release process.


Fully automated release process
-------------------------------

Run the following ommand to make a release::

    pipenv run release --type=major --repo=pypi

This runs the ``release`` script in Pipfile, which points to a Invoke task with
the same name.

A run-down of what the task does:

* Bump the package version. You can specify ``type`` to change what part to
  bump. Available values are ``major``, ``minor``, and ``patch``.
* Run Towncrier to generate an entry in ``CHANGELOG.rst``.
* Run Git to commit and tag the release.
* Build distros (sdist and wheels).
* Upload built distros to PyPI with Twine. You can change the upload
  destination with the ``repo`` option (to e.g. ``pypitest``).
* Pre-bump the package again to a dev version for the next development cycle.


.. _Pipenv: https:://pipenv.org
.. _Towncrier: https://github.com/hawkowl/towncrier
.. _Invoke: http://www.pyinvoke.org/
