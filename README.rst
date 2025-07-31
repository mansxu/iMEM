iMEM
======

.. image:: https://travis-ci.org/eight04/pyAPNG.svg?branch=master
  :target: https://travis-ci.org/eight04/pyAPNG
  
.. image:: https://readthedocs.org/projects/pyapng/badge/?version=latest
  :target: http://pyapng.readthedocs.io/en/latest/?badge=latest
  :alt: Documentation Status

A Python module to read and create iMEM files, memes in internationalized format.

Features
--------

- Merge multiple images into one iMEM file. (Uses Pillow to convert images into PNG format)
- Read iMEM files and extract different language versions to PNG files.

Dependencies
------------

- `Pillow <https://github.com/python-pillow/Pillow>`__ - **Optional**. You can still use iMEM without PIL, but only PNG files can be read.

Development dependencies
------------------------

- `pngcheck <http://www.libpng.org/pub/png/apps/pngcheck.html>`_
- See requirements.txt for other dev-dependencies.

Installation
------------

From `pypi <https://pypi.org/project/imem/>`__::

  pip install imem

Usage
-----

Convert a series of images into iMEM format:

.. code:: python

  from imem import iMEM
    
  iMEM.from_files(["en.jpg", "de-DE.png", "jp.webp"], default="en").save("output.imm")
    
Specify languages without file names:

.. code:: python

  from imem import iMEM
    
  files = [
    ("1.png", "en"),
    ("2.avif", "de-DE"),
    ("3.jpg", "jp")
  ]
    
  im = iMEM()
  for file, lang in files:
    im.append_file(file, language=lang)
  im.save("result.imm")

Extract memes from an iMEM file:
    
.. code:: python

  from imem import iMEM

  im = iMEM.open("meme.imm")
  for i, (png, control) in enumerate(im.versions):
    png.save("{l}.png".format(l=control.language))
    
Add the meme text to the PNG file:

.. code:: python

  from imem import PNG, set_text
  
  im = PNG.open("image.png")
  im.chunks.append(set_text(language="en", value="Peppy Farm Remembers!"))
  im.save("image.png")
    
Documentation
-------------

http://imem.readthedocs.io/en/latest/

Changelog
---------
