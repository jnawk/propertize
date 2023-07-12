.. _intro:

Introduction
============

Propertize is a library to typecast custom @property Callables to their return type.
Useful if you use an IDE that can't figure it out.

Requirements
------------

No extra requirements.

Installing
----------

You can install Propertize directly from PyPI using PIP and following command
in shell or command prompt: ::

    python3 -m pip install -U propertize

You can also install the latest development version (**maybe unstable/broken**) by
using following command: ::

    python3 -m pip install -U git+https://github.com/jnawk/propertize.git


Basic Usage
-----------
Here is a simple example to convince your IDE the custom properties you are
working with are in fact the return type of the under-the-covers callable.

.. code-block:: python3

    from propertize import p

    class HasOpaqueProperty:
        @custom_property_decorator
        def custom_property(self) -> str:
            return "Hello, World!"

    if __name__ == "__main__":
        has_opaque_property = HasOpaqueProperty()

        # has_opaque_property.custom_property is a typing.Callable[[...], str]
        # but if it were a property, it would be a str

        p(has_opaque_property.custom_property)  # is a str
