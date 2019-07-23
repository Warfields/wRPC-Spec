Precompilation Examples
=======================

JavaScript
----------
.. code-block:: JavaScript

    import bliss;
    export pain;

C/C++
-----

.. code-block:: C++

    #include<wRPC>
    using namespace std;
    int main() {
        int Blarg;
    }

Rust
----

.. code-block:: rust

    use wRPC;

    fn main(){
        let santa: wRPC::Module;
        match wRPC.get("santa") {
            Ok(jolly) => santa = jolly;
            Err(_) => panic;
        }

        let result = santa.call("deliver", [["gift","coal", std::f64::NAN], 136);
        // All of the gifts got delivered to region 139

    }

Go Lang
-------

.. code-block:: go

    package main
    import "fmt"
    func main() {
        fmt.Println("hello world")
    }
