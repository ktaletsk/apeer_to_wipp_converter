=======================
APEER to WIPP converter
=======================


.. image:: https://img.shields.io/pypi/v/apeer_to_wipp_converter.svg
        :target: https://pypi.python.org/pypi/apeer_to_wipp_converter

.. image:: https://img.shields.io/travis/ktaletsk/apeer_to_wipp_converter.svg
        :target: https://travis-ci.com/ktaletsk/apeer_to_wipp_converter

.. image:: https://readthedocs.org/projects/apeer-to-wipp-converter/badge/?version=latest
        :target: https://apeer-to-wipp-converter.readthedocs.io/en/latest/?badge=latest
        :alt: Documentation Status




Convert APEER plugins to WIPP

Both `APEER <www.apeer.com>`_ developed by Zeiss and `WIPP <https://isg.nist.gov/deepzoomweb/software/wipp>`_ developed by NIST provide image processing tools and pipelines based on modern containers.
While there are differences in the approaches and implementation, basic main components (Dockerfile with entrypoint + JSON description of the pipeline step) are similar enough that it is possible to convert one into the other.
Even though in the long term it is prefered that both systems adopt the same standard for these containers, in the short term it is useful to be able to at least convert between the standards.

This repo contains the command line utility to convert the source code of APEER plugin into the source code of the WIPP plugin.
Conversion is fully automatic and changes as little of the original source code as possible:
- Creates a bash script that translates WIPP input parameters into APEER format in the runtime
- Creates a new Dockerfile with modified ENTRYPOINT command and COPY command for bash script described above
- Creates a ``plugin.json`` according to WIPP specification

Installation
------------

``pip install apeer_to_wipp_converter``

Usage
-----

``a2w <path to module_specification.json in APEER module folder>``

After you converted plugin, you may build the Dockerfile and try it in WIPP. Instructions for local installation are available `here <https://github.com/usnistgov/WIPP/blob/master/deployment/wipp-complete-single-node/README.md>`.

Credits
-------

This package was created with Cookiecutter_ and the `audreyr/cookiecutter-pypackage`_ project template.

.. _Cookiecutter: https://github.com/audreyr/cookiecutter
.. _`audreyr/cookiecutter-pypackage`: https://github.com/audreyr/cookiecutter-pypackage
