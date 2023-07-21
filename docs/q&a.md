# Question and Answers

### [What is the difference between serialization and marshalling?](https://stackoverflow.com/questions/770474/what-is-the-difference-between-serialization-and-marshaling)

Serialization is the process of converting object state into a byte stream in such a way that the byte stream can be converted back into a copy of the object. Marshaling is the process of transforming the memory representation of an object into a data format suitable for storage or transmission.

When you serialize an object, only the member data within that object is written to the byte stream; not the code that actually implements the object. Marshaling is used when we talk about passing objects to Remote Method Invocation (RMI). In marshalling, state of an object is serialized: member data is serialized + codebase is attached.

### Is HTTP3 enforced by browser?

HTTP/3 is not enforced by browsers, but it is up to the servers to support it and offer it as an option for browsers to use. When a browser requests a website, it sends an initial request using HTTP/1.1 or HTTP/2, and the server responds with the version it supports. If the server supports HTTP/3, and the browser also supports it, the connection will use HTTP/3. If the server doesn't support HTTP/3, the connection will use the highest version that both the server and the browser support. 
