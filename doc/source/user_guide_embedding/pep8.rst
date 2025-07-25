.. _ref_pep8aliases:

PEP 8 aliases
=============

Overview
--------

PyMechanical provides `PEP 8 Style <https://peps.python.org/pep-0008/>`_ aliases for Mechanical APIs.
This enables you to convert traditional Pascal Case methods and property names to Snake Case that follow Python naming conventions.
This feature makes the Mechanical API more pythonic and consistent with standard Python coding practices.

When PEP 8 aliases are enabled, you can use both the original Pascal Case names and the new
Snake Case aliases interchangeably, providing backward compatibility while offering a more
Python-friendly API.

Enabling pep8 Aliases
---------------------

To enable PEP 8 aliases, use the ``pep8_aliases`` parameter when creating an ``App`` instance:

.. code:: python

   from ansys.mechanical.core import App

   # Create an app instance with PEP 8 aliases enabled
   app = App(pep8_aliases=True, globals=globals())

   # Now you can use both Pascal Case and Snake Case
   # Traditional way (Pascal Case)
   analysis = Model.AddStaticStructuralAnalysis()
   analysis.Name = "test"

   # Pythonic way (Snake Case)
   analysis = Model.add_static_structural_analysis()
   analysis.name = "test"

Examples
--------

The following examples illustrate how to use PEP 8 aliases in practice:

- ``Model.AddStaticStructuralAnalysis()``  → ``Model.add_static_structural_analysis()``
- ``Model.AddNamedSelection()``            → ``Model.add_named_selection()``
- ``Model.Mesh.GenerateMesh()``            → ``Model.mesh.generate_mesh()``
- ``Graphics.Camera.SetFit()``             → ``Graphics.camera.set_fit()``
- ``Model.Name``                           → ``Model.name``

.. code:: python

   # Example usage with PEP 8 aliases
   analysis = Model.add_static_structural_analysis()
   named_selection = Model.add_named_selection()
   Model.mesh.generate_mesh()
   Graphics.camera.set_fit()
   print(Model.name)


Limitations
-----------
- Enum values retain their original Pascal Case style; for example, ``Format.Automatic`` does not become ``Format.AUTOMATIC``.
- PEP 8 aliases are not included in type hints provided by PyMechanical stubs.
