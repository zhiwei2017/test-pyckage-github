test-pyckage-github
===================

..
    GitHub Actions
    ~~~~~~~~~~~~~~

    You can find all the configuration files of GitHub Actions in ``.github/workflows`` folder.

    Content
    :::::::

    +-------------+----------------------------------------------+--------------------------------------------------+-----------------------------+-----------------------------------------------------------+
    | Config File |          Steps                               |                Trigger Rules                     | Requisite CI/CD Variables   | CI/CD Variables description                               |
    +=============+==============================================+==================================================+=============================+===========================================================+
    |             | mypy check                                   |                                                  |                             |                                                           |
    |             +----------------------------------------------+                                                  |                             |                                                           |
    |             | flake8 check                                 | + **Pushes** to *master/develop* branches        |                             |                                                           |
    |             +----------------------------------------------+                                                  |                             |                                                           |
    | test.yml    | bandit check                                 | + **Pull Requests** to *master/develop* branches |                             |                                                           |
    |             +----------------------------------------------+                                                  |                             |                                                           |
    |             | test with python 3.8 (Ubuntu/Mac OS/Windows) |                                                  |                             |                                                           |
    |             +----------------------------------------------+                                                  |                             |                                                           |
    |             | test with python 3.9 (Ubuntu/Mac OS/Windows) |                                                  |                             |                                                           |
    |             +----------------------------------------------+                                                  |                             |                                                           |
    |             | test with python 3.10 (Ubuntu/Mac OS/Windows)|                                                  |                             |                                                           |
    |             +----------------------------------------------+                                                  |                             |                                                           |
    |             | test with python 3.11 (Ubuntu/Mac OS/Windows)|                                                  |                             |                                                           |
    |             +----------------------------------------------+                                                  |                             |                                                           |
    |             | twine check the built package                |                                                  |                             |                                                           |
    +-------------+----------------------------------------------+--------------------------------------------------+-----------------------------+-----------------------------------------------------------+
    |             |                                              |                                                  |                             | Token for uploading package to official PyPi. If you're   |
    |             |                                              |                                                  | POETRY_PYPI_TOKEN_PYPI      | using a private artifactory, please use the variables     |
    |             |                                              |                                                  |                             | `PACKAGE_INDEX_REPOSITORY_URL`, `PACKAGE_INDEX_USERNAME`, |
    |             |                                              |                                                  |                             | and `PACKAGE_INDEX_PASSWORD` instead.                     |
    |             |                                              |                                                  +-----------------------------+-----------------------------------------------------------+
    |             |                                              |                                                  | PACKAGE_INDEX_REPOSITORY_URL| URL of Private package index.                             |
    | release.yml | deploy to PyPi                               | **Pushes** to tags matching *vXX.XX.XX*          +-----------------------------+-----------------------------------------------------------+
    |             |                                              |                                                  | PACKAGE_INDEX_USERNAME      | Username of Private package index.                        |
    |             |                                              |                                                  +-----------------------------+-----------------------------------------------------------+
    |             |                                              |                                                  | PACKAGE_INDEX_PASSWORD      | Password of Private package index.                        |
    +-------------+----------------------------------------------+--------------------------------------------------+-----------------------------+-----------------------------------------------------------+
    | sphinx.yml  | deploy GitHub pages                          | **Pushes** to *master* branch                    |                             |                                                           |
    +-------------+----------------------------------------------+--------------------------------------------------+-----------------------------+-----------------------------------------------------------+

    **Note**:

    + Before publishing the GitHub pages of your project for the first time, please manually create the branch **gh-pages** via::

        $ git checkout master
        $ git checkout -b gh-pages
        $ git push origin gh-pages

    Setup Steps
    :::::::::::

    1. Go to **Settings**.
    2. Click **Secrets** section.
    3. Click **New repository secret** button.
    4. Input the name and value of a CI/CD variable.

    
    Makefile
    ++++++++

    .. list-table::
       :header-rows: 1

       * - Command
         - Description
       * - clean
         - Remove autogenerated folders and artifacts.
       * - clean-pyc
         - Remove python artifacts.
       * - clean-build
         - Remove build artifacts.
       * - bandit
         - Run `bandit`_ security analysis.
       * - mypy
         - Run `mypy`_ type checking.
       * - flake8
         - Run `flake8`_ linting.
       * - install
         - Install all the dependencies and the package itself.
       * - test
         - Run tests and generate coverage report.
       * - build
         - Build wheel package.
       * - publish
         - Publish the built wheel package.

Introduction
------------
jeroenjanssens

User Guide
----------

How to Install
++++++++++++++

Stable release
``````````````

To install test-pyckage-github, run this command in your terminal:

.. code-block:: console

    $ pip install test_pyckage_github

or

.. code-block:: console

    $ poetry self add test_pyckage_github

This is the preferred method to install test-pyckage-github, as it will always install the most recent stable release.


From sources
````````````

The sources for test-pyckage-github can be downloaded from the `Github repo <https://github.com/zhiwei2017/test-pyckage-github>`_.

You can either clone the public repository:

.. code-block:: console

    $ git clone https://github.com/zhiwei2017/test-pyckage-github.git

Once you have a copy of the source, you can install it with:

.. code-block:: console

    $ pip install .

or

.. code-block:: console

    $ poetry install

How to Use
++++++++++

To use test-pyckage-github in a project::

    import test_pyckage_github

Maintainers
-----------

..
    TODO: List here the people responsible for the development and maintaining of this project.
    Format: **Name** - *Role/Responsibility* - Email

* **Zhiwei Zhang** - *Maintainer* - `zhiwei2017@gamil.com <mailto:zhiwei2017@gamil.com?subject=[GitHub]test-pyckage-github>`_