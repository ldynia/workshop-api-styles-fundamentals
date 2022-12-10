# Question and Answers

### [What is the difference between serialization and marshalling?](https://stackoverflow.com/questions/770474/what-is-the-difference-between-serialization-and-marshaling)

Serialization is the process of converting and objects state into a byte stream in such a way that the byte stream can be converted back into a copy of the object. Marshaling is the process of transforming the memory representation of an object into a data format suitable for storage or transmission.

When you serialize an object, only the member data within that object is written to the byte stream; not the code that actually implements the object. Marshaling is used when we talk about passing objects to Remote Method Invocation (RMI). In marshalling, state of an object is serialized (member data is serialized) + codebase is attached.
