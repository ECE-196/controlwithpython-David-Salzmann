### How does the DevBoard handle received serial messages? How does this differ from the naïve approach?
* The DevBoard handles received messages using interrupts. This differs from the naïve approach of just checking for changes of values in the running loop of our board because we can use interrupts to quickly execute specific parts of our code that are associated with those interrupts.
### What does `detached_callback` do? What would happen if it wasn't used?
* detatched_callback makes a callback run in its own detatched thread. If it wasn't used, then our GUI would freeze or slow down whenever a callback takes too long to execute.
### What does `LockedSerial` do? Why is it _necessary_?
* LockedSerial locks the serial bus of our system and allows only on process to access it at a time. It's necessary because we're using threading to run our callbacks, and while this is fast, it allows for collisions in our system if two callbacks try to access something, like the serial bus, at the same time.
