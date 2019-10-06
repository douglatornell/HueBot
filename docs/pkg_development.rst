.. Copyright 2019, Doug Latornell
..
.. Licensed under the Apache License, Version 2.0 (the "License");
.. you may not use this file except in compliance with the License.
.. You may obtain a copy of the License at
..
..    https://www.apache.org/licenses/LICENSE-2.0
..
.. Unless required by applicable law or agreed to in writing, software
.. distributed under the License is distributed on an "AS IS" BASIS,
.. WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
.. See the License for the specific language governing permissions and
.. limitations under the License.


.. _HueBotPackagedDevelopment:

**********************************************************
:kbd:`huebot` Package Development
**********************************************************


.. image:: https://img.shields.io/badge/license-Apache%202-cb2533.svg
    :target: https://www.apache.org/licenses/LICENSE-2.0
    :alt: Licensed under the Apache License, Version 2.0
.. image:: https://img.shields.io/badge/python-3.7+-blue.svg
    :target: https://docs.python.org/3.7/
    :alt: Python Version
.. image:: https://img.shields.io/badge/version%20control-hg-blue.svg
    :target: https://bitbucket.org/douglatornell/huebot/
    :alt: Mercurial on Bitbucket
.. image:: https://img.shields.io/badge/code%20style-black-000000.svg
    :target: https://black.readthedocs.io/en/stable/
    :alt: The uncompromising Python code formatter
.. image:: https://readthedocs.org/projects/huebot/badge/?version=latest
    :target: https://huebot.readthedocs.io/en/latest/
    :alt: Documentation Status
.. image:: https://img.shields.io/bitbucket/issues/douglatornell/huebot.svg
    :target: https://bitbucket.org/douglatornell/huebot/issues?status=new&status=open
    :alt: Issue Tracker

The HueBot package (:kbd:`huebot`) is Hue lighting automation and schedule management


.. _HueBotPythonVersions:

Python Versions
===============

.. image:: https://img.shields.io/badge/python-3.7+-blue.svg
    :target: https://docs.python.org/3.7/
    :alt: Python Version

The :kbd:`huebot` package is developed and tested using `Python`_ 3.7 or later.
The package uses some Python language features that are not available in versions prior to 3.6,
in particular:

* `formatted string literals`_
  (aka *f-strings*)
* the `file system path protocol`_

.. _Python: https://www.python.org/
.. _formatted string literals: https://docs.python.org/3/reference/lexical_analysis.html#f-strings
.. _file system path protocol: https://docs.python.org/3/whatsnew/3.6.html#whatsnew36-pep519


.. _HueBotGettingTheCode:

Getting the Code
================

.. image:: https://img.shields.io/badge/version%20control-hg-blue.svg
    :target: https://bitbucket.org/douglatornell/huebot/
    :alt: Mercurial on Bitbucket

Clone the code and documentation `repository`_ from Bitbucket with:

.. _repository: https://bitbucket.org/douglatornell/huebot/

.. code-block:: bash

    $ hg clone ssh://hg@bitbucket.org/douglatornell/huebot HueBot

or

.. code-block:: bash

    $ hg clone https://your_userid@bitbucket.org/douglatornell/huebot HueBot

if you don't have `ssh key authentication`_ set up on Bitbucket
(replace :kbd:`you_userid` with you Bitbucket userid,
or copy the link from the :guilabel:`Clone` action pop-up on the `repository`_ page).

.. _ssh key authentication: https://confluence.atlassian.com/bitbucket/set-up-an-ssh-key-728138079.html


.. _HueBotDevelopmentEnvironment:

Development Environment
=======================

Setting up an isolated development environment using `Conda`_ is recommended.
Assuming that you have the `Anaconda Python Distribution`_ or `Miniconda3`_ installed,
you can create and activate an environment called :kbd:`huebot` that will have all of the Python packages necessary for development,
testing,
and building the documentation with the commands below.

.. _Conda: https://conda.io/docs/
.. _Anaconda Python Distribution: https://www.anaconda.com/download/
.. _Miniconda3: https://conda.io/docs/install/quick.html

.. code-block:: bash

    $ cd HueBot
    $ conda env create -f env/environment-dev.yaml
    $ source activate huebot
    (huebot)$ pip install --editable .

The :kbd:`--editable` option in the :command:`pip install` command above installs the package from the cloned repo via symlinks so that the installed package will be automatically updated as the repo evolves.

To deactivate the environment use:

.. code-block:: bash

    (huebot)$ source deactivate


.. _HueBotCodingStyle:

Coding Style
============

.. image:: https://img.shields.io/badge/code%20style-black-000000.svg
    :target: https://black.readthedocs.io/en/stable/
    :alt: The uncompromising Python code formatter

