##################################################################################################
Structure of a C Extension
############################################################################################################################


The setup file
##############

We use distutils to build extension modules. This method also ensures that we do not need a compiler to install the extension.



.. code-block:: python


   from distutils.core import setup, Extension

   module1 = Extension('demo',
                       sources = ['linkaddr.c'])

   setup (name = 'MyPackage',
          version = '1.0',
          description = 'This is a demo package',
          ext_modules = [module1])

   #    module1 = Extension('demo',
   #                    define_macros = [('MAJOR_VERSION', '1'),
   #                                     ('MINOR_VERSION', '0')],
   #                    include_dirs = ['/usr/local/include'],
   #                    libraries = ['tcl83'],
   #                    library_dirs = ['/usr/local/lib'],
   #                    sources = ['demo.c'])
   #



With this we run


.. code-block:: bash

   python setup.py build



The Python.h Functions
##########################

- As discuessed earlier all python objects translate to PyObject* it handles all data parsing between Python and C.

- PyArg_ParseTuple(args, format, …) Handles getting the arguments from Python.

- Py_BuildValue(format, …) Handles turning values into PyObject pointers.

- Py_BuildValue(format, …) Handles turning values into PyObject pointers.

- More functions and their descriptions are available at `https://docs.python.org/3/c-api/module.html#initializing-modules`
