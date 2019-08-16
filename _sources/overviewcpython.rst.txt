############################################
Overview of the CPython Interpreter
############################################

..
   https://medium.com/@dawranliou/getting-started-with-python-internals-a5474ccb8022

Python is an interpreted language. But does that mean that there is no compilation in the process?


Well! There is!

Your source code is first compiled to [bytecode]. This [bytecode] is fed to the interpreter which then generates the output.


**Observe the example below**


.. code-block:: python


  # This is good example.

  compiled_bytecode = compile('import csv', 'csvimp.py', 'exec')
  print(compiled_bytecode.co_code)
  # Output: b'd\x00d\x01l\x00Z\x00d\x01S\x00'

  # This is your bytecode which is then interpreted by the CPython
  # compile is an in-built function


We have a utility that disassembles bytecodes for us.



.. code-block:: python

   # test.py
   x = 1
   y = 2
   z = x + y
   print(z)

.. code-block:: bash

   python -m dis <filename>.py
   

   
.. code-block:: bash


     1           0 LOAD_CONST               0 (1)
              2 STORE_NAME               0 (x)

     2           4 LOAD_CONST               1 (2)
                 6 STORE_NAME               1 (y)

     3           8 LOAD_NAME                0 (x)
                10 LOAD_NAME                1 (y)
                12 BINARY_ADD
                14 STORE_NAME               2 (z)

     4          16 LOAD_NAME                3 (print)
                18 LOAD_NAME                2 (z)
                20 CALL_FUNCTION            1
                22 POP_TOP
                24 LOAD_CONST               2 (None)
                26 RETURN_VALUEn



Interpretation
#########################


- We all know that everything in python are  objects this translates to *PyObject* in CPython
- An Argument is a PyFrameObject


.. code-block:: c 

   typedef struct {
     Py_ssize_t ob_refcnt;   /* object reference count */
     PyTypeObject* ob_type;  /* object type */
   };



Object Lifetime
#######################


- Python performs garbage collection by reference count. In the above struct when the reference count drops to 0. Its garbage collected.