The :kbd:`HueBot` package uses the `black`_ code formatting tool to maintain a coding style that is very close to `PEP 8`_.

.. _black: https://black.readthedocs.io/en/stable/
.. _PEP 8: https://www.python.org/dev/peps/pep-0008/

:command:`black` is installed as part of the :ref:`HueBotDevelopmentEnvironment` setup.

To run :command:`black` on the entire code-base use:

.. code-block:: bash

    $ cd HueBot
    $ conda activate huebot
    (huebot)$ black ./

in the repository root directory.
The output looks something like::

  **add example black output**


.. _HueBotBuildingTheDocumentation:

Building the Documentation
==========================

.. image:: https://readthedocs.org/projects/huebot/badge/?version=latest
    :target: https://huebot.readthedocs.io/en/latest/
    :alt: Documentation Status

The documentation for the :kbd:`HueBot` package is written in `reStructuredText`_ and converted to HTML using `Sphinx`_.
Creating a :ref:`HueBotDevelopmentEnvironment` as described above includes the installation of Sphinx.
Building the documentation is driven by the :file:`docs/Makefile`.
With your :kbd:`salishsea-nowcast` development environment activated,
use:

.. _reStructuredText: http://www.sphinx-doc.org/en/master/usage/restructuredtext/basics.html
.. _Sphinx: http://www.sphinx-doc.org/en/master/

.. code-block:: bash

    (huebot)$ (cd docs && make clean html)

to do a clean build of the documentation.
The output looks something like::

  **add example Sphinx output**

The HTML rendering of the docs ends up in :file:`docs/_build/html/`.
You can open the :file:`index.html` file in that directory tree in your browser to preview the results of the build.

If you have write access to the `repository`_ on Bitbucket,
whenever you push changes to Bitbucket the documentation is automatically re-built and rendered at https://huebot.readthedocs.io/en/latest/.


.. _HueBotLinkCheckingTheDocumentation:

Link Checking the Documentation
-------------------------------

Sphinx also provides a link checker utility which can be run to find broken or redirected links in the docs.
With your :kbd:`huebot)` environment activated,
use:

.. code-block:: bash

    (huebot))$ cd HueBot)/docs/
    (huebot)) docs$ make linkcheck

The output looks something like::

  **add example linkcheck output**

Look for any errors in the above output or in _build/linkcheck/output.txt


.. _HueBotRunningTheUnitTests:

Running the Unit Tests
======================

The test suite for the :kbd:`HueBot` package is in :file:`HueBot/tests/`.
The `pytest`_ tool is used for test parametrization and as the test runner for the suite.

.. _pytest: https://docs.pytest.org/en/latest/

With your :kbd:`huebot` development environment activated,
use:

.. code-block:: bash

    (huebot)$ cd HueBot/
    (huebot)$ py.test

to run the test suite.
The output looks something like::

  **add example pytest output**

You can monitor what lines of code the test suite exercises using the `coverage.py`_ tool with the command:

.. _coverage.py: https://coverage.readthedocs.io/en/latest/

.. code-block:: bash

    (huebot)$ cd HueBot/
    (huebot)$ coverage run -m py.test

and generate a test coverage report with:

.. code-block:: bash

    (huebot)$ coverage report

to produce a plain text report,
or

.. code-block:: bash

    (huebot)$ coverage html

to produce an HTML report that you can view in your browser by opening :file:`HueBot/htmlcov/index.html`.


.. _HueBotVersionControlRepository:

Version Control Repository
==========================

.. image:: https://img.shields.io/badge/version%20control-hg-blue.svg
    :target: https://bitbucket.org/douglatornell/huebot/
    :alt: Mercurial on Bitbucket

The :kbd:`HueBot` package code and documentation source files are available as a `Mercurial`_ repository at https://bitbucket.org/douglatornell/huebot/.

.. _Mercurial: https://www.mercurial-scm.org/


.. _HueBotIssueTracker:

Issue Tracker
=============

.. image:: https://img.shields.io/bitbucket/issues/douglatornell/huebot.svg
    :target: https://bitbucket.org/douglatornell/huebot/issues?status=new&status=open
    :alt: Issue Tracker

Development tasks,
bug reports,
and enhancement ideas are recorded and managed in the issue tracker at https://bitbucket.org/douglatornell/huebot/issues.


License
=======

.. image:: https://img.shields.io/badge/license-Apache%202-cb2533.svg
    :target: https://www.apache.org/licenses/LICENSE-2.0
    :alt: Licensed under the Apache License, Version 2.0

The code and documentation of the HueBot project
are copyright 2019 by Doug Latornell.

They are licensed under the Apache License, Version 2.0.
https://www.apache.org/licenses/LICENSE-2.0
Please see the LICENSE file for details of the license.
