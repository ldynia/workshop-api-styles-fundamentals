# workshop-api-styles-fundamentals

1. OSI

- https://www.infoq.com/presentations/history-api/
- https://www.youtube.com/watch?v=aAb7hSCtvGw
- https://www.cloudflare.com/learning/ddos/glossary/open-systems-interconnection-model-osi/
- https://www.geeksforgeeks.org/layers-of-osi-model/
- https://infosys.beckhoff.com/english.php?content=../content/1033/tf6310_tc3_tcpip/84246923.html&id=
- https://www.imperva.com/learn/application-security/osi-model/
- https://cloud.google.com/blog/topics/developers-practitioners/differences-between-synchronous-web-apis-and-asynchronous-stateful-apis
- https://en.wikipedia.org/wiki/Duplex_(telecommunications)#FULL-DUPLEX
- https://cloud.google.com/blog/topics/developers-practitioners/differences-between-synchronous-web-apis-and-asynchronous-stateful-apis
- https://www.soapui.org/learn/api/soap-vs-rest-api/
- https://en.wikipedia.org/wiki/OpenAPI_Specification
- https://developers.google.com/protocol-buffers
- https://en.wikipedia.org/wiki/Apache_Thrift
- https://en.wikipedia.org/wiki/Apache_Avro
- https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol
- https://www.digitalocean.com/community/tutorials/http-1-1-vs-http-2-what-s-the-difference
- https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/Evolution_of_HTTP
- https://css-tricks.com/http2-real-world-performance-test-analysis/
- https://medium.com/walmartglobaltech/introduction-to-http-2-d3e3b4f4d662
- https://stackoverflow.com/questions/58498116/why-is-it-said-that-http2-is-a-binary-protocol
- https://developer.mozilla.org/en-US/docs/Web/HTTP
- https://freecontent.manning.com/animation-http-1-1-vs-http-2-vs-http-2-with-push/
- https://http3-explained.haxx.se/en/h3/h3-h2
- https://avinetworks.com/glossary/ssl-termination/
- https://www.ibm.com/docs/en/aix/7.2?topic=protocols-transmission-control-protocol
- https://ntrs.nasa.gov/api/citations/20080030196/downloads/20080030196.pdf
- https://www.json.org/json-en.html
- https://www.redhat.com/en/topics/api/what-is-a-rest-api
- https://en.wikipedia.org/wiki/HATEOAS
- https://medium.com/the-sixt-india-blog/rest-stop-calling-your-http-apis-as-restful-apis-e8336e3e799b
- https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.91.9164&rep=rep1&type=pdf
- https://gist.github.com/chrisnicola/1502400
- https://www.restapitutorial.com/lessons/whatisrest.html
- https://restfulapi.net/
- https://stackoverflow.com/questions/34130036/how-to-understand-restful-api-is-stateless
- https://www.redhat.com/en/topics/cloud-native-apps/stateful-vs-stateless
- https://www.redhat.com/en/topics/api
- https://www.redhat.com/en/topics/api/what-are-application-programming-interfaces
- https://restfulapi.net/what-is-an-api/
- https://nordicapis.com/understanding-idempotency-and-safety-in-api-design/
- https://krify.co/advantages-and-disadvantages-of-rest-api/
- https://www.geekboots.com/story/advantages-and-disadvantages-of-restapi-over-soap
- https://en.wikipedia.org/wiki/GraphQL
- https://phil.tech/2017/graphql-vs-rest-overview/
- https://honest.engineering/posts/why-use-graphql-good-and-bad-reasons
- https://www.howtographql.com/basics/0-introduction/
- https://www.howtographql.com/basics/2-core-concepts/
- https://www.prisma.io/blog/graphql-server-basics-the-schema-ac5e2950214e
- https://www.javatpoint.com/graphql-advantages-and-disadvantages
- https://unetworkingab.medium.com/millions-of-active-websockets-with-node-js-7dc575746a01#:~:text=The%20theoretical%20limit%20is%2065k,and%20then%20node%20examples%2FWebSocket.
- https://en.wikipedia.org/wiki/WebSocket
- https://en.wikipedia.org/wiki/Network_socket#Types
- https://hackernoon.com/pros-and-cons-of-websocket-and-eventsource
- https://www.rfwireless-world.com/Terminology/Advantages-and-Disadvantages-of-Websockets.html

# The problems with remote procedure calls (RPCs)

All of these are based on the idea of a remote procedure call (RPC), which has been around since the 1970s [42]. The RPC model tries to make a request to a remote network service look the same as calling a function or method in your programming language, within the same process (this abstraction is called location transparency). Although RPC seems convenient at first, the approach is fundamentally flawed [43, 44]. A network request is very different from a local function call:

- A local function call is predictable and either succeeds or fails, depending only on parameters that are under your control. A network request is unpredictable: the request or response may be lost due to a network problem, or the remote machine may be slow or unavailable, and such problems are entirely outside of your control. Network problems are common, so you have to anticipate them, for example by retrying a failed request.

- A local function call either returns a result, or throws an exception, or never returns (because it goes into an infinite loop or the process crashes). A network request has another possible outcome: it may return without a result, due to a timeout. In that case, you simply don’t know what happened: if you don’t get a response from the remote service, you have no way of knowing whether the request got through or not. (We discuss this issue in more detail in Chapter 8.)

- If you retry a failed network request, it could happen that the previous request actually got through, and only the response was lost. In that case, retrying will cause the action to be performed multiple times, unless you build a mechanism for deduplication (idempotence) into the protocol. Local function calls don’t have this problem. (We discuss idempotence in more detail in Chapter 11.)

- Every time you call a local function, it normally takes about the same time to execute. A network request is much slower than a function call, and its latency is also wildly variable: at good times it may complete in less than a millisecond, but when the network is congested or the remote service is overloaded it may take many seconds to do exactly the same thing.

- When you call a local function, you can efficiently pass it references (pointers) to objects in local memory. When you make a network request, all those parameters need to be encoded into a sequence of bytes that can be sent over the network. That’s okay if the parameters are primitives like numbers or strings, but quickly becomes problematic with larger objects.

- The client and the service may be implemented in different programming languages, so the RPC framework must translate datatypes from one language into another. This can end up ugly, since not all languages have the same types—recall JavaScript’s problems with numbers greater than 253, for example (see “JSON, XML, and Binary Variants”). This problem doesn’t exist in a single process written in a single language.

Custom RPC protocols with a binary encoding format can achieve better performance than something generic like JSON over REST. However, **a RESTful API has other significant advantages:** it is good for experimentation and debugging (you can simply make requests to it using a web browser or the command-line tool curl, without any code generation or software installation), it is supported by all mainstream programming languages and platforms, and there is a vast ecosystem of tools available (servers, caches, load balancers, proxies, firewalls, monitoring, debugging tools, testing tools, etc.).

For these reasons, REST seems to be the predominant style for public APIs. The main focus of RPC frameworks is on requests between services owned by the same organization, typically within the same datacenter.
