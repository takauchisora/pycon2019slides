##########################################
A Few Things to remember
##########################################



Here are a few gotchas that you have to remember.


PyMethodDef
##############


- The compiler does not pick up errors from in here.

- The structure must always end with terminating NULL and 0 values. {NULL, NULL, 0, NULL}
Here we tell python if the function has argument, no arguments or arguments and keywords

- It is important we declare all functions as `static` this ensures that namespaces do not get mixed up.


Passing Invalid Arguments to our sample fib function
######################################################


What happens when the parameter passed is not an `int` .

The program raises an exception and we get `UNSIGNED_LONG_MAX` which takes a while to compute even in C.

We discuss error handling in the next section.

.. note::

   Work in progress.


