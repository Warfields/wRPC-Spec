.. _js_bindings:

JS Bindings
===========
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

Don't worry you can choose to run an entirely wasm environment.
