.. image:: https://raw.githubusercontent.com/neo4j-contrib/neomodel/master/doc/source/_static/neomodel-300.png
   :alt: neomodel

An Object Graph Mapper (OGM) for the neo4j_ graph database, built on the awesome neo4j_driver_

- Familiar Django model style definitions.
- Powerful query API.
- Enforce your schema through cardinality restrictions.
- Full transaction support.
- Thread safe.
- pre/post save/delete hooks.
- Django integration via django_neomodel_

.. _django_neomodel: https://github.com/neo4j-contrib/django-neomodel
.. _neo4j: https://neo4j.com/
.. _neo4j_driver: https://github.com/neo4j/neo4j-python-driver

.. image:: https://secure.travis-ci.org/neo4j-contrib/neomodel.png
    :target: https://secure.travis-ci.org/neo4j-contrib/neomodel/

.. image:: https://readthedocs.org/projects/neomodel/badge/?version=latest
    :alt: Documentation Status
    :scale: 100%
    :target: https://neomodel.readthedocs.io/en/latest/?badge=latest


Documentation
=============

Available on readthedocs_.

.. _readthedocs: http://neomodel.readthedocs.org

Requirements
============

- Python 3.5+
- `Supported version <https://neo4j.com/developer/kb/neo4j-supported-versions/>`_ of neo4j


Installation
============

Install from pypi (recommended)::

    $ pip install neomodel

To install from github::

    $ pip install git+git://github.com/neo4j-contrib/neomodel.git@HEAD#egg=neomodel-dev

Upgrading 3.x to 4.x
====================

 * The deprecated search() method on RelationshipManager has been removed (use filter() instead)
 * The deprecated NormalProperty has been removed (use NormalizedProperty instead)
 * The "bolt+routing" scheme has been replaced with "neo4j". Using "bolt+routing" produces a deprecation warning, and replaces the scheme with "neo4j"
 * Neo4j no longer supports Python 2.7, or versions below 3.5
 * neobolt and neotime are no longer required
 * The ConnectionExpired exception has been removed
 * Be aware of changes in https://github.com/neo4j/neo4j-python-driver/wiki/4.0-changelog
    * Connections are now unencrypted by default; to reproduce former behaviour, set ENCRYPTED_CONNECTION to True and scheme to "neo4j+s", "neo4j+ssc", "bolt+s" or "bolt+ssc"
    * The neo4j.v1 subpackage is now no longer available; all imports should be taken from the neo4j package instead.
    * CypherError is now Neo4jError
    * max_pool_size is now max_connection_pool_size
    * access_mode is now default_access_mode

Using an older version
======================

To use an older version, for instances where you have to use Python 2.7, use neo4j-driver 1.7 and neomodel 3.3.2.


Contributing
============

Ideas, bugs, tests and pull requests always welcome. 

As of release `4.0.0` we now have a curated list of issues / development targets for
`neomodel` available on `the Wiki <https://github.com/neo4j-contrib/neomodel/wiki/TODOs-&-Enhancements>`_.

If you are interested in developing `neomodel` further, pick a subject from the list and open a Pull Request (PR) for 
it. If you are adding a feature that is not captured in that list yet, consider if the work for it could also 
contribute towards delivering any of the existing todo items too.

Running the test suite
----------------------

Make sure you have a Neo4j database version 3 or higher to run the tests on.::

    $ export NEO4J_BOLT_URL=bolt://neo4j:neo4j@localhost:7687 # (the default)

Setup a virtual environment, install neomodel for development and run the test suite::

    $ virtualenv venv
    $ source venv/bin/activate
    $ python setup.py develop
    $ pytest

If you are running a neo4j database for the first time the test suite will set the password to 'test'.
If the database is already populated, the test suite will abort with an error message and ask you to re-run it with the
`--resetdb` switch. This is a safeguard to ensure that the test suite does not accidentally wipe out a database if
you happen to not have restarted your Neo4j server to point to a (usually named) `debug.db` database.

If you have ``docker-compose`` installed, you can run the test suite against all supported Python
interpreters and neo4j versions::

    # in the project's root folder:
    $ ./tests-with-docker-compose.sh


.. image:: https://badges.gitter.im/Join%20Chat.svg
   :alt: Join the chat at https://gitter.im/neo4j-contrib/neomodel
   :target: https://gitter.im/neo4j-contrib/neomodel?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge
