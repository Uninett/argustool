==========
Argus tool
==========

.. image:: https://img.shields.io/github/actions/workflow/status/Uninett/argustool/tox.yml?branch=master
   :target: https://github.com/Uninett/argustool/actions

.. image:: https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/astral-sh/ruff/main/assets/badge/v2.json
   :target: https://github.com/astral-sh/ruff

This is a light wrapper around, currently, the `pyargus library (aka.
argus-api-client) <https://github.com/Uninett/pyargus>`_, to be able to
more easily write a glue service controlled via shell scripts.

Usage examples
==============

All commands exits with 0 on success, 1 on various errors, and 2 on
errors due to the Argus server or network trouble.

Error messages are printed to stderr.

Get a new authentication token
------------------------------

If your argus server is running version 1.29.0 or newer you can request
to get a new token (with a new expiration date) via API version 2. The
token you are using to access the server with must still be valid.

There are two methods:

Use an existing, still valid token
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: console

    $ argustool -t VALID_TOKEN -u URL token --refresh

This will spit out just the token. Making it verbose, via:

.. code-block:: console

    $ argustool -t VALID_TOKEN -u URL -v token --refresh

will also dump the expiration time, but is less useful in scripts.

You can put the token in the environment variable ``ARGUS_TOKEN``.

Use a username/password
~~~~~~~~~~~~~~~~~~~~~~~

Note that you don't need an existing token here.

.. code-block:: console

    $ argustool -u URL auth USERNAME PASSWORD

This will spit out just the token. Making it verbose, via::

    $ argustool -u URL -v auth USERNAME PASSWORD

will also dump the expiration time, but is less useful in scripts.

You can put the token in the environment variable ``ARGUS_TOKEN``.

Username may be read from ``ARGUS_USERNAME``, and password mau be read
from ``ARGUS_PASSWORD``.

Send an explicit heartbeat
--------------------------

When a source uses the API for anything, that will count as a heartbeat.
However if a source rarely has anything to report, it may seem like the
source is no longer functioning. Sending an explicit heartbeat fixes
this:

.. code-block:: console

    $ argustool -t VALID_TOKEN -u URL heartbeat --send

Detecting whether the server supports heartbeats
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The explicit heartbeat endpoint requires an Argus server new enough to
provide it. Detect if the server is new enough with:

.. code-block:: console

    $ argustool -t VALID_TOKEN -u URL heartbeat --is-supported

You do need a token for this as the endpoint is only available to
authenticated users.

Development
===========

See CONTRIBUTING.rst in this repo.
