Wasm Bindings
=============

WebAssembly
-----------
As a programming language, WebAssembly is comprised of two formats that
represent the same structures, albeit in different ways:

1. The ``.wat`` text format (called wat for "WebAssembly Text") uses
   S-expressions, and bears some resemblance to the Lisp family of languages
   like Scheme and Clojure.

2. The ``.wasm`` binary format is lower-level and intended for consumption
   directly by wasm virtual machines. It is conceptually similar to ELF and
   Mach-O. Wasm is designed as a portable target for compilation of high-level
   languages like C/C++/Rust, enabling deployment on the web for client and
   server applications.

The following sections describe how wRPC interacts with both formats

WebAssembly Text
----------------
Exported functions
~~~~~~~~~~~~~~~~~~

All that needs to be done for wRPC to get functions from your module is to
use the import and export structures provided by WebAssembly Text

.. code-block:: Lisp

    (export "add" (func $add))

All that will have to be done to make wRPC to recognize the exported functions
is the following initialization

.. code-block:: JavaScript

    import wRPC;
    wRPC.initModule("foo.wat");

Imported Functions
~~~~~~~~~~~~~~~~~~
.. todo::

    figure out how to get this working

Wasm Binarys
------------
Due to the large differences in compilers and packagers this has traditionally
been has been hard to deal with. wRPC Comes with profiles for dealing with this
for you.

.. code-block:: JavaScript

    // Init with compiler template
    wRPC.initModule("foo.wasm", "emscripten");

    // Init with language template
    wRPC.initModule("bar.wasm", "Rust");
