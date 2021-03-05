User-level documentation workflow
#################################

What you need to know
+++++++++++++++++++++

We use `Sphinx <https://www.sphinx-doc.org/en/master/>`_ to generate
documentation and `Read the Docs <https://readthedocs.org/>`_ to
publish it. Sphinx uses reStructuredText as the base format for the
documentation. To learn more about the syntax, check out this `quick
reference
<https://thomas-cokelaer.info/tutorials/sphinx/rest_syntax.html>`_.

The NEST simulator documentation lives alongside its code. It is
contained in the ``doc/userdoc`` directory within the `NEST source
code repository <https://github.com/nest/nest-simulator>`_ on GitHub.

We work with `GitHub <https://www.github.com>`_ as a web-based hosting
service for Git. Git allows us to keep our versions under control,
with each release of NEST having its own documentation.

This workflow aims for the concept of **user-correctable documentation**.

.. image:: ../_static/img/documentation_workflow.png
  :width: 500
  :alt: Alternative text

.. note::
   This workflow shows you how to create **user-level documentation**
   for NEST. For the **developer documentation**, please refer to our
   :doc:`Developer documentation workflow
   <developer_documentation_workflow>`.

Changing the documentation
++++++++++++++++++++++++++

If you notice any errors or weaknesses in the documentation, please
submit an `Issue <https://github.com/nest/nest-simulator/issues>`_ in
our GitHub repository.

You can also make changes directly to your forked copy of the `NEST source
code repository <https://github.com/nest/nest-simulator>`_ and create a `pull
request <https://github.com/nest/nest-simulator/pulls>`_. Just follow the
workflow below!

Setting up your environment
+++++++++++++++++++++++++++

To install the dependencies for building the documentation, you can
either directly run

.. code-block:: bash

    pip3 install -r <nest_source_dir>/doc/requirements.txt

or alternatively install the dependencies into a conda environment (we
recommend `miniconda <https://docs.conda.io/en/latest/miniconda>`_ for
this). After installing conda, you can simply run

.. code-block:: bash

    conda env create -f <nest_source_dir>/doc/environment.yml
    conda activate nest-doc

If you later on want to deactivate or delete the build environment:

.. code-block:: bash

   conda deactivate
   conda remove --name nest-doc --all

Generating documentation with Sphinx
++++++++++++++++++++++++++++++++++++

Now that you activated your environment, you can generate HTML files using
Sphinx.

Rendering HTML
~~~~~~~~~~~~~~

If you intend to work on the documentation, or if you want to obtain a
local version of it for other reasons, you can build the documentation
by simply running the following command in the build directory of NEST
(i.e. the directory where you ran ``cmake``)

.. code-block:: bash

    make html

To install the documentation under `<nest_install_dir>`` along with
the rest of NEST, this command can be followed by

.. code-block:: bash

   make install

If you want to view the files after installation, you can run

.. code-block:: bash

   browser <nest_install_dir>/share/doc/nest/html/index.html

Editing and creating pages
~~~~~~~~~~~~~~~~~~~~~~~~~~

To edit existing `reStructuredText <https://thomas-cokelaer.info/tutorials/
sphinx/rest_syntax.html>`_ files or to create new ones, follow the steps below:

1. You can edit and/or add ``.rst`` files in the ``doc`` directory using your
   editor of choice.

2. If you create a new page, open ``contents.rst`` in the ``doc`` directory
   and add the file name under ``.. toctree::``. This will ensure it appears on
   the NEST simulator documentation's table of contents.

3. If you rename or move a file, please make sure you update all the
   corresponding cross-references.

4. Save your changes.

5. Re-render documentation as described above.

Previewing on Read the Docs (optional)
++++++++++++++++++++++++++++++++++++++

Proceed as follows to preview your version of the documentation on Read the
Docs.

1. Check that unwanted directories are listed in ``.gitignore``:

.. code-block:: bash

   _build
   _static
   _templates

2. Add, commit and push your changes to GitHub.

3. Go to `Read the Docs <https://readthedocs.org/>`_. Sign up for an account
   if you don't have one.

4. `Import <https://readthedocs.org/dashboard/import/>`_ the project.

5. Enter the details of your project in the ``repo`` field and hit ``Create``.

6. `Build <https://docs.readthedocs.io/en/stable/intro/
   import-guide.html#building-your-documentation>`_ your documentation.

This allows you to preview your work on your Read the Docs account. In order
to see the changes on the official NEST simulator documentation, please submit
a pull request.

Creating pull request
+++++++++++++++++++++

Once your documentation work is finished, you can create a `pull request
<https://nest.github.io/nest-simulator/development_workflow#create-a-pull-
request>`_ to the ``master`` branch of the NEST Source Code Repository. Your
pull request will be reviewed by the NEST Documentation Team!

Helpdesk
++++++++

For a list of commands for SLI and C++, you can access the the online
command index via the command line

::

   import nest
   nest.helpdesk()

.. note::
    The ``helpdesk()`` command needs to know which browser to launch
    in order to display the help pages. The browser is set as an
    option of helpdesk. Please see the file ``~/.nestrc`` for an
    example, which sets Firefox as browser.

.. note::
    The ``helpdesk()`` command does not work if you have compiled NEST
    with MPI support, but you have to enter the address of the
    helpdesk (``file://<nest_install_dir>/share/doc/nest/index.html``)
    manually into the browser.  Replace ``<nest_install_dir>`` with
    the path under which NEST is installed.
