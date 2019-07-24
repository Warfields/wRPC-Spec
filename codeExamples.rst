Precompilation Examples
=======================

JavaScript
----------
Calls the toy factory module to get the toys delivered

.. code-block:: JavaScript

    import wRPC;
    wRPC.init();
    factory = wRPC.load("rusty_toy_factory");
    factory.call("main");

C/C++
-----
Describes a Santa function.

.. code-block:: C++

    #include<wRPC>
    #include<vector>
    using namespace std;
    wRPC.exportAll();
    
    bool deliver(vector<string> gifts, int globalRegion){
        // Does delivering
        return true;
    }

Rust
----
Get the Santa module to deliver gifts generated in rust.

.. code-block:: rust

    use wRPC;

    fn main(){
        let santa: wRPC::Module;
        match wRPC.get("santa") {
            Ok(jolly) => santa = jolly;
            Err(_) => panic;
        }

        let result = 
            santa.call("deliver", [["gift","coal", "Commadore64"], 136);
        // All of the gifts got delivered to region 139

    }

Go Lang
-------
Not Done yet!

.. code-block:: go

    package main
    import "fmt"
    func main() {
        fmt.Println("hello world")
    }
