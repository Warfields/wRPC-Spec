.. _js_bindings:

JS Bindings
===========
This is a quick quick section on how to interact with wRPC. On the JavaScript
level. To begin, wRPC needs to initialize available modules to add new modules
to the RCP network.

.. code-block:: JavaScript

    import wRPC;

    // Init a wasm/wat module and have wRPC infer interaction
    foo = wRPC.initModule("foo.wasm");

    // Init with compiler template
    foo = wRPC.initModule("foo.wasm", "emscripten");

    // Init with custom protocol buffer
    foo = wRPC.initModule("foo.wasm", "foo.proto");

Next, modules can be globally imported.

.. code-block:: JavaScript

    baz = foo.call("bar","1337"); // equivalent to foo.bar(1337)

:todo: look at webIDL to make foo.bar(1337)

wRPC will take care of all of the setup to get your wasm modules for you so
that they will appear as regular JS Modules.

Stand Alone Application
-----------------------
*So what if I don't want to mess with JS?*

Don't worry you can choose to run an entirely wasm environment.
