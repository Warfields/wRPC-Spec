Wasm RPC Protocol Specification
===============================
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

Proto Description
-----------------
The information that the initialization proto will provide are:

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

Response proto:

- Success/Fail
    + if fail why
- Data

Examples
--------
See the examples folder.

Conclusion
----------
yes
