# About the Node Lifecycle

Node is, essencialy, single-thread. There's only one big thread that interacts with the pool-thread of the OS.
What happens in the background, in simple way is:

- You write JS code;
- That JS code is read by the V8 (JS Engine), which compile your code;
- Then the JS Code is converted to C++ by the Node.js Bidings (node api), which is understood by the OS;
- When your application calls a function that will take some time to process (or will depend on external data), Node will delegate this function to the OS, which's multi-thread, with a callback function, which should be called once there's any return from the called function;
- Here's the main dilemma of node: the node itself is single-thread, but he can work with the threads of the OS, what makes it "emulate" a multi-thread process; but, in the end, what node really has is a hugh single-thread while-do loop dispatching functions and checking for the results - the pool thread;

Obs.: This text might have mistakes - it's just notes I took during the class, to help me understand the process.
