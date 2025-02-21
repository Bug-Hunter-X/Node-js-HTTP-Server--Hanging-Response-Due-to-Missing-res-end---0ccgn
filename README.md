# Node.js HTTP Server Hanging Response

This repository demonstrates a common error in Node.js HTTP servers: forgetting to call `res.end()` in the response handler.  This can cause client requests to hang indefinitely.

## The Bug

The `bug.js` file contains a simple HTTP server that intentionally omits the `res.end()` call.  This results in a hanging response, as the client waits for the server to signal the end of the response, which never happens.

## The Solution

The `bugSolution.js` file shows the corrected version of the server, which includes the crucial `res.end()` call. This ensures that the client receives a complete response and the connection is closed properly.

## How to Reproduce

1. Clone this repository.
2. Navigate to the directory.
3. Run `node bug.js` and attempt to make a request (e.g., using `curl` or a browser).
4. Observe that the request hangs.
5. Run `node bugSolution.js` and make the same request. Observe that the request completes successfully.