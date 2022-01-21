Installation
============

There are a few ways to install taskloop, with PyPi (via pip) being the easiest.

PyPi
----

Within a virtualenv, you can install taskloop with::

    pip install taskloop

That will create a ``taskloop`` command which you should be able to run.

Poetry (development):
---------------------

If you want to work with the source code directly, you can use poetry to install taskloop with::

    git clone https://github.com/kellya/taskloop.git
    cd taskloop
    poetry install
    poetry run taskloop/loop.py

.. note:: The global ``taskloop`` entry point is not available when installing this way.

