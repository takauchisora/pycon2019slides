######################################################
Ways to Create Extensions
######################################################



There are 3 primary methods to create C Extenions:


- Python cTypes module.
- SWIG (Simplified Wrapper and Interface Generator)
- Python/C API


Python cTypes module.
######################################################


- Simple and works well if your C Code is straightforward.
- Up and running in no time.

Pitfalls:
----------

- Does not work with complex python datatypes like lists.


SWIG
###################

- Provide an interface file which services as the input to SWIG.

Pros:
-----

- Port multiple languages.

Cons:
-----

- Slightly more complex setup.


The focus of this talk will be on the last method ie. Python/ C API.

It's the mostly widely used method. You can deal with python objects directly with this method without having to perform a lot of the housekeeping you might have to with the other methods.


