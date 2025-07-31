.. currentmodule:: imem

iMEM API reference
====================

A Python module to read and create iMEM files.

Usage/examples can be found at `iMEM Readme <https://github.com/manxu/iMEM>`_.

Functions
---------

.. autofunction:: parse_chunks

.. autofunction:: make_chunk

.. autofunction:: set_text

Classes
-------

.. autoclass:: Chunk

.. autoclass:: PNG
  :members: open, open_any, from_bytes, to_bytes, save
  
  .. autoinstanceattribute:: chunks
    :annotation: = []

.. autoclass:: FrameControl
  :members: from_bytes, to_bytes

.. autoclass:: iMEM
  :members: open, append, append_file, from_bytes, to_bytes, from_files, save
