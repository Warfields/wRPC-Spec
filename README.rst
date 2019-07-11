Wasm RPC Protocol Specification
+++++++++++++++++++++++++++++++
This is the specification of the Protocol Buffers that wasm/node modules will
use to setup their RPC interfaces with the central RPC server.

RPC Overview
------------

.. figure:: figures/landing-2.svg
    :align: center
    :alt: A picture of a server and node structure

    Borrowed from `gRCP <https://grpc.io/docs/guides/>`_

Overall in the MVP of this RPC Framework only the above server and node
implimentation will be used. Direct node communication will not be supported.

When a node is initialized it will pass a protobuf describing it's functions
and how to call them. Once initialized any other module or direct JS Call can
be made to that module.

What still needs to be figured out
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
- Will Data be returned as another proto or as a direct JS value?
- Will the core be written in JS or Wasm?
- What's the best way to make this easy for other Devs to use?
- What are some default failure modes/exceptions?

Proto Descriptions
------------------
Initialization Proto
~~~~~~~~~~~~~~~~~~~~
The information that the initialization proto will provide are as follows

- Module name
- How to initialize
- Any extra steps to call functions
- Functions
    + name
    + params
    + return type
    + failure types?
    + async?
- Public info/Data
- Meta data?

Response proto
~~~~~~~~~~~~~~
The idea of this protobuf response is based on `Rust's std::option type <https://doc.rust-lang.org/std/option/>`_.

- Success/Fail
    + if fail why
    + Data

JS Bindings
-----------
This is a quick quick section on how to interact with wRPC. On the JavaScript
level. To begin, wRPC needs to initialize available modules to add new modules
to the RCP network.

.. code-block:: JavaScript

    import wRPC;

    // Init a wasm/wat module and have wRPC infer interaction
    wRPC.initModule("foo.wasm");

    // Init with compiler template
    wRPC.initModule("foo.wasm", "emscripten");

    // Init with custom protocol buffer
    wRPC.initModule("foo.wasm", "foo.proto");

Next, modules can be globally imported.

.. code-block:: JavaScript

    import wRPC.foo as foo;
    baz = foo.bar(1337);

wRPC will take care of all of the setup to get your wasm modules for you so
that they will appear as regular JS Modules.

Stand Alone Application
-----------------------
*So what if I don't want to mess with JS?*

Examples
--------
See the examples folder.

Conclusion
----------
Yes.
